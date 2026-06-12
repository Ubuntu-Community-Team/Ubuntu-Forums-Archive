---
title: "System information in Xubuntu?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by Catfish Dubois on 2011-05-31
How can I find system information on Xubuntu like how much RAM is installed or what kind of processor my laptop has.  On Windows XP, I would go to "control panel" and then "system" to find this information.  Is there something similar in Xubuntu 11.04?

I'm trying to figure out if the RAM that I just installed is working.

I'm new to Xubuntu, although I have used Ubuntu for several months.

---

### Post by garvinrick4 on 2011-05-31
```
sudo apt-get install sysinfo
```
Package: sysinfo                         
New: yes
State: not installed
Version: 0.7-4
Priority: optional
Section: universe/utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 397 k
Suggests: nvidia-settings
Description: display computer and system information
 sysinfo is a graphical tool that is able to display some hardware and software
 information about the computer it is run on. 
 
 It is able to recognize information about: 
 * System (Linux distribution release, versions of GNOME, kernel, gcc and Xorg
   and hostname); 
 * CPU (vendor identification, model name, frequency, level2 cache, bogomips,
   model numbers and flags); 
 * Memory (total system RAM, free memory, swap space total and free, cached,
   active, inactive memory); 
 * Storage (IDE interface, all IDE devices, SCSI devices); 
 * Hardware (motherboard, graphic card, sound card, network devices); 
 * NVIDIA graphic card: only with NVIDIA display driver installed.
Homepage: [https://sourceforge.net/projects/gsysinfo/](https://sourceforge.net/projects/gsysinfo/)

rick@rick-HP:~$

---

### Post by Catfish Dubois on 2011-05-31
Yes, that's exactly what I'm looking for.  Thanks.  When I installed it and tried to run it, I get the following:
exec: 9: mono: not found

what does that mean?  Am I missing a dependency?

Thanks,

---

### Post by garvinrick4 on 2011-05-31
Never had a problem running it.
Hit Windows key:
type in sysinfo
click on icon;
It should open no problem.

---

### Post by Catfish Dubois on 2011-05-31
ok, thanks.

---

### Post by Ron Miracle on 2011-08-07
sysinfo exec: 9: mono: not found Didnt work .I reinstalled rebooted and same nothing.
Here is what the bin sysinfo says.

#!/bin/sh

prefix="/usr"
exec_prefix="$(prefix)"
libdir="$(exec_prefix)/lib/sysinfo"

cd $(libdir)

exec mono "Sysinfo.exe" "$@"

---

### Post by amjjawad on 2011-08-07
Last time I checked Xubuntu, there was an application which is installed by default to check the System Info.

If you installed a new Hardware, the best approach to check is from BIOS as BIOS can be entered even before an OS can be loaded.

---

### Post by XubuRoxMySox on 2011-08-07
I'm using Xubuntu 10.04 (Lucid) and it has System Monitor installed (a Gnome app, but hardly a resource-hungry monster).

I do **[COLOR="Purple"]Menu --> System -->  System Monitor[/COLOR]**.

The result is in the attached screenshot.

-Robin

---

