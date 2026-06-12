---
title: "Absolute noob question, not getting any audio"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by alxpenguin on 2009-07-11
Hi guys, Im trying out ubuntu on the cd right now without installing just to get a feel on the OS and see if I make the change from windows to Ubuntu. As of right now Im not getting any sounds from radio or anything. Is this normal and will it go away if I choose to install

---

### Post by overdrank on 2009-07-11
> **alxpenguin said:**
> Hi guys, Im trying out ubuntu on the cd right now without installing just to get a feel on the OS and see if I make the change from windows to Ubuntu. As of right now Im not getting any sounds from radio or anything. Is this normal and will it go away if I choose to install

Hi and welcome, do you mean Internet radio has no sound?
 You may need some flash installed or other restricted formats. A good place to start would be to identify your hardware and then search the forums for issues. You may use the command lspci in the terminal which is located under applications, accessories. This will identify your hardware and then you can search.
Moved to   Absolute Beginner Talk :)

---

### Post by earthpigg on 2009-07-11
hi alx,

you can test stuff from the live cd, *still without making any permanent changes to your computer*, before you install in order to make sure everything will work.

for example, if you want to get internet radio to work:

applications -> add/remove programs -> search for 'ubuntu restricted extras' -> click the check box next to it -> apply changes.

restart firefox -> go to your internet radio station website -> see if it works now.



if you do install, you will need to do this again.... anything you do while running off the live cd will vanish when you restart.

---

### Post by alxpenguin on 2009-07-12
Im actually not getting any sound at all, not when I open folder, not when I try to open movies and struff. Even the example files that come with the cd dont sound. Where can I look into this_

---

### Post by halitech on 2009-07-12
open a terminal and post the output of```
lspci
``````
lshw -C sound
```and```
aplay -l
```this will help us to help you

---

### Post by alxpenguin on 2009-07-12
Thanks ill give it a shot

---

### Post by alxpenguin on 2009-07-12
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
06:00.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
ubuntu@ubuntu:~$ lshw -c sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
Thats what I get. Im running the system from the cd right now, is it normal not to have sound

---

### Post by halitech on 2009-07-12
the hardware looks fine and no, its not normal to not have any sound but some cards require a little more work then others.

try running alsamixer from the terminal and see if anything is muted or has the volume turned down low.

edit to add: Also if you go to >System >Preferences >Sound under the Devices tag you should have everything set to Auto

---

### Post by alxpenguin on 2009-07-12
Geez, well the master is set to 91% and it doesnt look like anything is muted....what else can I do?

---

### Post by earthpigg on 2009-07-12
click the little speaker thingie -> volume control -> preferences -> check everything, so you can see it all -> turn everything up and make sure it isn't muted


beyond that, to be honest, my sound card has always worked... others will have to help you if that doesn't do it.

---

