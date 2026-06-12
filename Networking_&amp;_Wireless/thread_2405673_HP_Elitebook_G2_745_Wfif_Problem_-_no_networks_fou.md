---
title: "HP Elitebook G2 745 Wfif Problem - no networks found"
date: 2018-11-09
forum: Networking &amp; Wireless
---

### Post by nowocmic on 2018-11-09
Hello,

I have problem with WiFi on HP Elitebook G2 745. I can't find any networks. I know there are some solutions to this particular card on this form but all those solutions didn't work in my case.
I am using Broadcom Wireless Adapter BCM4352 802.11ac. I did install proper driver via:

sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl

I also checked
rfkill list all
and everywhere is "no" so nothing is blocking the wifi adapter.

When I search in console: sudo iwlist scan it returns "no results".

I did everything what I found on this forum and still the same problem - no networks.
Do you have any idea how to fix it or maybe Linux is not right environment for HP G2 745 and I need to switch on Windows10 ?

---

### Post by praseodym on 2018-11-09
Did you deactivate SecureBoot? The driver is not signed...

---

### Post by nowocmic on 2018-11-10
Hello,

In BIOS settings the SecureBoot Configuration is not editable but checkboxes are unmarked so I assume it doesn't work. Any other advice?

---

### Post by chili555 on 2018-11-12
What does this tell us?```
lspci -nnk | grep 0280 -A3
```Old Chili is getting a bad feeling right here....

---

### Post by nowocmic on 2018-11-12
Here it is:

```
02:00.0 Network controller [0280]: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Hewlett-Packard Company BCM4352 802.11ac Wireless Network Adapter [103c:2154]
    Kernel driver in use: wl
    Kernel modules: bcma, wl
```

I did:

```
sudo apt install shim-signed
sudo update-secureboot-policy --new-key
```

Now I am trying:

```
[FONT=inherit]sudo apt-get install ndisgtk[/FONT]
```

But I can't find .inf file with driver for Windows 10 (only exe).

---

### Post by chili555 on 2018-11-12
Here is a long thread about your device: [https://ubuntuforums.org/showthread.php?t=2405333&highlight=43b1](https://ubuntuforums.org/showthread.php?t=2405333&highlight=43b1) It doesn't end with a good result.

You might try all the steps we tried there and report back.

---

### Post by nowocmic on 2018-11-12
I did it and same effect - no networks found. Does it mean I can't run linux on HP Elitebook G2 745? I am really disapointed how Linux can't handle wifi ...

---

### Post by jeremy31 on 2018-11-12
You could replace the wifi card with a supported wifi.  Linux has no control of when Broadcom adds support to the proprietary bcmwl to support their wifi cards

---

### Post by chili555 on 2018-11-12
> I am really disapointed how Linux can't handle wifi ...As Jeremy suggests, it's not Linux, it's Broadcom.

Many devices, including my Intel, work perfectly in Linux.

---

### Post by nowocmic on 2018-11-14
Guys,

The solution is:

[COLOR=#000000][FONT=HPSimplifiedLight]1. Edit as root this file: "/etc/default/grub"[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]  - Find and modify GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="intremap=off"[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]  - Save and exit[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]2. $sudo grub-mkconfig -o /boot/grub/grub.cfg[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]3. Reboot

After it wifi works fine.[/FONT][/COLOR]

---

### Post by pwwiur on 2019-06-15
> **nowocmic said:**
> Guys,

The solution is:

[COLOR=#000000][FONT=HPSimplifiedLight]1. Edit as root this file: "/etc/default/grub"[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]  - Find and modify GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="intremap=off"[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]  - Save and exit[/FONT][/COLOR]

[COLOR=#000000][FONT=HPSimplifiedLight]2. $sudo grub-mkconfig -o /boot/grub/grub.cfg[/FONT][/COLOR]

[COLOR=#000000][FONT=HPSimplifiedLight]3. Reboot

After it wifi works fine.[/FONT][/COLOR]


This was the best answer, worked for me, so many thanks, you saved me.

---

