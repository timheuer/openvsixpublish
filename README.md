# openvsixpublish
This is meant to be used as a composite action step when publishing Visual Studio Extensions to the [Open VSIX Gallery](https://www.vsixgallery.com)

## Usage
When you have your GitHub Action workflow for your VSIX extension you can add this composite action:

```yml
on: [push]
      
jobs:
  build:
    name: Build 
    runs-on: windows-2022
      
    steps:
    - uses: actions/checkout@v2

    - name: Setup .NET build dependencies
      uses: timheuer/bootstrap-dotnet@v1

    - name: Publish to Open VSIX
      uses: timheuer/openvsixpublish@v1
      with:
        vsix-file: path/to/VSIXFile.vsix
```

This assumes there is a readme in your branch where you are publishing from otherwise you can specify a URL to a README.md by adding another `readme` argument in the use of the composite action.