---
title: "[SOLVED] Broadcom 4311 worked on Gnome, but not on KDE"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by MarlonDean on 2008-09-18
Hi,

I recently installed Kubuntu, as I was tired of the gnome enviroment. 

I went to enable my restricted drivers, but only my Nvidia card appeared in the list, and not my broadcom wireless as it did in gnome.

So I fired up Adept package manager and installed BCM43XX-fwcutter. That installed fine but still no wireless. Am I missing a step? I am pretty sure i have the 32bit version installed as uname -a returns:

Linux laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux                                                                                             

Please also note that Ndswrapper wont be an option for me as I have to use kismet on a regular basis.

Thanks in Advance!

---

### Post by MarlonDean on 2008-09-18
bump

---

### Post by Ayuthia on 2008-09-18
Did you try using b43-fwcutter instead of bcm43xx-fwcutter?  The bcm43xx is the depreciated module.

---

### Post by MarlonDean on 2008-09-19
Yes I did install it, any other suggestions?

---

### Post by Ayuthia on 2008-09-19
Can you post the results of:
```
lshw -C network
```

---

### Post by ammikulka on 2008-09-19
im pretty sure if you use the package manager it doesnt work, i've read that if you install them through the terminal they are more likely to work. I dont know why, but it worked like that for me

---

### Post by MarlonDean on 2008-09-22
Ok, because I was in need of my wireless, I formatted and installed ubuntu again, but now I dont have the option to install my broadcom in the restricted hardware anymore! I dont understand it, i am using the wireless in windows now and it works, no problem...

Why has my wireless disappeared even if it is a fresh install? I am so confused....

---

### Post by MarlonDean on 2008-09-22
The output of lshw -C network gives nothing, it just seems to hang with the output "PCI (sysfs)"

---

### Post by MarlonDean on 2008-09-22
uname -a outputs Linux Laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

This means I am running the 32bit version, right? I dont understand why it worked in the past but now it doesn't

---

### Post by Ayuthia on 2008-09-22
> **MarlonDean said:**
> The output of lshw -C network gives nothing, it just seems to hang with the output "PCI (sysfs)"

It might hang if you use it in sudo mode.  Is that what happened?

> uname -a outputs Linux Laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

This means I am running the 32bit version, right? I dont understand why it worked in the past but now it doesn't 
You are correct.  This is the 32-bit version.  The 64-bit version shows x86_64 instead of i686.

By the way, do you have the rev 01 or the rev 02 version of the 4311 card?  You can find this out by typing (in the Terminal):
```
lspci -nn
```If I recall correctly, the rev 02 card did have some problems in 8.04, but I think that it is supposed to work fine in 8.04.1

---

### Post by MarlonDean on 2008-09-22
I have revision 2 of the card. And yes I ran lshw -C network as sudo, but it gives me the same output when run as a normal user. So you suggest Kubuntu 8.04.1?

---

### Post by Ayuthia on 2008-09-22
I think that you might be better off if you tried 8.04.1.  Either that or install ndiswrapper, get the updates, and then install b43.

---

### Post by MarlonDean on 2008-09-22
Ok, off I go to download 8.04.1 I will let you guys know tomorrow what the outcome was.

Do you think I should try the daily build of ibex? or is it still really buggy?

---

### Post by Ayuthia on 2008-09-22
> **MarlonDean said:**
> Ok, off I go to download 8.04.1 I will let you guys know tomorrow what the outcome was.

Do you think I should try the daily build of ibex? or is it still really buggy?

It is in the alpha state so it is hard to say.  Things can go wrong.  Usually things are pretty stable, but I have seen times where things did break and you have to go in by live CD to fix it.  If you know what you are doing, then it should not be a problem.

---

### Post by MarlonDean on 2008-09-23
8.04.1 solved the problem. Thanks

---

