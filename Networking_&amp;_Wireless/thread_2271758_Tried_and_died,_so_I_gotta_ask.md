---
title: "Tried and died, so I gotta ask"
date: 2015-04-01
forum: Networking &amp; Wireless
---

### Post by delamite on 2015-04-01
I picked up a Dell Inspiron 6400 needed for tuning my HD in the garage.  Runs awesome with Linux, needless to say wireless a connection is needed for garage use. 

Now the problem, I have done lots of reading here and other places but I cannot get the wireless to run.  The ethernet is fine. 

Linux puppy picked up the wireless drivers when I placed a Win-xp disc in the dvd drive.  I remember seeing 3comm 3c59x file being installed and wireless works fine.  I cannot find this file on the win-xp disc.  

Ubuntu and Robolinux says the wireless card is a BCM 4311 rev-1, but loading the drivers have crashed the system or do nothing at all.  I have tried configuring the wireless also but I feel it is still a driver issue not allowing connection. And I am highly confused with the info needed for wireless connection configuration, mac, ssid, bssid, etc.  Have tried plugging these values in the best I could understand, but if puppy picked it up I still believe it is a driver problem. 

The point of all this work is- I need to run a windows tuning program for my HD, the only possible windows license I have to run is the xp-pro coa that came with the laptop.  Figured I could run it in vm either in ubuntu or Robolinux.  It will only be for tuning so it will seldomly be used.

---

### Post by Bucky Ball on 2015-04-01
Are you attempting to install the wireless drivers while online with a cable? That card should run out-of-the-box without issue. As you have posted in ***Networking***, let's forget about Windows (and Win drivers) and VMs for the moment. 

Plug an ethernet cable into the laptop, boot Ubuntu, get online, do an update, check 'Additional Drivers'. Anything there that mentions B43 or STA? If not, open a terminal and run:

```
sudo lshw -C network
```

... and post the output back here, please.

PS: We support Ubuntu and its official flavours here. We can't throw a lot of light on Robolinux or Puppy in the main support areas, so best to stick with getting Ubuntu working for support here. ;)

---

### Post by tgalati4 on 2015-04-01
What specific tuning are you performing?  Many hard disk parameters can be changed with *hdparm*.

---

### Post by jeremy31 on 2015-04-01
> **tgalati4 said:**
> What specific tuning are you performing?  Many hard disk parameters can be changed with *hdparm*.

Sounds like motor vehicle control module tuning and in this case HD= heavy duty or Harley Davidson

---

### Post by delamite on 2015-04-01
oh, 
it is the thunder-max tuning software for my Harley.

---

### Post by delamite on 2015-04-01
ok, 
some pics to post. latest version of ubuntu x64

---

### Post by chili555 on 2015-04-01
Please get a temporary internet connection by ethernet or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
```If it complains that it's not installed, that's fine; just continue:```
sudo apt-get install firmware-b43-installer
```Detach the temporary connection, reboot and your wireless should be working.

---

### Post by delamite on 2015-04-01
VIOLA ...!!!! you guys are so awesome...... many thanks.  This old laptop runs really, really well with Ubuntu.  An Xfce desktop would be even better but hey, this works.   Distro's and the community's behind them are so great.  I am learning (slowly) and hope to be  helpful to newbs like myself one day.   Now I am going to start tackling the other half of my problem..........running a windows program.  I know there are several ways to approach this issue.

---

### Post by QIII on 2015-04-01
Hello!

I'd recommend a Windows virtual machine.

I really doubt you'll find TMax Tuner or Smartlink in the Wine database.

Since XP is no longer supported, it might be worthwhile to buy a Win 7 consumer disk (not an OEM disk as that may be problematic in a VM).  That way you wouldn't risk compromising your Windows if you go on the web to get a basemap.

I imagine you think your bike is worth being sure.

---

### Post by delamite on 2015-04-01
ok, 

before closing the thread I would like to add that I do donate to community's I use.  I think I will make it a practice that every time I get tech help a small donation will be made. 
Why not,  when I think of all the money I have spent on bloatware over the years. 

Guess we can close the thread now. Thanks again

---

### Post by chili555 on 2015-04-01
> **delamite said:**
> ok, 

before closing the thread I would like to add that I do donate to community's I use.  I think I will make it a practice that every time I get tech help a small donation will be made. 
Why not,  when I think of all the money I have spent on bloatware over the years. 

Guess we can close the thread now. Thanks again
Please use Thread Tools at the top to mark Solved.

Glad it's working.

---

