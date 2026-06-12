---
title: "Problems w/ ubuntu wireless with broadcom"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by k9nacl on 2006-10-30
So, after finally turning to the light side I've convinced myself to try out some distros. I tried about 4 different ones and I'm convinced I like ubuntu the best. Not only for simplicity sake, but also just for general learnability and it's helped me to learn the terminal and general concepts of linux.

But, my biggest problem with all of the distros thus far is that I cannot figure out how to get a wireless going. My first real attempt and problem came on ubuntu after I got the newest ndiswrapper install (1.28) and I'm on a Broadcom BCM4318 54g Airforce One built-in network card on a 64bit AMD HP. Much to my dismay, all of the recent windows drivers are not up to 1.28 (1.23 is the highest for my network card) so none of them are installing or being recognized by my laptop. 

I install ndiswrapper and when i do iwconfig it shows that eth1 is my local network card and shows all the details, but again, when I try and activate my wireless connection (after putting all my settings in) it simply says "ok", and when i re-open it, it is deactivated and the wireless does not work.

Basically, I'm just incredibly frustrated and have spent a ton of time trying to get this to work yet I can't get going in any direction. I can get a wired connection just fine but nothing besides that and it is driving me nuts considering my entire school is wireless (printers, etc.) and I am rendered useless until I get this working.

thanks guys, sorry for the probably repetitve complaint, I just have no clue what i'm doing here.

---

### Post by k9nacl on 2006-10-31
Ok, actually, after some searching I think I'm getting there using this thread:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

My only problem is when i come to step 4) it says:

Open a terminal (dont worry) and type the following:
Code:

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o

I do that and nothing happens, but aren't I supposed to put something else for the wl_apsta.o? I know I installed the bcm43xx correctly as it did the whole process and such but now I'm stuck...

thanks.

---

### Post by k9nacl on 2006-10-31
ok, since I'm not that good at solving my own problems, I think I'll post again.

I went through the whole guide, as well as about 3 others that talked about my specific network card and still have no success. I configure all the options but still I get nothing. It says that my wireless stays active and my light is on but I still get nothing. i downloaded ndiswrapper and ran the install script which said it was installed, but for some reason it doesn't work and isn't installed.

---

### Post by nullmind on 2006-10-31
I have that same card. Basically follow that guide using the wl_apsta.o (extracting the firmware like they say) After getting the firmware installed do this:

```

apt-get install network-manager network-manager-gnome
apt-get install wpasupplicant
rmmod bcm43xx
modprobe bcm43xx
ifconfig eth1 up
iwlist scan

```

Your networks should display in the terminal. I would now press ALT+F2 to open a "Run Application" dialog and type:

```

nm-applet

```

This will start the network-manager applet (the tray icon). Click the tray icon to see what networks are available and try it out. It's important that you know what a "Keyring" is and that it's NOT the key of the network, so when it asks for you to set a keyring password you'll know what you're doing.

It sounds dumb but if the network doesn't work try doing these steps again:

```

rmmod bcm43xx
modprobe bcm43xx
ifconfig eth1 up
iwlist scan

```

Basically that helped me a lot, it helps the driver recover from all kinds of errors. I've noticed that the bcm43xx module doesn't seem to work very well on 64-bit systems, so you might consider compiling it yourself or just using ndiswrapper.

If you have any questions (or anyone else with a bcm) you can contact me at [email]nullmind@gmail.com[/email] via e-mail or Google's Jabber (Gtalk) server.

Cheers,
Kristopher Ives

---

### Post by k9nacl on 2006-10-31
well I've gone through all of those steps but stll have't gotten anything. I downloaded wifi-radar and it picks up networks and it says it has connected but I don't get an IP and it can't connect to it to get one.

when I tried the things you suggested my light turned off, and network manager doesn't do anything for me other then having the icon in the corner. If I click on the icon in the tray it simply says "no network devices have been found" but everything else detects my card and when i do a iwlist scan it says nothing can be found.

I install ndiswrapper but am not totally sure how to use it other then that I tried to get it to install my drivers and it installed the .inf file but not the .sys.

---

### Post by k9nacl on 2006-10-31
ok, when i do a ndiswrapper -l it says hardware and drivers present, and i've tried every command in that list but my light still isn't coming on yet. I can't connect to any wireless points stll and when I change my network settings it still hangs and doesn't work.

---

### Post by lyceum on 2006-10-31
I have a broadcom and I would recomend getting another card. It is too much of a hassle. I never got mine up. Broadcom needs to support Linux users better.

---

### Post by k9nacl on 2006-10-31
I managed to reformat ubuntu again properly and followed one of the guides and am getting there.. I think. My light stays on the whole time, my wireless thing stays active and is properly set and i have network manager/wifi-radar on there but when i scan with iwlist scan and use wifi-radar neither of them pick up any networks. previously, my light wouldn't stay on and it wouldn't stay connected but i could scan and pickup APs.

---

