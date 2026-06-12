---
title: "Installing bcmwl-kernel-source hangs on last line; Unable to lock directory"
date: 2018-10-08
forum: Networking &amp; Wireless
---

### Post by bennywas on 2018-10-08
Within the rabbit hole of trying to get my BCM4331 (rev 2) wireless working, I stumbled across a scary bug, [which is also documented here]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1173372") but the solutions documented in that old thread didn't work for me in Ubuntu 18.04 LTS.

**PROBLEM DESCRIPTION**
Installing bcmwl-kernel-source gets stuck on what I *assume* is the last line, "DKMS: install completed."

```
benny@benny-MacBookPro:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,550 kB of archives.
After this operation, 8,067 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 154115 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 4.15.0-36-generic
Building for architecture x86_64
Building initial module for 4.15.0-36-generic
This system does't support Secure Boot
Secure Boot not enabled on this system.
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-36-generic/updates/dkms/

depmod...

DKMS: install completed.


```
It hangs on that last line for forever. Ctrl-c doesn't do anything here.

Closing the terminal tab and starting afresh apparently didn't kill whatever processes that were hanging, either. I tried doing that but then terminal kept on returning the following when I tried to keep doing what I was doing:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

**SOLUTION**
Here's the _best_ way to kill the installation and un-hang this, using my own results as an example.
```
#LEAVE THE HANGING TERMINAL TAB OPEN. Don't close it in frustration. Let it hang.
#OPEN A NEW TERMINAL TAB (or window), from which we'll do the killing. Run these commands like I did.

benny@benny-MacBookPro:~$ ps aux | grep bcmwl #This lists all processes that are currently running which are related to "bcmwl".
root     26433  0.0  0.0  72716  4244 pts/2    S+   17:40   0:00 sudo apt-get install bcmwl-kernel-source
root     26434  1.1  1.0 140564 82916 pts/2    S+   17:40   0:00 apt-get install bcmwl-kernel-source
root     26461  0.0  0.0   4628  1712 pts/0    S+   17:40   0:00 /bin/sh /var/lib/dpkg/info/bcmwl-kernel-source.postinst configure
benny    27596  0.0  0.0  21536  1116 pts/3    R+   17:41   0:00 grep --color=auto bcmwl

#Those first three processes are the ones I needed to kill. I think the last process is just me running the grep command.
#No column titles are listed, but the process identification numbers (PID) are the second column.

benny@benny-MacBookPro:~$ sudo kill -9 26433 26434 26461
#Killing them all in one swoop. I tried doing variations of "kill", but it kept saying "bash: kill: (PID) - Operation not permitted" until I used "sudo" and "-9" as well.

benny@benny-MacBookPro:~$ ps aux | grep bcmwl #Just to make sure.
benny    27614  0.0  0.0  21536  1012 pts/3    S+   17:44   0:00 grep --color=auto bcmwl #Yep, everything bcmwl related is dead except for my grepping.

#GO BACK TO THE HANGING TAB, and it should say,
#(...)
DKMS: install completed.
Killed
benny@benny-MacBookPro:~$
#You can obviously now close out of either tab if you'd like.
```

And here's what _actually_ happened for me the first time, when I closed the hanging tab in frustration. I hope you haven't done this but it didn't turn out to be a big deal.
```
#I quit terminal and re-opened. Figuring there were still bits and pieces of the package lying around, I wanted to purge it.
benny@benny-MacBookPro:~$ sudo apt-get remove --purge bcmwl-kernel-source
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

#I had no idea what that meant, so I did like it asked and ran that command...
#But what it ended up doing was uninstalling the package and trying to reinstall it, then hanging at the same place.

benny@benny-MacBookPro:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.271+bdcom
Kernel:  4.15.0-36-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.271+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 4.15.0-36-generic
Building for architecture x86_64
Building initial module for 4.15.0-36-generic
This system does't support Secure Boot
Secure Boot not enabled on this system.
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-36-generic/updates/dkms/

depmod...

DKMS: install completed.

#Again, this is where it hung. BUT WAIT--
#This time, for whatever reason, I WAS ABLE TO CTRL-C and it actually worked and killed the process.

^Cdpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess was interrupted
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 bcmwl-kernel-source
benny@benny-MacBookPro:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 8,067 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 154200 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.130ubuntu3.5) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-36-generic
(Reading database ... 154114 files and directories currently installed.)
Purging configuration files for bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.130ubuntu3.5) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-36-generic
benny@benny-MacBookPro:~$

#After this I was able to purge bcmwl-kernel-source for real, with no issues.
```

**To this day,** I'm still unable to install bcmwl-kernel-source [COLOR=#008000]**[EDIT: see posts below for potential solution]**[/COLOR]. Now that I know how to fix this hanging problem for me, I've fearlessly re-tried installing it multiple times from terminal, but every time the same thing happens. I think I'll try to install broadcom-sta or similar instead? Because I've heard they're pretty much the same thing...although if someone would care to elaborate on the difference I'd appreciate it.

Peace, good luck, and feel free to post your own problems/solutions related to this below--although I DEFINITELY won't be able to help you lol. I'm a beginner with Ubuntu and terminal and everything.

~  ~  ~  ~  ~  ~  ~  ~  ~  ~

Here's my wireless information by the way:
```
benny@benny-MacBookPro:~$ lspci -vvnn | grep -A 9 Network
04:00.0 Network controller [0280]: Broadcom Limited BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00ef]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c1900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma, wl
```

---

### Post by wildmanne39 on 2018-10-08
If your wifi is not working I recommend you mark this thread unsolved then please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will most likely be able to help. 

Do you have trouble installing all applications or is this isolated to just the wifi driver? if it is with all applications I recommend starting a thread for installing the application issue.

---

### Post by bennywas on 2018-10-09
*THE LEGEND WILDMANNE39*
Thanks for replying. This was only a problem for this one package; it didn't happen for anything else. Also,[B]

UPDATE -- I successfully installed it without hanging![/B]
- I had previously purged the package using [FONT=courier new]sudo apt-get purge bcmwl-kernel-source[/FONT]
- Attempting to reinstall it, I kept trying [FONT=courier new]sudo apt-get install bcmwl-kernel-source [/FONT]but it would hang (thus my original post)
- Just now, I halfheartedly tried one last time but this time with [FONT=courier new]sudo apt-get install **--reinstall** bcmwl-kernel-source[/FONT] *and it worked!!* No hang!!

I guess the difference between [FONT=courier new]install[/FONT] and [FONT=courier new]install --reinstall[/FONT] in this situation is really significant? Maybe it has to do with the package being proprietary? (Idk, that's what the other thread mentioned)

[B]UPDATE2 -- The above is not a consistent solution to reinstalling bcmwl-kernel-source
[/B]- I tried recreating all this and *couldn't* install bcmwl-kernel-source successfully using [FONT=courier new]install --reinstall[/FONT]. Then, the next day after a night's rest, I tried it again and for some reason it worked. So honestly I'm not sure if it's [FONT=courier new]install --reinstall[FONT=arial] being a solution or just weird chance.[/FONT][/FONT]

~  ~  ~  ~  ~
> If your wifi is not working I recommend you mark this thread  unsolved then please click on the wireless script in my signature,  follow the directions for running it and posting the results back here  using the pastebin link created and someone will most likely be able to  help.
Thanks, but I tried bouncing around my wireless woes last week (including that script) and I got no help. So I started researching on my own and at this point I feel like I'm so close to figuring it out that I'll only post for help again if I get completely stuck. In the meantime I just wanted to share how I fixed this for myself, in case someone else has the same problem and doesn't know what to do / thinks they're alone.

---

### Post by bennywas on 2018-10-14
**I figured this out** to the point where I'm able to reproduce it for myself.
[COLOR=#a9a9a9]This seems super-specific but I'm sharing it anyway in case someone else comes across it.[/COLOR]

Nothing makes bcmwl-kernel-source install properly unless the "b43" module is not in use (NO idea why). If [FONT=courier new]lsmod|grep b43[/FONT] happens to show that b43 is in use, I can still kill the hanging process successfully, but any combination of [FONT=courier new]install[/FONT] / [FONT=courier new]install --reinstall[/FONT] / [FONT=courier new]autoremove[/FONT] / [FONT=courier new]clean[/FONT] / [FONT=courier new]purge[/FONT] / dist-upgrading / rebooting will still just lead to another perpetual hang. However, if b43 is *not* in use, then these commands are successful and the package ends up getting installed.

So, to reproduce this successfully, here's what I've been doing...
- If it's hanging, I kill the process(es) from another tab.
- I remove b43. Since removing b43 using [FONT=courier new]sudo modprobe -r b43[/FONT] gives me a segmentation error, I decided to blacklist b43 by opening [FONT=courier new]sudo gedit /etc/modprobe.d/blacklist.conf[/FONT] and adding the line [FONT=courier new]blacklist b43[/FONT] to the end, then rebooting so the module doesn't get loaded to begin with, then checking [FONT=courier new]lsmod|grep b43[/FONT] just to make sure it's not loaded.
[FONT=courier new]$ sudo apt-get autoremove[/FONT] #This may or may not autoremove "dkms"...One time I needed to do it; another time it showed nothing.
[FONT=courier new]$ sudo apt-get purge bcmwl-kernel-source[/FONT] #Idk why, but when autoremove shows dkms, I have to run this too afterwards and it deletes a bunch of stuff. If autoremove doesn't show anything, then purging doesn't show anything either.
[FONT=courier new]$ sudo apt-get install --reinstall bcmwl-kernel-source[/FONT] #After all that, this reinstalls it successfully.

---

### Post by wildmanne39 on 2018-10-14
Hello, I will try to clear up a couple of things for you, when you install:
```
bcmwl-kernel-source 
```
unless there is something wrong with your install the b43 driver is blacklisted automatically.
If you use the purge --remove command to get rid of the:
```
bcmwl-kernel-source 
```
before you install the b43 driver then the b43 driver should be unblacklisted at that time.
> sudo apt install --reinstall bcmwl-kernel-source
is exactly what finally made installing the wl driver successful.

Finally you can not have the wl and the b43 driver installed at the same time because they will conflict with each other.

---

