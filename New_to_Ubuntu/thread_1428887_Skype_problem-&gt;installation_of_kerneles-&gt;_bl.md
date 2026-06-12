---
title: "Skype problem-&gt;installation of kerneles-&gt; black screen"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by stevand on 2010-03-13
Dear All,
I purchased brand new Lenovo ThinkPad SL510 which has Windows 7 preloaded, and asked IT guy to install Ubuntu as dual boot.

I updated (or up-grated) to Carmic 9.10 if I am not mistaken.

I put the skype and I tried to get mic to work by looking at many posts and tried to do what some people recommended.

I installed some KERNELS by following some instructions, hoping that this will solve mic problem and
 I found myself with BLACK SCREEN

with the 

login:

prompt. If I restart computer I am getting the login: prompt and black screen

 Can anyone get me out of this mess ... PLEASE 
THANKS
stevan

---

### Post by MichealH on 2010-03-13
black screen? Is that what you are referring to, A kernel panic?

---

### Post by dmillard10 on 2010-03-13
While I can't help with the kernels and the blank screen, the only thing that needs to be done to install Skype is to download the .deb of appropriate architecture from [this]("http://www.skype.com/download/skype/linux/choose/") site and install it.

---

### Post by stevand on 2010-03-13
> **MichealH said:**
> black screen? Is that what you are referring to, A kernel panic?

no I have a place to login:
and I login ... I see files and everything but I am like on unix terminal .... do not have icons and do not understand ow to get them back ... like login screen and others ...

---

### Post by stevand on 2010-03-13
> **dmillard10 said:**
> While I can't help with the kernels and the blank screen, the only thing that needs to be done to install Skype is to download the .deb of appropriate architecture from [this]("http://www.skype.com/download/skype/linux/choose/") site and install it.

I installed skype, and I was able to login into skype and everything was perfect except that my microphone did not work .... and then I tried to do probably something that is not for my machine ... some Alsa stuff to get mic to work ... it resulted that I installed some kernels hoping that this will work and I ended up on the terminal line .. after restart

---

### Post by oingk on 2010-03-13
Don't worry. I also installed Ubuntu a couple of days ago, all I can say is that things are *probably* not as bad as you fear.

In regard to Skype, all you need to do like the other person said is to download and install it, it should work "fine" (not so fine as it does with Windows, bacause only an older vesion is available for Linux, as far as I know).

Regarding the black screen, I would guess you're just in a place that you don't understand. Describe it here as well as you can and I'm sure one of the more experienced will be able to help you.

Also this may be stupid but try clicking Control-Alt-F7 this may take you to your desktop

---

### Post by stevand on 2010-03-13
Also,
I tried to work out with some help posts but I was not successful, and when I type

startx

I get a black screen whit the arrow associated with the mouse but nothing else?

---

### Post by dmillard10 on 2010-03-13
Try typing

```
startx
```

after logging in.

---

### Post by stevand on 2010-03-13
I tried Control-Alt-F7 and there is not change in the state of the screen 

Also I am right now in the boot and I see that I installed

Linux 2.6.31-20- generic
Linux 2.6.31-20- generic (recovery mode)
Linux 2.6.31-19- generic-pae
Linux 2.6.31-19- generic- pae( recovery mode)
Linux 2.6.31-19- generic
Linux 2.6.31-19- generic (recovery mode)
Linux 2.6.31-17- generic
Linux 2.6.31-17- generic (recovery mode)
Linux 2.6.31-16- generic
Linux 2.6.31-16- generic (recovery mode)
Linux 2.6.31-15- generic
Linux 2.6.31-15- generic (recovery mode)
Linux 2.6.31-14- generic
Linux 2.6.31-14- generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on/dev/sda1)
Windows 7 (loader) (on/dev/sda2)

this is in the boot process ...

---

### Post by stevand on 2010-03-13
I tried
startx
but it gives me just black screen with the mouse pointer ..... nothing else and I can not do anything further I need to restart at the power button

also when I login at the commend line :
and I typed 
$ls

I can see

linux-2.6.31
linex_2.6.31-20.57.diff.gz 
linux_2.6.3-20.57.dsc
linux_2.6.31.orig.tar.gz
Desctop
Documments
Dowloads
Music
Pictures
Public
Templates
Videos
pulse-backup

---

### Post by MichealH on 2010-03-13
> **stevand said:**
> I tried Control-Alt-F7 and there is not change in the state of the screen 

Also I am right now in the boot and I see that I installed

Linux 2.6.31-20- generic
Linux 2.6.31-20- generic (recovery mode)
Linux 2.6.31-19- generic-pae
Linux 2.6.31-19- generic- pae( recovery mode)
Linux 2.6.31-19- generic
Linux 2.6.31-19- generic (recovery mode)
Linux 2.6.31-17- generic
Linux 2.6.31-17- generic (recovery mode)
Linux 2.6.31-16- generic
Linux 2.6.31-16- generic (recovery mode)
Linux 2.6.31-15- generic
Linux 2.6.31-15- generic (recovery mode)
Linux 2.6.31-14- generic
Linux 2.6.31-14- generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on/dev/sda1)
Windows 7 (loader) (on/dev/sda2)

this is in the boot process ...

Try the Linux 2.6.31-19- generic It may just be a new kernel problem

---

### Post by stevand on 2010-03-13
> **MichealH said:**
> Try the Linux 2.6.31-19- generic It may just be a new kernel problem

I tried it for each of kernels but it is the same for Linux 2.6.31-19- generic 
I just get
name-laptop login:
Password:

---

### Post by stevand on 2010-03-13
Resolved by kendankendan post

---

