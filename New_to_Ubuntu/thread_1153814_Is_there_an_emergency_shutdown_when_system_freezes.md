---
title: "Is there an emergency shutdown when system freezes?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by btedm on 2009-05-09
I am new to Ubuntu and just started with 8.10 and recently upgraded to 9.04.
Ubuntu is generally easy to use and I am pleased with it, but have problems that the screen sometimes freezes.  I can move the cursor but cannot get any response when I try to click on an icon.  I have had to resort to switching off the power on the computer.  I do not like to do this because I understand that this can cause loss of data and be bad for the hard drive.  I have tried ctrl-alt-del which sometimes works in Windows, and also ctrl-alt-F2 which I read might help.  In general neither of these have any effect.  Can anyone suggest a better approach than simply switching off power?

I found the following at the end of the /var/log/Xorg.0.log.old

(II) NVIDIA(0): Initialized GPU GART.
(this repeated 15 times in total)
(II) NVIDIA(0): Initialized GPU GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***

Can this be a clue to what is causing the freeze?

---

### Post by Rinzwind on 2009-05-09
Regarding the ctrl alt delete:

If ctrl alt f2 does not work in Linux you can use alt+sysrec+{key} to do some special things. Here's a short list:

Alt+SysRq+ 	Action 	Uses
R 	UnRaw 	Turns off keyboard raw mode. This allows input from the keyboard even if X-Window has crashed.
K 	SAK - Kill all on console 	Secure Access Key - Kills all programs on the current virtual console. This is useful if you want to make sure there are no programs waiting on the console to grab your password, or if a process won't let you switch consoles.
S 	Sync 	Attempts to sync all filesystems. This lessens the chance of data loss and fscking. Syncing is complete when "done" or "OK" is printed.
U 	Umount 	Attempts to remount all filesystems as read-only. Umounting is complete when "done" or "OK" is printed.
B 	Reboot 	Will immediately reboot without syncing or unmounting any disks. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.
C 	Crashdump 	Will perform a kexec reboot, in order to take a crashdump. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.
O 	Power Off 	Turns off the computer without syncing or unmounting disks. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.
P 	Show Pc 	Attempts to dump all registers and pointers to console.
T 	Show Tasks 	Attempts to dump a list of all tasks to console.
M 	Show Memory Info 	Displays memory info to console
V 	Voyager processor info 	Dumps Voyager SMP processor info to your console.
0-8 	Kern&#1077;l Error Verbosity 	Set the console log level for kernel messages. Setting to 0 only shows messages like PANIC and OOPS
F 	OOM Kill 	Calls oom_kill to kill a memory hog process
E 	Term 	Sends SIGTERM signal to all processes.
I 	Kill 	Kills (sends SIGKILL signal to) all processes.
L 	Kill + Kill Init 	Kills (sends SIGKILL signal to) all processes, including init. You will not be able to do anything else after using this!
N 	Nice 	Make real-time processes nice-able.
H 	Help 	Prints some help

From the list: 
Alt+SysRq+B will reboot. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.


Regarding the problem:
(II) NVIDIA(0): Initialized GPU GART.
should only appear ONCE.
It probably means you are missing some sort of package or that xorg is damaged.
Found it here with no sollution: 
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/229704](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/229704)
[https://bugs.launchpad.net/ubuntu/+bug/361361](https://bugs.launchpad.net/ubuntu/+bug/361361)

Found an answer on the fedora forums:
[http://forums.fedoraforum.org/archive/index.php/t-193698.html](http://forums.fedoraforum.org/archive/index.php/t-193698.html)
(2008-07-08, 11:03 AM CDT: reinstall xorg server).

Looks like this could do it:
sudo apt-get install ubuntu-desktop --reinstall

(dunno if it solves it :) but can't go wrong I believe :) )

---

### Post by Didius Falco on 2009-05-09
I'll leave the nVidia part for someone that uses nVidia - they'd know more than I would.

To safely reboot your system. Hold Alt + Prnt Scrn then 
press each of the letters one by one. If it doesn't
do anything, you have a total freeze and will need 
to hard kill it.


Alt+PrintScreen + R, E, I, S, U, B


Regards,

Didius

---

### Post by btedm on 2009-05-09
Thanks.  I tried the alt-systReq sequence with REISUB and it worked.  I had tried this earlier with 8.10 and had no success but today it works consistently.

Unfortunately the desktop reinstall did not make any difference.  But meanwhile, I have found one cause of the freeze.  I use Firefox and have it set to warn when I close multiple tabs.  If I only have a single tab open, I can close Firefox without a problem.  When I have two tabs open and exit by hitting the X in the upper right-hand corner, Firefox brings up a window asking if I want to (Quit,Cancel,Save Tabs).  When this window comes the Xorg.0.log file shows multiple ((II) NVIDIA(0): Initialized GPU GART) even before I make any selection from the list.  So I can avoid the problem by closing all tabs but one before I exit, or probably also by setting the option so Firefox does not ask when closing multiple tabs.
Thanks again.

---

### Post by 123456789123456789123456 on 2009-05-09
What NVIDIA chip set do you have on the computer?
are you using default drivers through Ubuntu, or are you using NVIDIA specialized drivers?

I have worked on one machine with NVIDIA chipset, with no problems at all.  However the video did not work under Ubuntu drivers, and the Pripiritary NVIDIA driver had to be used.

Can you provide Motherboard specs?  If you don't have that, provide computer specs.
could help with research.

---

### Post by btedm on 2009-05-09
> **123456789123456789123456 said:**
> What NVIDIA chip set do you have on the computer?
are you using default drivers through Ubuntu, or are you using NVIDIA specialized drivers?

I have worked on one machine with NVIDIA chipset, with no problems at all.  However the video did not work under Ubuntu drivers, and the Pripiritary NVIDIA driver had to be used.

Can you provide Motherboard specs?  If you don't have that, provide computer specs.
could help with research.

I am using Nvidia drivers obtained from Ubuntu.  It lists as version 180 in the "Hardware Drivers".  In /var/log/kern.log I see: 
NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44
so I assume it is version 180.44.  There is a version 180.51 on the Nvidia site, but I have not tried it.

I have the following computer specs:
Grafik: NVIDIA® GeForce® 8100, max. 512 MB shared Memory, VGA, DVI, DirectX® 10
Mainboard: Biostar GF8100 M2+ TE, Sockel AM2+, GeForce 8100 Chipset, 1× ATA - UDMA 133, 4× SATA II, 4× USB 2.0 + 2× Front-USB, 1× PCIe X16 (v2.0), 2× PCI, 2× PS/2, 6-Kanal HD Audio

In About Firefox:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.10) Gecko/2009042523 Ubuntu/9.04 (jaunty) Firefox/3.0.10

Hope this has everything you need, and if not I will try to find more.

---

### Post by hobo14 on 2009-05-09
ctrl - alt - backspace

Takes you back to the login screen.

But you'll have to enable this key combo first, because they've disabled it by default in 9.04! ;)

Search these forum for howto re-enable...

---

### Post by 123456789123456789123456 on 2009-05-10
Biostar may be the problem.  I have not personally used them, however a friend of mine has, and says that they generally have problems, with Windows, along with other OS's as well.  Could be problems related to the board, and not nessarily video.  You can try that driver from the nvidia site, though it probably want do much better than the one currently being used.  Have you checked the crash log, don't know if anything would be written in it since technically, it never crashed, but it could help track down the problem.  How often does the problem you are having accure?

---

### Post by btedm on 2009-05-10
Yesterday I found that closing multiple tabs in Firefox caused the system freeze.  Since then I have had no system freeze except for a few times when I deliberately closed multiple tabs to see if the behavior was repeatable. I wonder if this is possibly a bug in Firefox and looked in Google.  I found the following link that seems to be the same behavior: [https://bugs.launchpad.net/bugs/357718](https://bugs.launchpad.net/bugs/357718)
It appears that I am not the only one with this problem.
I do not see any file labelled crash log.  Where do you look for one?
PS I think I just found out.  I looked in /var/crash and there is no log file for any of these system freezes.

---

