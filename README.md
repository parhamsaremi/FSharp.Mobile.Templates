# net6.0-mobile-fsharp

In this repository, you can find all the templates for creating apps on iOS and Android using .NET 6.0 and F# 6.0

### Prerequisites
In order to build and run the Android and iOS projects, you need to install the corresponding workloads
```
dotnet workload install android
dotnet workload install ios
dotnet workload install maccatalyst
dotnet workload install maui
```

For `net6.0-xamarinforms-fsharp`, you'll also need to go into the file `nuget.config` and replace `USERNAME` with your GitHub username and `TOKEN` with your personal access token.
See https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-nuget-registry#authenticating-with-a-personal-access-token

### Available templates
- Blank Android: ✔️
- Blank iOS: ✔️
- Blank Mac Catalyst: ✔️
- Xamarin.Forms
  - Android: ✔️
  - iOS: ✔️
- Maui
  - Android: ✔️
  - iOS: ✔️
  - Mac Catalyst: ✔️

### Known issues

- First build fails on Android (native, XF and MAUI)
  - You need to compile 2 times to get it working. It's a current limitation of FSharp.Android.Resource used to expose the resources.
  - You might also need to unload/reopen either the Android project or the solution for Intellisense to find the resources
- Blank Mac Catalyst
  - Project has to be run with `dotnet build -t:Run`. IDEs like Rider will otherwise try to debug it as an iOS app
- Maui
  - For the moment, it requires an ugly custom import in the fsproj for all `Platforms/**/*` files. I believe we can fix this directly in Maui Sdk and keep it compatible with C# (see [#8](https://github.com/fabulousfx/net6.0-mobile-fsharp/issues/8))
  - Only tested on macOS M1 with `dotnet build -t:Run -f net6.0-ios` / `net6.0-android` / `net6.0-maccatalyst`

### Acknowledgements

Thanks @Dolfik1 for the blank Android template.  
Thanks @edgarfgp for the blank iOS template.
