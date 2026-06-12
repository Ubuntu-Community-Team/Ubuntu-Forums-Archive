---
title: "Wireless Propblem: Dapper Drake on Sony Vaio"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by adverseyaw on 2006-08-13
Hello all.  I have been using linux for about 5 months now. I had Breezy on my laptop, a Sony Vaio VGN-FS550 and Debian at home.  I just upgraded to Dapper Drake and things that did work, no longer do.:-({|= 
When I installed Breezy I had to set the display to the proper resolution with 915resolution.  And the sound didn't work, but I fixed that (I don't remember how).  But the wireless network worked fine from the beginning.  I assume that it recognized the card (inbuilt Intel PRO/Wireless 2200BG) and set up everything for me. The wired connection was eth1 and wireless was eth0.
 After the upgrade to Dapper Drake I did the 915resolution thing again and am trying to figure out sound, but my real problem is that I have no wireless connection anymore.  eth0 is the wired connection and the modem connection is in there, but no wireless connection.  I don't have a '+ADD' button to add the wireless as I saw in the ubuntu help.  So I am at a loss.
When I do **lspci** command I find that it recognized the 'Intel PRO/Wireless 2200BG' but I don't know how to set up devices for it, and get it into the Network Configuration dialog.  I tried ndiswrapper with the recommended driver (8.1.1) from their list on the site but I get the dreaded *ndiswrapper line 135* error.  All the files in the package are there in the directory it just doesn't want to Copy to the dev folder.
Any help anyone can give me is greatly appreciated.
Thanks in advance
AdverseYaw

---

### Post by adverseyaw on 2006-08-14
After quite a bit of research it seems that I need to use the [FONT="Courier New"]ipw2200[/FONT] driver.  This is installed by Dapper Drake 6.06.  It doesn't seem to be installed on my machine though.  
How do I go about finding out if it is installed?
If it isn't installed, then it seems I will have to build it. 
I have already downloaded the three files that I require according to the [HOWTO]("http://ubuntuforums.org/showthread.php?t=26623"):
[LIST]
[*]ipw2200-fw-2.4.tgz
[*]ieee80211-1.1.0.tgz
[*]ipw2200-1.0.6.tgz
[/LIST]
But I am having trouble finding the kernel-headers.  The repository doesn't list the headers for my kernel version (2.6.12-10-686)[from  apt-get install kernel-headers-$(uname -r)].  What kernel headers do I need?  Can I use other kernel headers?  When building the kernel is the -686 just a compile flag?  Or are there other files that I need compared to -386.
There is so much that I need to learn...:oops:
Thanks
AdverseYaw

---

### Post by mjziegle on 2006-08-14
What's the output of iwconfig?

This sounds like a configuration problem, not a driver problem.

---

### Post by adverseyaw on 2006-08-14
It outputs the :
no wireless extension.
For each lo and eth0 and the modem connection.
Adveseyaw

---

### Post by mpvano on 2006-08-14
To find out if the builtin driver is present (it almost certainly is),  give the command

locate ipw2200

The driver modules themselves are the ones ending in .ko. There will be one for each kernel you have installed - in that kernel's modules directory.

To find out if it's loaded give the following command

lsmod | grep  ipw

and see if the name of the driver appears on any of the lines of output.

If not, you can run a simple test to see if it can be loaded manually by typing:

sudo modprobe -a ipw2200

and seeing what the result of the command is. If no errors are reported, try the lsmod command again and see if ipw2200 shows up in the result. If it does, then you can try reporting the following:

sudo iwconfig

and also the results of 

sudo ifconfig

If the driver is either loaded or CAN be loaded, you can move on in troubleshooting, but one thing at a time....

Mario

---

### Post by adverseyaw on 2006-08-15
I did everything up to [FONT="Courier New"]sudo modprobe -a ipw2200[/FONT].  The locate command found the driver in its proper place.  lsmod | grep ipw showed that it wasn't started(?).  And modprobe returned the error that I don't have ieee80211 installed, or it is not in its proper place.  All I have found is the source for ieee80211.  Is there a precompiled executable somewhere that I can download? or do I have to compile it from source?
AdverseYaw

---

### Post by mpvano on 2006-08-15
It's unlikely that you'll do anything but get in a tailspin if you build things from source. It's rarely needed and often breaks other drivers if you follow generic build instructions or the ones for other releases.

Please tell us if you have already been doing other things like this, since it often will break existing drivers. Have you uninstalled anything or installed any drivers (like video drivers, acpi or other networking drivers) by trying to build them from source?

Could you describe a little better what modprobe said? Perhaps even actually quote the exact words?

Do a "locate ieee80211" and show us what the result is.

I'd still like to actually see the result of the earlier commands. Also, which kernel are you using? Show us the output of "uname -a".

Are you sure you're trying to load the right driver? Please also send the results of "sudo lspci" or explain what you meant about all the trouble you had finding out which driver you were trying to load.

Mario


Mario

---

### Post by adverseyaw on 2006-08-15
[FONT="Courier New"]locate ipw2200[/FONT]:
```
--(2018 UTC:Tue,15 Aug 06:$)-- locate ipw2200
/lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200
/lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko
/usr/src/linux-headers-2.6.15-23-686/include/config/ipw2200
...
/home/adverseyaw/MyDownloads/ipw2200/ipw2200-1.1.0/README.ipw2200
/home/adverseyaw/MyDownloads/ipw2200/ipw2200-1.1.0/INSTALL

```
[FONT="Courier New"]
locate ieee80211[/FONT]:
```
--(2019 UTC:Tue,15 Aug 06:$)-- locate ieee80211
/lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ieee80211
/usr/src/linux-headers-2.6.15-23-686/include/config/ieee80211
...
/home/adverseyaw/MyDownloads/ipw2200/ieee80211-1.1.14/remove-old
/home/adverseyaw/MyDownloads/ipw2200/ieee80211-1.1.14/.tmp_versions

```
[FONT="Courier New"]
lsmod | grep ipw[/FONT]: Has no output.  Not found

[FONT="Courier New"]sudo modprobe -a ipw2200[/FONT]
```
--(2022 UTC:Tue,15 Aug 06:$)-- sudo modprobe -a ipw2200
WARNING: Could not open '/lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ieee80211/ieee80211.ko': No such file or directory
WARNING: Error inserting ipw2200 (/lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

[FONT="Courier New"]sudo ifconfig:[/FONT]
```
--(2022 UTC:Tue,15 Aug 06:$)-- sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4A:19:9F:1C
          inet addr:10.71.3.81  Bcast:10.71.15.255  Mask:255.255.240.0
          inet6 addr: fe80::201:4aff:fe19:9f1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2032936 (1.9 MiB)  TX bytes:336207 (328.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2933220 (2.7 MiB)  TX bytes:2933220 (2.7 MiB)

```

[FONT="Courier New"]sudo iwconfig:[/FONT]
```
--(2025 UTC:Tue,15 Aug 06:$)-- sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

[FONT="Courier New"]uname -a:[/FONT]
```
--(2025 UTC:Tue,15 Aug 06:$)-- uname -a
Linux linuxbox 2.6.12-10-686 #1 Fri Jul 7 01:30:06 UTC 2006 i686 GNU/Linux

```

> **mpvano said:**
> Please tell us if you have already been doing other things like this, since it often will break existing drivers. Have you uninstalled anything or installed any drivers (like video drivers, acpi or other networking drivers) by trying to build them from source?

I have used the remove-old script for ieee80211-1.1.14 so the binaries are probably gone. I got this from the [HOWTO]("http://ubuntuforums.org/showthread.php?t=26623") thread.
Other than that all I have installed is 915resolution from the universe for  my laptop screen.

Here is the output when I tried to build the ieee80211-1.1.14 binary:
```
--(2033 UTC:Tue,15 Aug 06:$)-- make
Checking in /lib/modules/2.6.12-10-686 for ieee80211 components...
make -C /lib/modules/2.6.12-10-686/build M=/home/adverseyaw/MyDownloads/ipw2200/ieee80211-1.1.14 modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/adverseyaw/MyDownloads/ipw2200/ieee80211-1.1.14/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/adverseyaw/MyDownloads/ipw2200/ieee80211-1.1.14/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/adverseyaw/MyDownloads/ipw2200/ieee80211-1.1.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [modules] Error 2

```

What is that thing about gcc?

I hope this can point you in the right direction.  As you may see I am in Linux now replying. This hotel has a wired connection in the rooms so I don't have to keep switching back and forth between linux and windows to reply.
Thank you,
AdverseYaw

---

### Post by mpvano on 2006-08-15
I think you've broken things with that script.

I believe that the drivers for your card were already present and ready to use (in fact, I believe I've used them on a notebook I had here for about a week a while ago) before you started following the instructions in the FAQ you refer to. It's for another operating system Ubuntu 5.04. In those days the drivers were not built in. You're running Ubuntu 6.06 (aren't you!). You shouldn't pay any attention to any part of it. It's not for your machine or operating system version!

I think at this point the best thing to do would be to use Synaptic to reinstall your kernel and all it's drivers. You do this by finding the kernel image entry that matches your running kernel (run the command "uname -a" to find that out if you're not sure). Select it with the mouse on the checkbox, even if it's already installed, and pick "mark for re-installation" by clicking with the mouse right button. Then click on apply and wait for the reinstallation to complete.

Once you have done that reboot the computer and we need to go back to finding out if your driver loaded. It's possible it may now be loading all by itself, but if not, we'll need to go back to the first steps I told you to follow.

By the Way...

I'm just another ubuntu user like you. Most of the respondents in these forums are like the two of us - just normal users. This is a community self-help forum. I'm sorry if this is slow going, but I only visit here when I'm not doing other more important things...

Mario

---

### Post by adverseyaw on 2006-08-15
[QUOTE=mpvano]I think at this point the best thing to do would be to use Synaptic to reinstall your kernel and all it's drivers. You do this by finding the kernel image entry that matches your running kernel (run the command "uname -a" to find that out if you're not sure). Select it with the mouse on the checkbox, even if it's already installed, and pick "mark for re-installation" by clicking with the mouse right button. Then click on apply and wait for the reinstallation to complete.[/QUOTE]

Well, you hit that one right on the head.  I installed the latest kernel and when I booted up everything works (sound, wireless, wired, et al).  Now the uname -a gives me:
```
--(0220 UTC:Tue,15 Aug 06:$)-- uname -a
Linux linuxbox 2.6.**15**-**23**-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux

```

The old one was:
```
--(2025 UTC:Tue,15 Aug 06:$)-- uname -a
Linux linuxbox 2.6.**12**-**10**-686 #1 Fri Jul 7 01:30:06 UTC 2006 i686 GNU/Linux
```

It seems I was running the old kernel image with the new Dapper distro.
Everything is working great now.  Thank you for your time and patience.
AdverseYaw

---

