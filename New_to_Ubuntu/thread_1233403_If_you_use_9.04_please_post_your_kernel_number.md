---
title: "If you use 9.04 please post your kernel number"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Sir Jasper on 2009-08-06
Hi,

Thank you.

My regards

---

### Post by doas777 on 2009-08-06
2.6.28-14-generic

---

### Post by TheNosh on 2009-08-06
2.6.28-13-generic

---

### Post by Sir Jasper on 2009-08-06
Hi doas777,

Thanks for your quick response.

My regards

---

### Post by credobyte on 2009-08-06
```
2.6.28-14-generic
	
```

Just curious .. why do you need this info ?

---

### Post by Sir Jasper on 2009-08-06
Hi Credobyte,

I seem to have your version available but System Monitor reports my using 2.6.27-11-generic.

I have Ubuntu with the Xubuntu desktop installed.

I can try googling but any and all advice will be much appreciated.

My regards

---

### Post by credobyte on 2009-08-06
Check your kernel version:
```
uname -r

```

If needed, upgrade it:
```
sudo apt-get dist-update
```

---

### Post by RD1 on 2009-08-06
2.6.30-020630-generic :popcorn:

---

### Post by Sir Jasper on 2009-08-06
> **credobyte said:**
> Check your kernel version:
```
uname -r

```

If needed, upgrade it:
```
sudo apt-get dist-update
```

The first code reports 2.6.27-11-generic

The second (pasted or typed) reports E: Invalid operation dist-update

Thanks for your help.

My regards

---

### Post by TheNosh on 2009-08-06
i'm not sure if this will help you, but i just moved from 2.6.28-14-generic from 2.6.28-13-generic after reading this thread, so heres what i did:

2.6.28-14-generic is in the repos. after reading this thread i checked synaptic and it said i had it downloaded already. i just had to tell grub to boot to it (i did so using KGRUBEditor)

---

### Post by LowSky on 2009-08-06
enter as one long code in terminal, it will update all programs on the the system including the kernel```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by The Cog on 2009-08-06
Have a look in /boot and see what kernels are there. Then have a look in the file /boot/grub/menu.lst and see which kernel grub is configured to load. You can edit menu.lst to change which kernel to boot but you must be careful not to get it wrong and leave the PC un-bootable. Come back here for help if you think menul.st needs editing, and someone can give more detailed advice on doing that.

---

### Post by ubudog on 2009-08-06
2.6.28-11  Hope that helps :)

---

### Post by H2SO_four on 2009-08-06
2.6.28-15-generic

---

### Post by credobyte on 2009-08-06
> **Sir Jasper said:**
> The first code reports 2.6.27-11-generic

The second (pasted or typed) reports E: Invalid operation dist-update

Thanks for your help.

My regards

Woops, sorry .. it should be *dist-upgrade* ( instead of *update* ) 8-[

---

### Post by fooman on 2009-08-06
> **RD1 said:**
> 2.6.30-020630-generic :popcorn:

2.6.30-02063004-generic  :D

---

### Post by Sir Jasper on 2009-08-06
Hi guys and gals,

Getting closish but I&#7743; not quite there.

I have triple boot 8.10, 9.04 (and windows) and both 8.10 and 9.04 have the Xubuntu desktop installed.

9.04 is the default load but I&#7743; almost sure it boots from menu.&#314;st in 8.10 (though 9.04 also has its own menu.lst).

Thanks to everybody for their help thus far.

My regards

PS I added the second Ubuntu system so I could do a few tests and also try out 9.04 upgrade.

---

### Post by Sir Jasper on 2009-08-06
Hi all,

What seemed promising had led nowhere - more help would be appreciated.

If anyone has any questions I will try to answer them in the next hour or so, otherwise tomorrow.

My regards

---

### Post by CJ Master on 2009-08-06
> **Sir Jasper said:**
> Hi all,

What seemed promising had led nowhere - more help would be appreciated.

If anyone has any questions I will try to answer them in the next hour or so, otherwise tomorrow.

My regards

If everything works fine why upgrade the kernel? You could potentially break something for no gain.

---

### Post by Conzo on 2009-08-06
2.6.28-14-generic



Conzo!

---

### Post by wojox on 2009-08-06
```
Hello, wojox

Today's date is Thu Aug  6 19:37:05 EDT 2009 .

This is a Linux machine.

Running kernel-release: 2.6.28-14-generic

Running kernel-version: #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009

On a processor type: i686

That's all wojox !

wojox@wojox-desktop:~$
```

---

### Post by Sir Jasper on 2009-08-06
> **CJ Master said:**
> If everything works fine why upgrade the kernel? You could potentially break something for no gain.

Hi,

I don't have a deep understanding and I merely try to apply what I read in the best possible way.

Yesterday, for the first time in 6 months using Ubuntu the system went horribly and strangely wrong; hence my interest in trying to get the kernel right before going on to other important settings.

My regards

---

### Post by Ubun2 Us3r on 2009-08-06
2.6.28-13-generic

---

### Post by CJ Master on 2009-08-07
> **Sir Jasper said:**
> Hi,

I don't have a deep understanding and I merely try to apply what I read in the best possible way.

Yesterday, for the first time in 6 months using Ubuntu the system went horribly and strangely wrong; hence my interest in trying to get the kernel right before going on to other important settings.

My regards

Post your problem. More then likely it's a problem with XOrg and not your kernel.

---

### Post by anjilslaire on 2009-08-07
2.6.28-14-generic

---

### Post by kg84 on 2009-08-07
As above :)

---

### Post by ruehara on 2009-08-07
2.6.28-14-generic

---

### Post by kpkeerthi on 2009-08-07
2.6.30.4-dell-xps (custom trimmed kernel optimized for Dell XPS laptops)

---

### Post by Sir Jasper on 2009-08-07
Hi everyone,

My problem is resolved after many hours of trial and error.
Thank you to all who helped with information and advice.

My regards

---

