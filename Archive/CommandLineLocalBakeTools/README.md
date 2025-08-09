# Project Acoustics Bake Tools

Package containing **Project Acoustics 2022.1** bake tools to execute acoustics bakes without the need for cloud compute.

## Usage

Check **Local Bake** section in [Project Acoustics Unreal Baking - Bake Submission](../Docs/UnrealEngine/unreal-baking-bake.md).

### SYNOPSIS

Linux:
```
LocalProcessor --<opt0> <val0> <val1>... --<opt1> <val0> <val1>... ...
LocalProcessor --configfile YourMap_AcousticsData_config.xml --workingdir working
LocalProcessor --configfile YourMap_AcousticsData_config.xml --workingdir working --Resume true
```

Docker:
```
docker run --rm -w /acoustics/ -v "%CD%":/acoustics/working/ mcr.microsoft.com/acoustics/baketools:2022.1.Linux ./tools/Triton.LocalProcessor --configfile Acoustics_PrisonUnderground_config.xml --workingdir working --resume true
del *.enc
```

### OPTIONS

| Option                      | Description                                    |
| --------------------------- | ---------------------------------------------- |
| --ConfigFile *NAME*         | (Required) Name of XML triton job config file. |
| --NodeSize                  | (Optional) Size of the PC/VM being used for the simulation. Default is 'Local'. |
| --NumThreads *INT*          | (Optional) Defaults to max logical processors. Number of threads to run the bake on. |
| --OutputName *NAME*         | (Optional) Name of the output ACE file. |
| --Resume *BOOL*             | (Optional) Defaults to false. If specified, and if there are existing .enc files in the working directory, will resume bake starting from the last .enc index. |
| --SharedInputDataDir *PATH* | (Optional) Path to the vox and config file, relative to the working dir.If not specified, Vox and config files will be assumed located in the WorkingDir. |
| --WorkingDir *DIRECTORY*    | (Optional) Process working directory. Task output will also be written to this path.Config and Vox files should be here unless specified by SharedInputDataDir. |
| --Help                      | Prints the help output. |
