---
title: "Minor annoyances"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by pj_kare on 2010-05-13
I have a USB flash drive plugged in permanently and since a clean install of Lucid, each time I go to open it for the FIRST time I always have to double double-click (double click twice) on the desktop icon, at first I thought I may have just  been getting sloppy with my double clicking.

I was also wondering why Ubuntu has to change your system clock each time you do a new install (or re-install). (Don't know about upgrade as I haven't done one). Why doesn't it just accept the time you already have set? It did it with my first Ubuntu install, Feisty, then again when I did a clean install of Karmic and now again with Lucid.:confused: 
Until you set up time servers / internet etc it's not like it has a way of checking.

---

### Post by ubunterooster on 2010-05-13
I have similar click problem but never thought twice...Hmm what is causing that?

Does it not correct the time once it connects to the Ubuntu server for updates?

---

### Post by ManiDhillon on 2010-05-13
Because while installing you must have chosen "System Clock is set to UTC". That is why Ubuntu changed your clock. It's not a bug or problem.

---

### Post by pj_kare on 2010-05-13
Thank you for the reply **ubunterooster** glad the double click thing is not just me. It is OK after the first time.

I usually just fix the time/date after install finishes. So I'm not sure whether it would correct the time after connecting to the Ubuntu server. No biggy.... I just don't know why it (Ubuntu) needs to change time/date at all. (Except when checking with time server).

---

### Post by pj_kare on 2010-05-13
@ManiDhillon Thank you for your reply also, I have searched before and learnt about the UTC, though as far as I know all I do is select Sydney/Australia as my time zone during install (it's my closest capital city), I don't ever remember seeing anything about choosing (or not choosing) UTC. I can't imagine I have missed it on every install or re-install. I guess it is possible though.

---

### Post by ubunterooster on 2010-05-13
Go to System>administartion>time and date.

Click on the padlock and under "configuration" choose manual. (or adjust the settings otherwise as you want)

---

### Post by ManiDhillon on 2010-05-13
Well in live environment UTC System clock is used by default as I think because I haven't seen that after 8.04 though I can't remember for sure.
But I always use alternate CD to install ubuntu and on that you asked for your choice of time zone and UTC. Also if you are connected to internet while installing, your system time is automatically set up.

---

### Post by pj_kare on 2010-05-13
> **ManiDhillon said:**
>  Also if you are connected to internet while installing, your system time is automatically set up.

Thanks again ManiDhillon ,well that could be half the problem right there.....I am STILL on dialup. Takes a bit of setting up with Gnome-PPP and its dependencies, setting up pppconfig and also setting up dialup account before I can get online.

Also, my dialup is so slow I have to order burnt copy of (full) install disc from here-> [http://ubuntu.net.au/](http://ubuntu.net.au/)

(It's not that we don't have broadband here, it's just that I'm 13km from town on a farm, using OLD!!!! phone lines which are barely capable of even carrying dial up.) :(

---

### Post by ManiDhillon on 2010-05-14
> **pj_kare said:**
> Thanks again ManiDhillon ,well that could be half the problem right there.....I am STILL on dialup. Takes a bit of setting up with Gnome-PPP and its dependencies, setting up pppconfig and also setting up dialup account before I can get online.

Also, my dialup is so slow I have to order burnt copy of (full) install disc from here-> [http://ubuntu.net.au/](http://ubuntu.net.au/)

(It's not that we don't have broadband here, it's just that I'm 13km from town on a farm, using OLD!!!! phone lines which are barely capable of even carrying dial up.) :(

Well around two years ago I had the same situation with Dial Up. I used to request copies of Ubuntu from friends and sometimes from [https://shipit.ubuntu.com](https://shipit.ubuntu.com)

But now I have a 2 Mbps line at home and 1.5 Mbps 3G connection on my mobile. So connectivity and downloading is not a problem. Why don't you use 3G or 4G if you don't have DSL line in your area?

---

### Post by Black Hawk on 2010-05-14
If you only have to duble click twice on the usb flash drive icon the first time after you boot up it might be because the flash drive doesn't automaticly mounmt. So you first have to double click once to mount it, then double click again to open it. I'm not on lucid and i don't have a flash drive so i can't test. 

If your flash drive is permanently plugged in you can add it as an entry to /etc/fstab

---

### Post by pj_kare on 2010-05-15
> Why don't you use 3G or 4G if you don't have DSL line in your area?To quote another post in these forums with regards to alternatives to dial up,  > "other saps lack financial resources".Yep, that's about right, though we only have one carrier servicing our area, and they are quite expensive. For a decent usage limit that is....

@Black Hawk, yes, I think you may be right, this is what I was thinking also. Though it hasn't been an issue before.

---

### Post by Centx on 2010-12-06
Have this same problem, but it only happens with certain disks, like my LVM2 software JBOD and my encrypted disk.

---

