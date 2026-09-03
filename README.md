# syn-settings

System settings: displays and resolution, keyboard and language, date and
time, network, Bluetooth, power and sleep, kernels, the AI backend, the
screen reader, default applications, and where configuration actually lives.

A window with panes, and a command line that answers each pane as records.

## The window

```bash
syn-settings gui             # open it
syn-settings gui network     # open it on one pane
```

Panes: `display`, `region`, `time`, `network`, `bluetooth`, `power`, `apps`,
`kernel`, `ai`, `speech`, `system`.

## Reading the same answers from a script

```bash
syn-settings --rec display   # connectors: the kernel's state beside what
                             # the compositor is actually driving
syn-settings --rec time      # the clock, and how the desktop writes it
syn-settings --rec apps      # the default app per role, and WHICH file
                             # decided it
syn-settings --rec kernel    # every kernel on offer, installed, running
syn-settings --rec fprint    # the reader, and which fingers are enrolled
```

The `apps` pane reports which file made each decision, because a deliberate
choice and a fallback look identical everywhere else — that is the difference
between "nothing is set" and "something set it and you did not".

## What it drives

`systemd` for `localectl`, `timedatectl` and `systemctl`; `networkmanager`
for the network pane; `bluez-utils` for Bluetooth; `wlr-randr` and `synctl`
for displays; `synpkg` and `pacman` for kernels; `fprintd` for fingerprints.
Each pane says what is missing rather than showing an empty box, and changes
that need authorisation go through polkit instead of asking for a root shell.

## Install

```bash
git clone https://github.com/velle999/syn-settings
cd syn-settings && makepkg -si
```

makepkg fetches the source for this PKGBUILD's exact version from this
repository's releases, so a clone can only ever build the source it was
written against. `.SRCINFO` lists what it needs.

## Where this comes from

Developed in [the SynapseOS monorepo](https://github.com/velle999/SYNAPSE),
in `syn-settings/`. **This repository is generated from it** — the PKGBUILD, a
generated `.SRCINFO` and this README — so issues and patches belong there.

syn-settings 0.1.0-47 · GPL-2.0-or-later
