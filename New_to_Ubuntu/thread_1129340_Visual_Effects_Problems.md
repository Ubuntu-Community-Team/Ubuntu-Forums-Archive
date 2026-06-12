---
title: "Visual Effects Problems"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-04-18
Something seems to have happened when I after I updated the Ubuntu 9.04 Beta I just installed. Just after the installation, my Visual Effects was on "Normal" mode. After using Update Manager, I shut down for the night and just now turned it on. Now, I find that it is on the "None" setting. I tried setting it back on "normal, but it deeps telling me that Desktop effects could not be enabled. What happened? How to fix it?

Thanks for your time.

Take care,
RedStarYellowSun

PS: According to Sysinfo => "Hardware" => "Graphic card" => "VGA compatible controller", my card is a:
"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
Subsystem: Lenovo Device 20b5
I hope that helps.

---

### Post by cariboo on 2009-04-18
HAve a look [here]("http:///www.ubuntu.com/testing/jaunty/beta") under Known Issues.

Jim

---

### Post by prshah on 2009-04-18
> **RedStarYellowSun said:**
> after I updated the Ubuntu 9.04 Beta 
my card is a:
"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Unfortunately, there are issues with Intel graphics devices (esp 965's) with Jaunty beta.

I ran into great trouble after upgrading to Jaunty; got a totally garbled screen.  (PS: resolved it by manually specifying the correct resolution for my laptop screen).

It is very likely that your system has fallen back to the vesa driver; to check, open a terminal (Applications-Accessories-Terminal) and post back the output of the following commands```
cat /var/log/Xorg.0.log | grep driver
``` If OK, it should show (among other things) that the "intel" driver and not the "vesa" driver is in use.

If this is the case, post back on how to change to the Intel driver.

If you are in fact using the Intel driver, open a terminal and give the command```
compiz --replace
``` the error messages (if any) will give a clue as to where things are going wrong.

---

### Post by xxeder on 2009-04-18
hi, i have the same problem but with a geforce 7000m.
in 8.10 i couldnt even install the drivers, but wen i upgraded to jaunty, the resolution and drivers were all fixed except for the desktop effects

---

### Post by RedStarYellowSun on 2009-04-19
Thanks for the replies.
So, I see that other people with Intel cards are having this problem, too. Thanks for the info!
And as to the information from Terminal, here it is:```
jutumang@jutumang-laptop:~$ cat /var/log/Xorg.0.log | grep driver
	X.Org XInput driver : 4.0
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) [drm] loaded kernel module for "i915" driver.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
	ABI class: X.Org XInput driver, version 4.0
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
jutumang@jutumang-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```
I hope this helps.

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by prshah on 2009-04-21
> **RedStarYellowSun said:**
> 
(==) Matched intel for the autoconfigured driver
(II) [drm] loaded kernel module for "i915" driver.

Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity[/code]


Your card (identified by 8086:2a02) has been blacklisted by compiz because there are known issues with it. Because of this, compiz refuses to run.

Some Intel onboard cards are blacklisted by Compiz when using XAA acceleration. However, since 8.04 (7.10?) EXA acceleration is the default, so I can't understand where things are going wrong. So we need to check what type of acceleration you are using```
cat /var/log/Xorg.0.log| grep -i -E EXA\|UXA\|XAA\|greedy
cat /etc/X11/xorg.conf | grep -i accel
```

Or if you can't be bothered by all this and just want to burn through without trying any troubleshooting first (read: quick-fix) try```
SKIP_CHECKS=yes compiz --replace
``` from the terminal; it may or may not work, but shouldn't harm the situation any.

---

### Post by kori.mendocino on 2009-04-21
I have the exact same problem - I upgraded to Release Candidate last night, and it doesn't show the Intel GFX problems as known issues anymore. 

```
cat /etc/X11/xorg.conf | grep -i accel
```
doesn't give back any output, and

```
cat /var/log/Xorg.0.log| grep -i -E EXA\|UXA\|XAA\|greedy
```
gives this back

```
(==) intel(0): Using EXA for acceleration
(II) intel(0): Using exact sizes for initial modes
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
(WW) intel(0): DRI2 requires UXA
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II) intel(0): 0x0ed40000-0x0fffffff: exa offscreen (19200 kB)
```

```
SKIP_CHECKS=yes compiz --replace
```
did it for me, desktop effects are just fine now. Here's my output:

```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by prshah on 2009-04-21
> **kori.mendocino said:**
> 
```
(==) intel(0): Using EXA for acceleration
(WW) intel(0): DRI2 requires UXA

```


When using EXA acceleration, you need an additional setting```
Option     "MigrationHueristic"     "Greedy"
``` for best performance.

In Jaunty, with EXA but without the "greedy" option, I experience tearing and other visual noise and disturbance on my Fujitsu Laptop screen. With "greedy" it works perfectly, and is in fact almost twice as fast as Ibex (based on glxgears performance information).

From Jaunty onwards, a new acceleration method DRI2/UXA is available (for Intel chipsets) and looks to becoming the default. While UXA is supposed to be the fastest yet, I've found it to have the same level of performance as EXA/Greedy in Ibex.

In summary, I find a huge performance improvement with EXA/greedy in Jaunty, rather than UXA (which also works fine).

Post back for more instructions if you'd like to use EXA+Greedy or UXA.

---

### Post by ozPATT on 2009-04-21
i just tried SKIP_CHECKS=yes compiz --replace from the terminal and my awn and desktop effects kicked in which is great, but when i restarted, they all disappeared again... should it be installed without the checks then run fine each time? Or do i need to type that in every time i want them activated - which is all the time :D my issue and output is identical to kori, including the blacklist and everything..

---

### Post by RedStarYellowSun on 2009-04-22
> **prshah said:**
> Your card (identified by 8086:2a02) has been blacklisted by compiz because there are known issues with it. Because of this, compiz refuses to run.

Some Intel onboard cards are blacklisted by Compiz when using XAA acceleration. However, since 8.04 (7.10?) EXA acceleration is the default, so I can't understand where things are going wrong. So we need to check what type of acceleration you are using```
cat /var/log/Xorg.0.log| grep -i -E EXA\|UXA\|XAA\|greedy
cat /etc/X11/xorg.conf | grep -i accel
```

Or if you can't be bothered by all this and just want to burn through without trying any troubleshooting first (read: quick-fix) try```
SKIP_CHECKS=yes compiz --replace
``` from the terminal; it may or may not work, but shouldn't harm the situation any.

Thanks for the reply. Sorry for the delay. I had some urgent matters to attend to.
Anyway, here are the results:```
jutumang@jutumang-laptop:~$ cat /var/log/Xorg.0.log| grep -i -E EXA\|UXA\|XAA\|greedy
(==) intel(0): Using EXA for acceleration
(II) intel(0): Using exact sizes for initial modes
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
(WW) intel(0): DRI2 requires UXA
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II) intel(0): 0x0ed40000-0x0fffffff: exa offscreen (19200 kB)
jutumang@jutumang-laptop:~$ cat /etc/X11/xorg.conf | grep -i accel
```

So, what next?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by kori.mendocino on 2009-04-22
prshah, thank you for your continued input. I don't believe that adding the greedy option will help me out here since I don't have any performance issues, it's just that my (our) card has been blacklisted. After some digging, here is the relevant bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)

---

### Post by prshah on 2009-04-22
> **ozPATT said:**
> i just tried SKIP_CHECKS=yes compiz --replace but when i restarted, they all disappeared again

You can permanently add the environment variable to your /etc/environment file; Open a terminal (Applications-Accessories-Terminal) and give the command```
echo SKIP_CHECKS=yes | sudo tee -a  /etc/environment
```

Now,the SKIP_CHECKS environment variable will be set every boot.

> **RedStarYellowSun said:**
> 
(WW) intel(0): DRI2 requires UXA
(II) intel(0): 0x0ed40000-0x0fffffff: exa offscreen (19200 kB)
[/code]


You are using EXA acceleration, which is normal (/correct). You can:

a) Start compiz using the SKIP_CHECKS as mentioned in the previous posts.

If everything works fine, then you are done.

If you face problems (window tearing, color bleeding, display artifacts, display noise) post back for other options, along with a description of the problem you are facing.

---

### Post by RedStarYellowSun on 2009-04-22
> **prshah said:**
> Your card (identified by 8086:2a02) has been blacklisted by compiz because there are known issues with it. Because of this, compiz refuses to run.

Some Intel onboard cards are blacklisted by Compiz when using XAA acceleration. However, since 8.04 (7.10?) EXA acceleration is the default, so I can't understand where things are going wrong. So we need to check what type of acceleration you are using```
cat /var/log/Xorg.0.log| grep -i -E EXA\|UXA\|XAA\|greedy
cat /etc/X11/xorg.conf | grep -i accel
```

Or if you can't be bothered by all this and just want to burn through without trying any troubleshooting first (read: quick-fix) try```
SKIP_CHECKS=yes compiz --replace
``` from the terminal; it may or may not work, but shouldn't harm the situation any.

Okay, here are the results:
Everything appears normal with Firefox above. But when I click on Terminal, I find that the upperbar of Terminal is merged with the upperbar of the Desktop. They are separate, yet the smaller bar is merged to Ubuntu's longer bar. I tried to copy and paste the contents

What can I do?

Thanks.

I tried to copy the contents of Terminal into Ubuntu Forum reply screen, but forgot that I should not use "Ctrl+C" Now, the Terminal is full merged with the Desktop Upperbar. It is one. It has File, Edit, View, Terminal, Help, and strangely enough the weather+clock+ date+shutdown/restart button on the upper left. I cannot move the Terminal, which is covering half of the screen. I have tried moving it to a workspace to the right. yet, it is still here. I tried moving Firefox but received the same results. I cannot move to any workspace. The screen has hung/frozen. except I can still highlight, copy, and paste text. Here are the contents of the Terminal: ```
jutumang@jutumang-laptop:~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
```
Wait, I left-clicked to get Firefox to correct some wrong spelling and Terminal minimised. Unfortunately, the window with the correct spelling does not appear. The Terminal is upperbar is still merged with Desktop upperbar, though Terminal is minimized. All else is the same.
 Please help.
I will restart.
Take care,
RedStarYellowSun

---

