# xcjit - JIT enabler for iOS, iPadOS, etc. via Xcode

A script that utilizes Xcode's command line tools to enable Just-In-Time (JIT) compilation for apps running on
iOS, iPadOS, and other related OS families.


## Prerequisites

- Mac with Xcode 16 and its Xcode Command Line Tools installed.
- Target device has Developer Mode enabled.
- Target device is [paired with Xcode on Mac](https://developer.apple.com/documentation/xcode/running-your-app-in-simulator-or-on-a-device/#Connect-real-devices-to-your-Mac).
- No warnings are shown at: Xcode > Window > Device and Simulators > Devices > \[your target device\].

## Usage

Ensure your paired device is connected to your Mac over USB, or on Wi-Fi on the same local network.

Then, in the project directory, run:

```bash
./xcjit '<device name>' '<app/process name>'
```

e.g.,

```bash
./xcjit 'iPad Pro' 'UTM'
```

You can softlink or copy the script to a directory in your PATH for quick access.


## Background

JIT on iOS and related OS families are "enabled" by simply attaching a debugger to the target app, and then immediately
detaching it. Apps being debugged go into a lower security state that allows apps like [UTM](https://getutm.app/) to
[use JIT](https://github.com/utmapp/qemu/blob/ios-support/docs/devel/ios.rst#jit-support), which isn't usually possible.

If you already have Xcode installed, this script provides a lightweight alternative that uses Xcode's built-in tools to
enable JIT, without any additional software or dependencies.
