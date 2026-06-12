---
title: "Ati Drivers"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by L2linux on 2009-08-08
I want to install an ati driver for my desktop which has a raidon HD 4870. The driver is: 

ati-driver-installer-9-7-x86.x86_64.run. 

It is saved on my desktop.

When I type 
./ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty

However when I put this in terminal I get: 

bash: ./ati-driver-installer-9-7-x86.x86_64.run: No such file or directory

What am I doing wrong?

---

### Post by mcduck on 2009-08-08
First, before you even continue with the driver you downloaded, go to System/Administration/Hardware Drivers, and if it offers to install you drivers then use that instead.

Only if that doesn't work for you continue with the package you downloaded. And to install it oyu have to run the install command in the same directory where the package you downloaded is. So if the package is in your desktop, start by running "cd ~/Desktop" to move into your desktop directory. After that the command you tried should work.

---

### Post by L2linux on 2009-08-08
It is already enabled, but is it the same driver as the one I installed? I want to install the Orange box on Ubuntu so I can get rid of windows once and for all.

---

### Post by 3rdalbum on 2009-08-08
> **L2linux said:**
> It is already enabled, but is it the same driver as the one I installed? I want to install the Orange box on Ubuntu so I can get rid of windows once and for all.

Yes. If the Hardware Drivers program shows the ATI driver as being installed and active, then you are using the same driver that ATI provides.

I'm not familiar with this "Orange box" or how it relates to getting rid of Windows - is this something we might be able to help you with?

---

### Post by mike1234 on 2009-08-08
I would stick with your current driver also. You will not gain anything by installing this driver from ATI. Catalyst control panel still looks and functions the same. Albeit quite ugly I might add. If you do manage to do a "sudo, gdm stop ctrl, alt F1 and all that", chances are the first Ubuntu kernel update will remove this driver anyways. And it will never update itself like synaptic does. You'll have to manually install updates. You might gain the ATI splashscreen at bootup. (Big Deal) :confused:. Truthfully Linux drivers from ATI and Nvidia aren't any better than what Ubuntu offers. Debian is another story..........

M.

---

### Post by Vakman on 2009-08-08
If your current driver works do not change it. I do find that the ones in Hardware Drivers do not always work as well but since this is the same driver this time anyway. May as well keep it.

> **3rdalbum said:**
> Yes. If the Hardware Drivers program shows the ATI driver as being installed and active, then you are using the same driver that ATI provides.

I'm not familiar with this "Orange box" or how it relates to getting rid of Windows - is this something we might be able to help you with?

:lolflag: That made my day, sorry. You really have no reason to know to be honest unless you have played it. Just the way you said it made me laugh. The Orange Box is a collection of Steam games for Windows (I assume he is going to try to install them under Wine). Contains Team Fortress 2, Half-Life 2, Portal, HL2: Episode 1 + 2. Unless there is another meaning I am unsure of, which would be funny because I didn't know it this time :P

---

