---
title: "Installing KDE without installing redundant apps"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by zer010 on 2010-11-11
I have a sweet running 10.04 system running. Currently, my only DE is GNOME, but I would like to have the option of running KDE. However, I don't want to install a bunch of redundant apps. My GNOME apps are just fine. I understand that some managers and apps will be inevitable, but I would like to minimize the footprint that KDE will impose.  From this: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) , I see I have three options. I'm already ruling out the first the first option, as it contains a lot of redundant packages. 
So which one should I use, kde or kde-core?

---

### Post by Stafke on 2010-11-11
If you want to minimize your KDE-footprint, as you say, than KDE-core could be your choice. You're always free to install other packages afterwards if you want or move 'one step up' to kde instead of kde-core.

If afterwards you're not happy with KDE or it has installed too many packages and you just want to go back to gnome, there is a nice script at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by zer010 on 2010-11-11
Thanks for the tip! I had a look at the link you provided and it says that the removal command might uninstall a few packages that I might want to keep. If I installed kde-core, wouldn't  "sudo apt-get autoremove kde-core" do the job?  Perhaps it might leave some stuff behind?

---

### Post by sandyd on 2010-11-11
> **zer010 said:**
> I have a sweet running 10.04 system running. Currently, my only DE is GNOME, but I would like to have the option of running KDE. However, I don't want to install a bunch of redundant apps. My GNOME apps are just fine. I understand that some managers and apps will be inevitable, but I would like to minimize the footprint that KDE will impose.  From this: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) , I see I have three options. I'm already ruling out the first the first option, as it contains a lot of redundant packages. 
So which one should I use, kde or kde-core?

use kde-minimal

---

### Post by zer010 on 2010-11-11
Thanks, sandy! *thumbs up*

---

### Post by zer010 on 2010-11-11
I installed kde-minimal, but I'm guessing that KDE would run better on a machine with higher specs than mine. It was fairly slow in response and load times.  No matter how many times I try using KDE, I still can't stand using it. I autoremoved it already. I just can't see what all the fuss is about.  I'll just stick with GNOME.
Thanks for everyones help.

---

### Post by sandyd on 2010-11-11
> **zer010 said:**
> I have a sweet running 10.04 system running. Currently, my only DE is GNOME, but I would like to have the option of running KDE. However, I don't want to install a bunch of redundant apps. My GNOME apps are just fine. I understand that some managers and apps will be inevitable, but I would like to minimize the footprint that KDE will impose.  From this: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) , I see I have three options. I'm already ruling out the first the first option, as it contains a lot of redundant packages. 
So which one should I use, kde or kde-core?

the lag is probably because of your video card.
disabling blur and desktop effects may help.

---

### Post by zer010 on 2010-11-12
I'll take your suggestions into consideration, but I think I'll stick with less bloated DEs. It's actually unfortunate that KDE assumes that the machine will run it's effects smoothly.  Again, I thank you for your great advice! :)

---

### Post by mister_playboy on 2010-11-12
> **zer010 said:**
> I'll take your suggestions into consideration, but I think I'll stick with less bloated DEs. It's actually unfortunate that KDE assumes that the machine will run it's effects smoothly.  Again, I thank you for your great advice! :)

If you had installed and were using KWin, then I understand your complaint.  Compiz works great for me, but KWin performance is very poor.  It is possible to use Compiz (instead of KWin) with KDE.

---

### Post by zer010 on 2010-11-12
Actually, I was running Compiz, but I probably should have undone some of KDE's desktop effects like transparency and fades and such.   I'm not too worried about it now though.

---

