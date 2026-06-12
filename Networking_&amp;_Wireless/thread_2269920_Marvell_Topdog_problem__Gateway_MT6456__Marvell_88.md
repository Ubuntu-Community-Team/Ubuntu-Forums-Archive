---
title: "Marvell Topdog problem / Gateway MT6456 / Marvell 88w8362e"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by kananesgi on 2015-03-19
New to Linux. I've dabbled with it a few times, but never anything serious. I bought this laptop on eBay for cheap, fully working with Win7 Ultimate. With only 1gb of RAM, it ran like a snail with Win7. I just got the computer to play with and for a side project, so I decided to try Linux to see if I could get it to run better. At first, I tried installing Lubuntu along side Windows 7, but for some reason, GRUB wouldn't install and I could not get it to boot into the lubuntu installation. I finally gave up and decided the thing was little more than a paper weight under Windows, so I went whole-hog and blanked it out, reformatted, and installed lubuntu 14.04 LTS. The computer works great now from my initial tests, but the wifi adapter doesn't work.

I've been researching and trying to fix this all night, and I think I've run into a roadblock. The best success has been from following chili555's advice in this thread:

[http://ubuntuforums.org/showthread.php?t=2186043](http://ubuntuforums.org/showthread.php?t=2186043)

The problem I'm having is I have no way to connect this computer to the internet. I'm having the same problem the fellow in the thread had, that was apparently solved by compiling a fresh build of ndiswrapper, but from what I'm finding, the computer needs internet to do that. My internet access is provided by the mobile hotspot feature on my phone, so I cannot access the net without wireless. I managed to install ndiswrapper by downloading them on this computer (my main Windows laptop) and loading them onto the usb drive that I used to install lubuntu to begin with.

Everything worked perfectly to the point in the thread where chili555 said to run:

```
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
```

The first command returns this:

```
module configuration already contains alias directive
```

10 times.

The second command doesn't return anything, but takes about 10 seconds before the cursor comes back.

The third command returns the fatal error from the previous thread.

In the "Start" menu (not sure what to call it in linux) under system tools there is now a tool called "Windows Wireless Driver" which shows the driver is installed and the hardware present, but I still don't have any wifi access. When I click on Configure Network, I can see my wifi network (last used: never), but if I select it and try to edit it, a window flashes up and disappears. It was popping up an error dialog earlier, but now it isn't.

Is there any way I can solve this without hard-wire internet access? I'm about to break down and buy a USB wifi adapter in the hopes that it would fix the problem, but I'd rather get this working as it stands if I can.

BTW, I know this is a topic that's been gone over several times. I've gone through those posts and still have problems.

---

### Post by kananesgi on 2015-03-21
well, I bought a USB adapter that superseded this. Now I have another problem with it. New thread for the new problem.

---

