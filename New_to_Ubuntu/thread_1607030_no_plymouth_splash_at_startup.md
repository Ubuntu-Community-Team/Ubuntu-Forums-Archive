---
title: "no plymouth splash at startup"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-10-27
my ubuntu 10.10 shows no splash screen animation at boot time.It only shows a blinking cursor for about 15 seconds and then comes directly to the login screen.:( 

This is a problem i'm facing from 10.04, though on that version the splash screen showed atleast for half second and the boot time was also faster.

I might also mention this is no issue of nvidia or ati graphics card, my laptop is hp 520 and it has mobile intel 945gm express chipset.

Hoping someone replies soon.:confused:

---

### Post by ECas123 on 2010-10-28
Bump. I'm having the same issue too. I get the cursor for 10 seconds then I see the final second of the splash followed by the login.

---

### Post by garvinrick4 on 2010-10-28
[LEFT]This makes graphic drivers hit before mountall mounts your /
it is a fix from launchpad #540801 that works.

```
su -i
```[/LEFT]
```
[LEFT]echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 
[/LEFT]

```Hit ctrl/d

---

### Post by ECas123 on 2010-10-28
> **garvinrick4 said:**
> [LEFT]This makes graphic drivers hit before mountall mounts your /
it is a fix from launchpad #540801 that works.

```
su -i
```[/LEFT]
```
[LEFT]echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 
[/LEFT]

```Hit ctrl/d

Is that a terminal command? I try entering su -i but it tells me command not found

---

### Post by Hatsune Miku on 2010-10-28
> **ECas123 said:**
> Is that a terminal command? I try entering su -i but it tells me command not found

Do this then,

```
sudo su -i
```


Also on a side comment. Does this also work for NVIDIA cards? i would like to have Native splash/resolution as well :)

---

### Post by garvinrick4 on 2010-10-28
> **ECas123 said:**
> Is that a terminal command? I try entering su -i but it tells me command not found
I am sorry 
```
sudo -i
```
Just puts you in root.

---

### Post by garvinrick4 on 2010-10-28
> **Hatsune Miku said:**
> Do this then,

```
sudo su -i
```Also on a side comment. Does this also work for NVIDIA cards? i would like to have Native splash/resolution as well :)
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
Scott James Remnant is writer of post #2 seems when he says something
it is worth listening to.

---

### Post by dhiman33 on 2010-10-28
:P Ok, that fixed the plymouth problem. But the boot process is still slow. I thought ubuntu 10.10 could boot within 10 seconds! Any way to achieve that?:confused:

---

### Post by garvinrick4 on 2010-10-28
> **dhiman33 said:**
> :P Ok, that fixed the plymouth problem. But the boot process is still slow. I thought ubuntu 10.10 could boot within 10 seconds! Any way to achieve that?:confused: No you get what you get. It has 3 packages to run on the get go
ureadahead, graphic drivers now and mountall and what your machine gives you
is what you are going to get out of it. 
There are other graphics you can use in plymouth though.
Go to Synaptics and type in plymouth and choose some themes, solar, fade in and such like about 6 or 7 of them I think. Then run this and choose by number which one to use.
Here is the code after you choose themes in Synaptics and install them.
                     ```
sudo update-alternatives --config default.plymouth
```Now Choose your theme by the number it asks you. Then
                     ```
sudo update-initramfs -u 
```
Please mark thread as Solved under Threads and tools.

---

### Post by dhiman33 on 2010-10-29
](*,)But any old version of ubuntu could boot faster than that.First, I get a blinking cursor for about 15 sec., then plymouth splash for about 12 sec. Even a fresh install of xp would take less than that time!:confused: Are you sure there's no way to cut down the time(like updating driver etc.) Also I'm on a dual boot.Can that effect the boot time?(Here I'm not considering the 10 sec timeout of grub loader)

---

### Post by Omnomnom on 2010-10-29
Having 2 operating systems in a dual boot cannot hinder the loading times, just boil some water for a coffee while you wait. Having 2 or more partitions with different operating systems is just like having 2 HDD's, each with a different operating system.

---

### Post by dhiman33 on 2010-10-30
Ok, perhaps I should put that question in another thread. BTW, I think the boot time has improved about 5 sec for my ubuntu after using it for 2-3 days. So,I won't bother now about reaching that 10 sec boot time.I'm gonna mark this thread as solved for now.:guitar:

---

### Post by tsger on 2010-10-30
I found this link helpful...still slow, though.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by dhiman33 on 2010-10-31
Thnks for the link tsger=D>. I'll try the startup manager method the nxt time I'm gonna install ubuntu in some machine(Right now my ubuntu shows the plymouth o.k, so better not experiment more with this!:wink:).

---

### Post by Mike_tn on 2010-11-16
> **garvinrick4 said:**
> 

```
sudo -i
```
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

```Hit ctrl/d

Thanks garvinrick4, fixed my splash screen problems !!

Check this splash screen for Maverick, works good in Maverick with your fix
no I'm not advertising, just stumbled on it and liked it, just sharing
[http://www.n00bsonubuntu.net/content/install-dm-ubuntu-plymouth-theme-ubuntu-1010-maverick-meerkat](http://www.n00bsonubuntu.net/content/install-dm-ubuntu-plymouth-theme-ubuntu-1010-maverick-meerkat)

---

### Post by same.500 on 2010-12-12
Thank you!:D
I had the same problem.

---

### Post by same.500 on 2010-12-12
Thank you!:D

---

