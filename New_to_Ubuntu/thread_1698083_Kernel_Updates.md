---
title: "Kernel Updates"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by jda8818 on 2011-03-01
Hello all:

My first Ubuntu installation (10.04 LTS) was last summer, and I have just resurrected an old P4 machine and again installed 10.04 LTS.  

I have kept the first machine updated when asked to do so, and although the newly resurrected machine is only a couple of days old I just performed the prescribed updates this last hour.

curiously, I seem to  have different versions of the kernel in these two machines, and I'm wondering why that might be:

Last Summer's Installation:
```
ja@HTPC:~$ uname -a
Linux HTPC 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux
ja@HTPC:~$ 
```Most Recent:
```
johnny@morris:~$ uname -a
Linux morris 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux
johnny@morris:~$ 

```I would have thought that since both machines have been updated as suggested they would have the same kernel.  What am I missing?

Thanks to everyone in advance for any comments or suggestions,

JA

---

### Post by jwcalla on 2011-03-01
What's the latest kernel version in /boot on your older machine?

---

### Post by jda8818 on 2011-03-01
Hello jwcalla:

My /boot directory contains:

[LIST]
[*]the grub diirectory
[*]the file abi-2.6.32-22-generic-pae
[*]the file config-2.6.32-22-generic-pae
[*]the package initri.img-2.6.32-22-generic-pae
[*]the file memtest86+.bin
[*]the file System.map-2.6.32-22-generic-pae
[*]the file vmcoreinfo-2.6.32-22-generic-pae
[*]the file vmlinuz-2.6.32-22-generic-pae
[/LIST]
Thank you,


JA

---

### Post by matt_symes on 2011-03-01
Hi

On your old machine open a terminal and type

```
sudo apt-get update
sudo apt-get upgrade
```

Enter your password. It will not be echoed to the screen. What information do they display ?

Is the upgrade holding back your kernel ?

Did you lock your kernel to 22 ?

Do you have the correct repositories enabled ?

Kind regards

---

### Post by jda8818 on 2011-03-01
matt_symes:

Thank you for your reply ...

```
ja@HTPC:~$ sudo apt-get update
[sudo] password for ja: 
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ lucid/partner Translation-en_US   
Hit http://us.archive.ubuntu.com lucid Release.gpg                  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
ja@HTPC:~$ 

```and

```
ja@HTPC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ja@HTPC:~$ 
```As far as the repositories are concerned, they  should be the defaults.

I may have locked the kernel somehow, I had a lot of trouble with the AlsaMixer upgrade situation, how do i check?

(I guess the answer to my original question is that yes, these two installations should have the same kernel)

Thank you for your response, matt!

JA

---

### Post by peculiar penguin on 2011-03-01
You're using the generic kernel on one box and the server/PAE one on the other, dunno if both of these should be available with identical version numbers (and I'm too lazy to look it up right now).

---

### Post by jda8818 on 2011-03-01
Dear Peculiar:

Thank you for your reply!

The earlier is "generic-pae"

and the latter is "generic"

You're saying that the "generic" kernel is a server?  The image file for the installation was "ubuntu-10.04.2-desktop-i386.iso which i got off the ubuntu download site.

Hmmmmmmmmmmmmmmm ...

let me look at the CD ...

JA

---

### Post by peculiar penguin on 2011-03-01
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
> Both the CD and DVD installer of Ubuntu 10.04 automatically installs the  PAE enabled kernel if it detects more than 3 Gb of available memory.Maybe someone else can check what version of this kernel should be available for Lucid.

---

### Post by jda8818 on 2011-03-01
Oops, I think I may have confused "old" machine with "Old" machine.

One machine is fairly new, but Ubuntu was installed last summer.   This is a new machine, but the older of the two installations in this case.

The other machine is old as in having been manufactured around 2000 or so;  i just resurrected it and installed Ubuntu yesterday.  thus this an old machine, but a new Ubuntu installation.

the sudo apt-get update etc that was requested for my "old" machine was for the "new" one with the older Ubuntu install.  

Whew

I'll just pause for a moment ...

JA

---

### Post by matt_symes on 2011-03-01
Hi

> Maybe someone else can check what version of this kernel should be available for Lucid.

I can see 2.6.32.29.35 for generic-pae image and headers. The pae kernel allows one to address more memory than the standard generic kernel.

```
matthew@matthew-laptop:~/Downloads$ apt-cache search linux-image-2.6.*-generic-pae
linux-image-2.6.32-21-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-22-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-23-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-24-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-25-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-26-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-27-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-28-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-29-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.35-22-generic-pae - Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-23-generic-pae - Linux kernel image for version 2.6.35 on x86
matthew@matthew-laptop:~/Downloads$ 
```


You can lock kernels using synaptic package manager. Select the package you want to lock from from the packages menu select lock version. You can also do this using apt-get pinning. Did you do this by chance ?

Kind regards

---

### Post by jda8818 on 2011-03-01
Ah Ha Peculiar!

The new machine with the older install has 4GB of available memory, the Old Old Machine with the newer install has 1GB of available memory.

so maybe ...

JA

---

### Post by jda8818 on 2011-03-01
Hi Matthew,

As far as I can tell, Synaptic Package Manager does not show any locked files or packages.

However, I do remember being annoyed when my sound configuration was broken by a kernel upgrade last fall.  So I may have locked something.   Short to medium term memory loss I guess.

Do you know of a good command line instruction to look for files or packages locked against updates?

As always, thanks in advance for your suggestions, interest and comments.

JA

---

### Post by matt_symes on 2011-03-01
Hi

> Do you know of a good command line instruction to look for files or packages locked against updates?

Yes. Open a terminal and type

```
apt-cache policy
```

That will show you pinned packages in apt and package priorities. 

You could install another kernel and headers manually and do the required updates yourself. However if it's not broke.....

Kind regards

---

### Post by jda8818 on 2011-03-01
Thanks, Matthew,

```
ja@HTPC:~$ apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://archive.canonical.com/ lucid/partner Packages
     release v=10.04,o=Canonical,a=lucid,n=lucid,l=Partner archive,c=partner
     origin archive.canonical.com
 500 http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Packages
     release v=10.04,o=Ubuntu,a=lucid-security,n=lucid,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ lucid-security/universe Packages
     release v=10.04,o=Ubuntu,a=lucid-security,n=lucid,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ lucid-security/restricted Packages
     release v=10.04,o=Ubuntu,a=lucid-security,n=lucid,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
     release v=10.04,o=Ubuntu,a=lucid-security,n=lucid,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Packages
     release v=10.04,o=Ubuntu,a=lucid-updates,n=lucid,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Packages
     release v=10.04,o=Ubuntu,a=lucid-updates,n=lucid,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Packages
     release v=10.04,o=Ubuntu,a=lucid-updates,n=lucid,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
     release v=10.04,o=Ubuntu,a=lucid-updates,n=lucid,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Packages
     release v=10.04,o=Ubuntu,a=lucid,n=lucid,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Packages
     release v=10.04,o=Ubuntu,a=lucid,n=lucid,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Packages
     release v=10.04,o=Ubuntu,a=lucid,n=lucid,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
     release v=10.04,o=Ubuntu,a=lucid,n=lucid,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
Pinned packages:
ja@HTPC:~$ 
```nothing pinned.

well, it's working.  Are we sure that the pae kernel in this machine is obsolete?

once again it is 
```
ja@HTPC:~$ uname -a
Linux HTPC 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux
ja@HTPC:~$ 

```I've learned that the pae kernel addresses more memory, which makes sense.  The resurrected machine contains only 1GB.

so the question becomes:  Is there a later kernel that should reside on this machine?

Thank you for your interest, Matthew,

JA

---

### Post by matt_symes on 2011-03-01
Hi

```
matthew@matthew-laptop:~/Downloads$ apt-cache search linux-image-2.6.*-generic-pae
linux-image-2.6.32-21-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-22-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-23-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-24-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-25-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-26-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-27-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-28-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-29-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.35-22-generic-pae - Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-23-generic-pae - Linux kernel image for version 2.6.35 on x86
matthew@matthew-laptop:~/Downloads$
```

This is the list of the generic-pae kernels i get after an apt-cache search. These do not include any of the backport pae kernels.

The newest one seems to be linux-image-2.6.32-29-generic-pae - Linux kernel image for version 2.6.32 on x86. However i have never used the pae kernels so i would not know if there was anything special about them as far as updating goes.

What does this return for you ?

```
apt-cache search linux-image-2.6.*-generic-pae
```

Kind regards

---

### Post by jda8818 on 2011-03-01
Thanks, Matthew:

```
ja@HTPC:~$ apt-cache search linux-image-2.6.*-generic-pae
linux-image-2.6.32-21-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-22-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-23-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-24-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-25-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-26-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-27-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-28-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.32-29-generic-pae - Linux kernel image for version 2.6.32 on x86
linux-image-2.6.35-22-generic-pae - Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-23-generic-pae - Linux kernel image for version 2.6.35 on x86
ja@HTPC:~$ 
```I'm not sure just how to interpret this, though ...

Thanks for your interest, Matthew,

JA

---

### Post by matt_symes on 2011-03-01
Hi

It's three in the morning here and i have to sleep so, if no one else explains, we can interpret tomorrow. ):P

Kind regards

---

### Post by jda8818 on 2011-03-01
I hear you ... Thanks for your help!

JA

---

### Post by matt_symes on 2011-03-02
Hi

Just want to check the basics.

System->Administration->Software sources->Updates tab; What Ubuntu update options have you got set ?

Also can you post the output of

```
cat /etc/apt/sources.list
```

Also, your kernel is just the plain vanilla generic-pae and not a backport pae ?

Kind regards

---

### Post by jda8818 on 2011-03-02
Hello again Matthew,

My Software Sources Update tab is as follows:

[LIST]
[*]Important security updates (lucid-security) is checked
[*]Recommended updates (lucid-updates) is checked
[*]Pre-released updates (lucid-proposed) is unchecked
[*]Unsupported updates (lucid-backports) is unchecked
[/LIST]
Check for updates daily is checked

Only notify about available updates is selected

Release upgrade: Show new distributiion releases: long term support releases only

```
ja@HTPC:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
ja@HTPC:~$ 

```As far as I know, this is all  plain-vanilla, but having said that, I struggled with HDMI sound last summer and had some hardware issues as well, so ....

Thank you for your interest, Matthew,

JA

---

### Post by JKyleOKC on 2011-03-02
Go into Synaptic, and enter this into the text box at the upper right of the window: ```
linux-image-2.6.32-
```The result should be a list of kernel packages essentially identical to the one you got earlier, but Synaptic will also have checkboxes at the left of each. Most of them will probably be blank but at least one should be solid green, indicating that the package is installed. You may have more than one of them installed; in fact, your automatic updates should have installed many of them (but the list will include several variants for each version)! The "-29" version just came to my systems this morning.

Since the only reason for releasing kernel upgrades during the life cycle of any specific release is to plug security gaps, you really do need to have the most recent available version installed! However you may run into trouble if you use proprietary video drivers; if you do, it will be relatively easy to fix, but you do need to be aware of the possibility...

---

### Post by matt_symes on 2011-03-03
Hi

Just to expand on what JKyleOKC said. Use synaptic to check what kernels you have installed.

If it's only the one then you have a choice. 

1. You can either keep the existing kernel following the old adage 'if it ain't broke don't fix it' or...

2. you can install a new kernel to try to get the benefits of the new kernel but potentially give you the same issues you had before.

I am not sure why it's not automatically updating the kernel for you as i also have a shiny new .29. Remember though 'all that glisters/glitters is not gold'.

I can only assume that it has something to do with the changes you made when you installed to get HDMI working. Maybe you put a hold on the package at the dpkg level, however without knowing what you did it's all guess work.

The decision is yours to make, but i would err on the side of caution.

Kind regards

---

### Post by jda8818 on 2011-03-03
Good morning Matt, and hello and good morning to JkyleOKC!

Thank you for your interest!

First of all, Synaptic responds to ```
linux-image-2.6.32-
``` with only one greened-in box, not surprisingly linux-image-2.6.32-22-generic-pae with the installed version 2.6.32-22.36.  It goes on to report that this (the .36) version is the latest version of the .22 kernel and that it's size is 91.7 MB etc.

Synaptic lists the .21 thru .29.58 kernels as available.

In addition to the HDMI problems (explainable) hardware issues with this system have been a nightmare. Here is the story:

Due to random freezes, seizures, lock-ups and failure to boot. the Zotac H55-ITX-A-E Wifi motherboard was RMA'ed and upgraded by Zotac to the H55-C-E WiFi.  Same situation - lock ups and other unexplainable behavior.  So I take it all apart, sprinkle Holy Water on everything, it boots, then fails at some unpredictable time in the future. 

So, thinks I,  must be a memory problem, although the memory passes all tests I can come up with (flying colors)   So I RMA and replace the memory (Patriot DDR3-1333 2x2GB) without resolution. Same situation.  Motherboard not an issue?  Memory not an issue?

Finally in desperation, I RMA'd the processor (i3-530), got a replacement, and since then the system has been rock solid and trouble-free.  Very weird, since over the years (approaching 30 now) I have never had an issue with an Intel processor unless it was overheated or overclocked.  Even then never permanently damaged that I can remember.

Point being the original Ubuntu installation is still on the original hard disk.  And that original installation has been pounded pretty hard when you consider that while the processor was psychotic I was hacking around with Alsa-Upgrade scripts and .conf files. And I may very well have locked something, I just can't remember what.

So anyway, am I right in assuming I can use Synaptic to mark the .29.58 kernel for installation if I choose to do so?

I have a text file that describes my HDMI experiences, so I could probably re-create that fix if necessary.  I think it only involves running the Alsa-Upgrade script since i have an /etc/asound.conf file in place.

Mainly though, what I would really like to do, is find out why this system does not upgrade the kernel by itself (what I did to it).  so I'll be investigating that further ...

I'm off to work on other projects.  Thank you Matt and Jim for you interest and suggestions, maybe we can investigate this locked kernel further?

Thanks again,

JA

---

### Post by matt_symes on 2011-03-03
Hi

Anytime. Just add a new message to this thread. I am, and will continue to be, subscribed.

Kind regards

---

### Post by jda8818 on 2011-03-05
Hi Matt and Jim:

After various tries trying to jump start the automatic kernel update process without success, and since I had had severe hardware problems in the past (past ? - looking for a fingers-crossed icon) I copped and saved all my old stuff and reinstalled from the latest 10.04.2 32 bit image.

All went smoothly, and although HDMI sound was dead, the latest AlsaUpgrade script also ran smoothly and I'm back with a clean and up-to-date system that so far anyway is rock solid and working perfectly.  Further kernel upgrades will probably break the HDMI pathways, but I'm getting pretty good at taking care of that ...

Thank you for your interest!

JA

---

