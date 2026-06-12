---
title: "live CD"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Bill-Gates on 2010-01-06
[SIZE=2]I am running a live Ubuntu cd right now and I have a no OS on my hard drive.
My hard drive seems to be failing.
[/SIZE][SIZE=2]
[/SIZE]
[LIST=1]
[*][SIZE=2]Could anyone direct me to the best "tutorial for dummies" on making an ISO? I would like to burn my own.[/SIZE]
[*][SIZE=2] Is it possible to make a live Ubuntu cd with all of the updates and my personal preferences?[/SIZE]
[*][SIZE=2] What are the drawbacks of running live vs. running installed?[/SIZE]
[*][SIZE=2] I don't think my computer will boot to a flash drive but, if it could, would it be better to run Ubuntu from flash vs. a live cd[/SIZE]
[*][SIZE=2] How could I use a flash drive to my advantage running a live cd?[/SIZE]
[*][SIZE=2] Are there any pros' to running live?[/SIZE]
[/LIST]
[SIZE=2]Thanks![/SIZE]

---

### Post by CaptainMark on 2010-01-06
Running from installed will be a lot faster, i mean loads too not just a bit. And running live cds wont save anything, installing will save any changes you make.

---

### Post by Bill-Gates on 2010-01-06
> **CaptainMark said:**
> Running from installed will be a lot faster, i mean loads too not just a bit. And running live cds wont save anything, installing will save any changes you make.

Ok, I get the much faster part. Thanks

Could I save things to flash drives?

Could I burn a new ISO to keep those changes I make?

---

### Post by sanderd17 on 2010-01-06
You can create a flash drive from your cd with the Live USB Creator. But I hope you have enough memory because a Live CD works entirely from RAM. 
Otherwise you can make a live USB on an other computer. 
With a live USB, you can save your data and your installed files but don't be suprised if your live USB will be full after installing a few apps, 
it is very likely this will happen if you compare the size of a normal filesystem (lets say 500 GB) to the size of a normal flash drive (2GB).
Why don't you want to install Ubuntu?

TIP: if you want to use an OS a long time with your USB I would recommend a smaller OS, Puppy linux is very good for this purpose: only 100 MB big. Puppy also supports saving data on the same CD, if the cd isn't terminated.

---

### Post by Bill-Gates on 2010-01-06
> **sanderd17 said:**
> You can create a flash drive from your cd with the Live USB Creator. But I hope you have enough memory because a Live CD works entirely from RAM. 
Otherwise you can make a live USB on an other computer. 
With a live USB, you can save your data and your installed files but don't be suprised if your live USB will be full after installing a few apps, 
it is very likely this will happen if you compare the size of a normal filesystem (lets say 500 GB) to the size of a normal flash drive (2GB).
Why don't you want to install Ubuntu?

TIP: if you want to use an OS a long time with your USB I would recommend a smaller OS, Puppy linux is very good for this purpose: only 100 MB big. Puppy also supports saving data on the same CD, if the cd isn't terminated.


[SIZE=2]Thanks, I will look at Puppy as soon as I learn how to burn an ISO but I sure do like Ubuntu.

I think I am making a live flash right now as we speak. I am attempting to anyway.
I just formatted my usb using Gparted. Now I am using Using USB Start Up Creator.
It finished as I am typing this.
I am not sure my computer will boot to flash but I will try to set it up in the bios. I saw where I had an option to boot to an "unknown device" in my bios so I will give that a go.
I have done all of this from a live cd and so far I can't tell I am running live.

What I would like to do just to see if I can do it is create a live cd with all of the current updates and my preferences. I could have a copy on my flash and a backup on cd.

I have installed Ubuntu a few times but my hard disk is facing "imminent failure" so I want to see what I can do without it.

I thought that I might be able to run live and use my flash as a hard drive.

I was also thinking that if there was a new update or I wanted to make some changes I could burn a new ISO off of my other burner, all while I was live. I think that would be fun.

[/SIZE]       [SIZE=2]I also like the fact no matter what happens that no one can modify my live (terminated) disk as far as a rootkit or malware and everything that falls under the malware umbrella. Everything would have to be ram based and would disappear upon reboot. (I think)[/SIZE]

---

### Post by C.S.Cameron on 2010-01-06
you can make a custom Live CD using Remastersys, (the instructions don't sound easy to me).

You can boot a Live USB using a Boot CD. see [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
(The pendrivelinux web site also has a tutorial).

The above method will also work if you wish to boot a USB drive with a full install on it. For a full install just boot your Live CD, plug in your USB device and run install.

You can use a flash drive to save changes when booted from a Live CD. Let me know if you are interested and I will explain how.

---

