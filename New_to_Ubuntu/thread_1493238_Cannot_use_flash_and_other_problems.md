---
title: "Cannot use flash and other problems"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Babuloseo on 2010-05-25
Hi, I cannot install flash because of flashplugin-installer, anyone knows how to remove it? 



I also have problems with boooting and my wireless mouse and keyboard, it seems to run slow at random times after rebooting the computer. It also messed with my internet, I could not access the internet with it plugged in. Switched to PS/2 mouse and keyboard.

There are tons of other bugs, like my system crashing. Tried glxgears and it crashed my pc.

Any attempt to help and find a solution for the problems is appreciated greatly! Just want flash to run and my system to not crash!

---

### Post by Calash on 2010-05-25
We will need a bit more information on the version of Ubuntu you have, and your hardware.  Specifically your video card and if you installed the restricted drivers or not.

Can you give us the output of the following terminal commands

```

uname -a

```

and

```

lspci

```

Your flash question is a bit confusing as the package you listed, flashplugin-installer, is the default installer for flash.  What would also help would be if you can type the following in the address bar of Firefox

```

about:plugins

```

Look for the entry for Shockwave Flash and give us the version number it lists.

---

### Post by Babuloseo on 2010-05-25
> **Calash said:**
> We will need a bit more information on the version of Ubuntu you have, and your hardware.  Specifically your video card and if you installed the restricted drivers or not.

Can you give us the output of the following terminal commands

```

uname -a

```

and

```

lspci

```

Your flash question is a bit confusing as the package you listed, flashplugin-installer, is the default installer for flash.  What would also help would be if you can type the following in the address bar of Firefox

```

about:plugins

```

Look for the entry for Shockwave Flash and give us the version number it lists.

```
Linux bhuiyan-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```


```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```

```

Shockwave Flash
Description:	Shockwave Flash 10.1 r999. Gnash 0.8.7, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc. 
Compatible Shockwave Flash 10.1 r999.
Location:	/usr/lib/gnash/libgnashplugin.so

```

Using Gnash, tried SWFdec also, I cant install flash no matter what i try, and these ones are horrible. I get
this when I try to

```


(Reading database ... 130627 files and directories currently installed.)
Removing flashplugin-installer ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing flashplugin-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Directive 4 on 2010-05-25
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

this will solve all problems if you are using firefox


ref

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Babuloseo on 2010-05-25
Using google chrome

---

### Post by SRST Technologies on 2010-05-25
Little known secret about Ubuntu that will solve tons of problems.  Instead of trying to install flash-nonfree directly (and to get a ton of other software installed that will be nice to have for other things), issue the following command in the terminal:

sudo apt-get install ubuntu-restricted-extras

It should install flash-nonfree correctly.

---

### Post by Directive 4 on 2010-05-25
well, since this will 

"Remove conflicting flash plugins from Ubuntu Linux systems and install  the appropriate version according to system architecture."

maybe it's worth a thought to 

install firefox 
fix flash
remove firefox and head back to crome (if you want!)

---

### Post by Babuloseo on 2010-05-25
trying to fix it currently! thx for all the replies, flash is a big priority and then I have to move onto fixing why my computer crashes.

Firefox 3.6.3 is horrible for me on Linux, seems to work well with other operating systems. I love Firefox, but it made my computer crash (could be because of flash or xserver or something) but i disable flash on it and OI am using Google Chrome now. Cannot wait for the new Firefox release which features the Lorentz technology. If only AMD made a driver for my gfx card....

---

### Post by lovinglinux on 2010-05-25
> **Directive 4 said:**
> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

this will solve all problems if you are using firefox


> **Directive 4 said:**
> well, since this will 

"Remove conflicting flash plugins from Ubuntu Linux systems and install  the appropriate version according to system architecture."

maybe it's worth a thought to 

install firefox 
fix flash
remove firefox and head back to crome (if you want!)

Thanks for pointing to that extension. I have developed it because of the amount of threads with similar Flash issues and it is designed to fix them as you mentioned. But if you are not using Firefox, you can use the commands directly. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Nevertheless, it seems Chrome has a built in flash plugin, so I'm not sure it will solve the problem.

---

### Post by lovinglinux on 2010-05-25
> **Babuloseo said:**
> trying to fix it currently! thx for all the replies, flash is a big priority and then I have to move onto fixing why my computer crashes.

Firefox 3.6.3 is horrible for me on Linux, seems to work well with other operating systems. I love Firefox, but it made my computer crash (could be because of flash or xserver or something) but i disable flash on it and OI am using Google Chrome now. Cannot wait for the new Firefox release which features the Lorentz technology. If only AMD made a driver for my gfx card....

Lorentz is really nice. If you want to try it, see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

You can also easily test it without removing your current version or affecting your user profile with [FoxTester](http://foxtester-extension.blogspot.com/). I'm also the developer of that extension, so feel free to ask any questions.

---

### Post by Babuloseo on 2010-05-25
Still cannot install the Adobe flash plugin, removed Swfdec,Gnashs,etc....
I keep getting this error, I have tried some of the things you mentioned....


```

Setting up flashplugin-installer (10.0.45.2ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by lovinglinux on 2010-05-25
Try:

```
sudo dpkg-reconfigure flashplugin-installer
```

---

### Post by Babuloseo on 2010-05-25
> **lovinglinux said:**
> Try:

```
sudo dpkg-reconfigure flashplugin-installer
```

```

/usr/sbin/dpkg-reconfigure: flashplugin-installer is broken or not fully installed

```

I opened firefox a while ago and CRASHED, it was LORENTZ too.. but i was just checking addons and plugins, when baam, everything freezes. So far with Google Chrome there has not been that many crashes (only 1 )

---

### Post by Babuloseo on 2010-05-25
Anyone else that can help or give input? I would really like to get flash working with both Google Chrome and Firefox.

---

### Post by lovinglinux on 2010-05-25
> **Babuloseo said:**
> Anyone else that can help or give input? I would really like to get flash working with both Google Chrome and Firefox.

EDIT: Nevermind. I must be going nuts, since this has already been suggested.

Try:

```
sudo apt-get purge flashplugin-installer
```

---

### Post by durand on 2010-05-25
Remove it first with 
```
sudo dpkg -r flashplugin-installer.
```

It looks like it got corrupted or something.

---

### Post by Babuloseo on 2010-05-25
Same error
```


$ sudo dpkg -r flashplugin-installer
(Reading database ... 132167 files and directories currently installed.)
Removing flashplugin-installer ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing flashplugin-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-installer

```

---

### Post by durand on 2010-05-25
Uhm, looks like the flash preinst script is buggy.

Try this:

```
sudo mv /var/lib/dpkg/info/flashplugin-* .
```

Then repeat the removal command posted previously.

---

### Post by Babuloseo on 2010-05-25
It got removed! Wow it worked! I wonder if i can install flash now. Now only if i can figure out what is making my system crash, currently glxgears and firefox crashes it >.>

Flash is working :)

---

### Post by durand on 2010-05-25
Awesome! What was it that did it?

---

### Post by Babuloseo on 2010-05-25
The commands that you prescribed! I can use flash now *heeheehee*
Anyways, think you can solve my other problems... glxgears seems to crash, and my system crashes often.

---

### Post by cuberts on 2010-05-25
> **Babuloseo said:**
> Hi, I cannot install flash because of flashplugin-installer, anyone knows how to remove it? 



I also have problems with boooting and my wireless mouse and keyboard, it seems to run slow at random times after rebooting the computer. It also messed with my internet, I could not access the internet with it plugged in. Switched to PS/2 mouse and keyboard.

There are tons of other bugs, like my system crashing. Tried glxgears and it crashed my pc.

Any attempt to help and find a solution for the problems is appreciated greatly! Just want flash to run and my system to not crash!First you should get all of the Updates from the Update manager

---

### Post by Babuloseo on 2010-05-25
Ok I have all the updates

---

### Post by Babuloseo on 2010-05-25
My computer is crashing frequently, like when i enlarge and minimize screens, go on firefox and run glxgears.

---

### Post by lovinglinux on 2010-05-25
> **Babuloseo said:**
> My computer is crashing frequently, like when i enlarge and minimize screens, go on firefox and run glxgears.

Check if you have the latest driver for your graphics card. Go to "System >> Administration >> Hardware Drivers".

---

### Post by Babuloseo on 2010-05-25
Thats the funny part, using the opensource ati driver, I have a radeon 9550, propriety driver stopped working ever since 9.04 :(. Have not been able to run WoW ever since then >.>.

Funny thing is my integrated  nvidia geforce 6100 has driver for the latest versions of ubuntu but not this computer.

---

### Post by durand on 2010-05-26
Well, you need to install them. If you can't get them via hardware drivers, try installing them from the manufacturer's website. I'm still not sure if you have an nvidia or an amd card here...

---

### Post by Babuloseo on 2010-05-26
Ati card is what i have, the nvidia pc seems to be working fine.

Ubuntu crashes like every 3 hours or 4 hours. Have not tested videos, just editing documents,ppt, images, and web surfing.

---

### Post by durand on 2010-05-26
I have absolutely no experience with ATi but I think if you go to their website, you can get linux drivers. Or better, search google for ati and ubuntu, specifically your card.

---

### Post by Babuloseo on 2010-05-26
I do not think the propriety driver supports the latest kernel or X server version, and etc. AMD stopped supporting my old card a while ago.

Please I am not sure whats going on and need a fix! I am crashing constantly and need to get it fixed so that I can do productive work.

---

### Post by durand on 2010-05-27
Post a bug at launchpad.net for it then. I have no idea, sorry :(

---

### Post by Babuloseo on 2010-05-29
Ubuntu 10.04 is making my head spin, its not suited for old ATI cards..
Will post the bug in launchpad soon, if anyone knows how to solve my crashing problem it will be great!

I also managed to stop glxgears from crashing by running a specific command

---

