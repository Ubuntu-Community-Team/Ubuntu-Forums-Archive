---
title: "Stuck on Plymouth Boot Splash"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by NUboon2Age on 2010-06-28
My Lucid notebook is getting **stuck on the Plymouth boot screen** and never gives me the Gnome Display Manager (gdm) log on screen.  It turns out the system is up because I can cntl+alt+F1-F5 to get to tty1-5 and log in and then restart the gdm with ```
sudo service gdm restart
``` and after things seem to be working okay, but **i need help fixing this so it just boots up correctly**.

----
[FONT=Arial Black][SIZE=4]Here's the two step fix:[/SIZE][/FONT]



In my case [SIZE="3"]**the real problem was that[/SIZE]** by mistake I had [SIZE="3"]**installed the kernel 2.6.32-23[/SIZE]** (i had been fine with the 2.6.32-22 kernel) from the Kubuntu experimental repository and at least in my system it seemed to clash with the Plymouth boot splash option.  The result was:

[LIST=1]
[*]First when booting it **came straight to the Grub2 recovery interface**.  *The fix: [SIZE="3"]**boot w/ a 10.04 liveCD**[/SIZE] and **run the [SIZE="3"]grub-reinstall[/SIZE] command** to get grub to reconfigure itself*. Ignore this step if it doesn't apply to your case. This was just the first layer of the problem...


[*]Secondly it would **stall on the Plymouth boot splash** (note: The 'splash' option in the below described kernel boot option determines whether Plymouth is used) and never reach the Gnome Display Manager (gdm) logon screen.  I could log in however by cntl+alt+F1-F6 and use a tty to work from the command line or  the gui by doing a 'sudo service gdm restart'. I *fix is to **[SIZE="3"]uninstall the 2.6.32-23 kernel[/SIZE]*** header and image packages via Synaptic (and then I *unchecked the Kubuntu experimental repository* that I'd mistakenly installed from.

I did a cntl+alt+F1 to get to tty1 and logged in and then restarted the gdm with ```
sudo service gdm restart
```.  Then I used Synaptics to uninstall all 2.6.32-23 kernel packages that I'd previously installed.

**The way I found out what the problem was and how to fix it was to:**
* hold down the shift key while booting, which brings up the Grub2 menu
* move the cursor up and down with my arrow keys to select a given kernel to boot from
* then type 'e' to edit whichever option I wanted to try, which brings up the Command options screen.
* I tried with and without the 'quiet splash' options on that page
* then type cntl+x to boot with whatever combinations of options I was trying.

**When I wanted to make the changes automatic** (so I wouldn't have to make them through the Grub2 menu the way I explained above) and [B]edit the   /etc/default/grub   file and put whichever kernel boot options I wanted into the line:

GRUB_CMDLINE_LINUX_DEFAULT="<options go here>"[/B]

So for example: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
{gives you no boot feedback to the screen (quiet mode) and the Plymouth boot splash} This is the installation default.  

-OR-

GRUB_CMDLINE_LINUX_DEFAULT="splash i915.modeset=0"
{gives you boot feedback to the screen (verbose mode), then Plymouth boot screen and the i915 modeset turned off}

-OR EVEN-

GRUB_CMDLINE_LINUX_DEFAULT=""
{verbose mode, no plymouth boot splash}

and for me i tried i915.modeset=0 and it worked okay for my Intel display adapter, but i found it wasn't necessary so i went with

GRUB_CMDLINE_LINUX_DEFAULT="splash"
{which gives me verbose mode plus the Plymouth boot screen}

:!::!::!::!:
[B]THEN IF YOU MAKE ANY CHANGES TO THAT FILE YOU MUST RUN:
```
sudo update-grub
``` for the change to take effect
[/B]
[/LIST]

**Note: I'm sure at some point** after the 2.6.32-23 kernel has been fully vetted and Plymouth and the other parts of Lucid have been appropriately upgraded to match it, **the 2.6.32-23 kernel will work just fine with Plymouth** and with my system.  I just installed it before my Lucid system was ready for it.


):P
Since I'm an Ubuntu newbie and don't really know my way around Ubuntu yet, **[SIZE="3"]there's no way I could have found these fixes without[/SIZE]** hours and hours of volunteer help from the [SIZE="3"]**[Ubuntu Beginners Team]("https://wiki.ubuntu.com/BeginnersTeam")[/SIZE]** and other folks on the #ubuntu, #kubuntu and (primarily) the #ubuntu-beginners IRC channels.  **People who helped include**: ddecator, tenach, hobgoblin, pedro3005, geirha, kermiac, seidos, stlsaint, zkriesse, James147, win_2_linux and others (sorry if i forgot to mention your name here...).  You guys rock!  :guitar:


**A few more details:**
[LIST]
[*]```

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```I didn't find anything in dmesg to give me a clue, except just noting which kernel was in use:
```
 
[    0.000000] Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)

```I wasn't really able to pick up any firm clues from the boot.log, and Xorg.log, although maybe I could have if I were more knowledgeable.

From the dpkg log here are what I'm guessing were the fateful entries:
```

2010-06-26 10:18:50 status installed linux-libc-dev 2.6.32-23.37 
{...}
2010-06-26 10:28:41 install linux-image-2.6.32-23-generic <none> 2.6.32-23.37
{...}
2010-06-26 10:30:21 upgrade linux-generic 2.6.32.22.23 2.6.32.23.24
{...}
2010-06-26 10:31:24 install linux-headers-2.6.32-23 <none> 2.6.32-23.37
{...}
```
[/LIST]

---

