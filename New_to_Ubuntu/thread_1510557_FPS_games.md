---
title: "FPS games?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by adobrakic on 2010-06-15
What are some good FPS (multiplayer preferred) games? I have Assault Cube, but am now looking for some more updated games. I was looking at Smokin' Guns, but I'm not sure how to install it.

Before anyone asks:

```
ado@ado-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1)
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
ado@ado-laptop:~$ 

```


```
ado@ado-laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
11835 frames in 5.0 seconds
11978 frames in 5.0 seconds
11965 frames in 5.0 seconds
11887 frames in 5.0 seconds
ado@ado-laptop:~$
```

---

### Post by BastardNamban on 2010-06-15
Do you have Open Arena? I quite recommend it- it's a great time waster. It's in the repositories, check out synaptic.

---

### Post by adobrakic on 2010-06-15
Thanks, downloading now. If I'm not back for a while, it's good. :p

---

### Post by ks07 on 2010-06-15
It's a bit arcade-y, but I love sauerbraten (also in the repos, not sure if they have the latest version though). It's built from the new version of the engine used to make assault cube, cube 2 (:p) , so it should feel quite familiar.

Another game I've tried is Tremulous. Tbh, I hated it. :lolflag: However, you might like it, and I have to say the idea behind it is very interesting. Similar in a way to Aliens V Predator.

---

### Post by adobrakic on 2010-06-15
I'm looking at Sauerbraten right now. Is it worth figuring out how to install the game manually, if the repos don't have the latest version? 

I pretty much like any FPS game, really. I play COD: MW2 when I get on Windows 7, and still sometimes put on Halo: CE when I get bored. Third-person shooters make me want to vomit.

---

### Post by ks07 on 2010-06-15
> **adobrakic said:**
> I'm looking at Sauerbraten right now. Is it worth figuring out how to install the game manually, if the repos don't have the latest version? 

I pretty much like any FPS game, really. I play COD: MW2 when I get on Windows 7, and still sometimes put on Halo: CE when I get bored. Third-person shooters make me want to vomit.
Just had a look at the repo version, it seems to be up-to-date. If it's not, it's a good idea to update because you can only play with people who have the same version. It's not too hard if you do want to do it manually though, iirc.

---

### Post by pete1983 on 2010-06-15
Check out play-deb.net there is a whole bunch of games on there site
[COLOR="Red"]http://www.playdeb.net/welcome/[/COLOR]

[COLOR="DarkOliveGreen"]To install go to System-Administration-Software Sources, Third-Party Software tab, Add

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games[/COLOR]

[COLOR="Purple"]Then add the repository GPG key, open a terminal window and type

wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -[/COLOR]

After you install the client you just click a game that looks good and let it install thats it. Good luck and have fun.

---

### Post by waynefoutz on 2010-06-15
Urban Terror is the best FPS game out there, in my opinion. Just download it, extract it, and launch the ioUrbanTerror.i386 file if you are running 32 bit, ioUrbanTerror.x86_64 file if you are running 64 bit. There's also a Windows .exe file in there if you have WINE installed or want to run it on a windows machine. 

[http://www.urbanterror.info/news/home/]("http://www.urbanterror.info/news/home/")

---

### Post by waynefoutz on 2010-06-15
> **BastardNamban said:**
> Do you have Open Arena? I quite recommend it- it's a great time waster. It's in the repositories, check out synaptic.

Open Arena used to be a great game, but these days I can only find one or two servers and they are populated with nothing but bots.

---

### Post by Bölvaður on 2010-06-15
**Urban terror** is great, the community isnt dead and the gameplay is good. The graphics is just what is needed and nothing more.

**Warsow** has more of a limited community but strong one imo. It's played on clanbase and actually a mate of mine that is a cb admin was doing something about warsow the other day. It looks good and has many interesting game modes.

**Quake Live**, need I say more?
[B]
Nexuiz[/B] looks great and I have no idea about how many ppl play it. It's just a good game that I havent been playing.
[B]
Alien Arena[/B] might be worth a look also. but to be honest I think smokin' guns is more interesting even though the graphics sucks.. but then again, I normally turn graphic off when I start playing so...w/e

---

### Post by adobrakic on 2010-06-15
Yeah, I stumbled across Urban Terror using Pete's suggestion, and I love it. Definitely going to be looking out for this one more. Thanks guys :)

I recorded some demos in UT, and noticed the videos are in .dm_68 format, can I convert these to .avi?

---

### Post by adobrakic on 2010-06-16
bump please for the converting question.

---

### Post by joshmuffin on 2010-06-16
Urban terror is great its somewhat like counter strike. And yeah you cant convert them though I'm not sure what to or how, I'll get back to you when i find it

---

### Post by joshmuffin on 2010-06-16
Also nexus is well made and fun if your spacey type shooters I personally much prefer a machine gun and its sounds.

---

### Post by bigseb on 2010-06-16
> **adobrakic said:**
>  Third-person shooters make me want to vomit.

I hate that too.

OT: biggest drawback imo  about Linux shooters is they don't have a decent  single player campaign. Only multiplayer. However some are real good quality eg: Urban Terror, Tremulous, etc.

---

### Post by waynefoutz on 2010-06-16
> **bigseb said:**
> I hate that too.

OT: biggest drawback imo  about Linux shooters is they don't have a decent  single player campaign. Only multiplayer. However some are real good quality eg: Urban Terror, Tremulous, etc.

Sauerbraten has a decent single player mode. There's not much of a plot or story line to it though.

---

### Post by Bölvaður on 2010-06-16
> **adobrakic said:**
> 
I recorded some demos in UT, and noticed the videos are in .dm_68 format, can I convert these to .avi?

dm files arent video files
you should grab what is on the screen with recordmydesktop

---

