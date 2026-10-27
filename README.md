
# SARTHAK OPTIMIZER v1.0

A Windows optimizer that actually tells you what it changes.

Every tweak is listed, reversible, and backed by a restore point.

## What it is

SARTHAK OPTIMIZER is a focused system tuner for Windows 10 and 11.

No registry "cleaning". No fake RAM boosters. No telemetry of its own. It changes a defined set of documented Windows settings, shows you exactly what each one does, and can undo every change it made.

## What it does

Startup and tasks
- Lists every startup entry with its publisher and file path
- Enables, disables or deletes startup entries
- Finds and removes orphaned scheduled tasks left by uninstalled software
- Flags entries that point to files which no longer exist

Bloatware
- Lists installed Appx packages with size and publisher
- Removes bundled apps by name or by category
- Can reinstall a removed package from the Microsoft Store

Telemetry and privacy
- Disables the diagnostic data pipeline, activity history and advertising ID
- Turns off the compatibility telemetry scheduled tasks
- Disables feedback prompts, tips and suggested content
- Per-item toggle, nothing applied in bulk without consent

Services
- Three profiles: Safe, Balanced, Aggressive
- Every service is listed with its display name, current start type and a one-line explanation
- Nothing is disabled that breaks Windows Update, Defender, networking or audio
- One click to restore all services to their original start type

Storage
- Clears temp, cache, prefetch, thumbnails, crash dumps and old update files
- Reports exactly how much each category frees before deleting anything
- Skips anything in use instead of forcing a delete

Memory and power
- Trims working sets of background processes
- Clears the standby list on demand
- Switches between Balanced, High Performance and Ultimate Performance power plans
- Enables or disables Game Mode and Hardware Accelerated GPU Scheduling

Network
- TCP autotuning, Nagle, and throttling index toggles
- Per-adapter view, so you can see what is being changed before applying
- Resets to Windows defaults in one click

## What it does not do

- It does not touch the registry looking for "errors". That class of tool damages systems.
- It does not delete files it cannot identify.
- It does not run anything in the background.
- It does not phone home.
- It installs no service and no driver. It is a normal user-mode application.

## Safety

Before applying anything, it creates a System Restore point with a timestamped name.

Every action is written to a log at `<install dir>\sxoptimizer.log`, so you can see exactly what was changed and when.

The Revert screen restores the original state for every category it touched. If a revert fails partway, the log tells you which item failed and what the previous value was.

## Requirements

- Windows 10 21H2 or newer, or Windows 11
- Administrator rights for service, power plan and telemetry changes
- No dependencies, no .NET runtime, no redistributables

## Install

1. Run `SarthakOptimizer_Setup.exe`
2. Follow the setup pages
3. Launch the app from the finish page

To remove it, use Add/Remove Programs or the bundled uninstaller.

## Usage

Open the app, pick a category from the left panel, review the list, tick what you want, apply.

Command line, for scripting:

    SarthakOptimizer.exe --list-startup
    SarthakOptimizer.exe --clean temp,prefetch,thumbnails
    SarthakOptimizer.exe --services balanced
    SarthakOptimizer.exe --telemetry off
    SarthakOptimizer.exe --power ultimate
    SarthakOptimizer.exe --revert all
    SarthakOptimizer.exe --dry-run

`--dry-run` prints every change it would make and touches nothing. Use it first if you are unsure.

## FAQ

Is it safe?
It only changes documented Windows settings, it creates a restore point first, and every change is reversible from inside the app. Nothing is hidden.

Will it speed up my PC?
Startup cleanup, telemetry tasks and service tuning make a measurable difference on low-end hardware. On a modern machine with an SSD, expect a cleaner system more than a faster one. Anyone promising more is selling you something.

Does it break Windows Update?
No. The Safe profile does not touch update, Defender, networking or audio services. Aggressive mode warns you before touching anything that could affect them.

Can I undo everything?
Yes. `--revert all` restores the original state for every category.

Does it work on Windows 11?
Yes, both 22H2 and 23H2 are tested. Windows 10 21H2 and newer are supported.

Why does it need admin rights?
Service start types, power plans and telemetry policies are machine-wide settings. Without elevation it can only show you state, not change it.

## Changelog

v1.0.0
- Startup manager with orphan detection
- Scheduled task cleanup
- Bloatware removal and reinstall
- Telemetry and privacy toggles
- Service profiles with full revert
- Storage cleanup with per-category size report
- Memory trim and standby list clear
- Power plan and GPU scheduling toggles
- Network tweaks with adapter view
- Restore point creation before every apply
- Full action log and one-click revert

## Tags

#windows #optimizer #tweaks #systemtools #cpp #win32 #performance #privacy #debloat

dev by sarthak </>
