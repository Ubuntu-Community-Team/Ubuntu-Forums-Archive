---
title: "How do I setup wireless internet?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Lupy on 2009-01-10
I have just installed Ubuntu 8.10 on my Hewlett-Packard G60-125NR laptop, and everything works great, I love it! Except for one, crucial, thing: I can't connect to the internet. I have an Atheros AR5007 802.11b/g Wifi adapter. I tried following the directions in "Help" but I do not see a "Hidden Network" button :confused: ; please help me.

---

### Post by gettinoriginal on 2009-01-11
I do not use wireless, but may I suggest this thread ??  :P

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by HunterThomson on 2009-01-11
Um... you should set up a Open AP to test first.... 

You probably need to install the MadWiFi drivers for you athros WIFI card.

---

### Post by hotweiss on 2009-01-11
> **HunterThomson said:**
> Um... you should set up a Open AP to test first.... 

You probably need to install the MadWiFi drivers for you athros WIFI card.

Those Atheros drivers should be on the Live CD already. Like HunterThomson said, try with an open network first.

This review mentions of no wireless problems:

[http://www.linuxjournal.com/content/studiodave-does-hardware-review-and-meets-ubuntu-810](http://www.linuxjournal.com/content/studiodave-does-hardware-review-and-meets-ubuntu-810)

---

### Post by nothingspecial on 2009-01-11
In your menus system > administration > hardware drivers
Disable the atheros driver in there. Then accessories > terminal and copy and paste


```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Then


```
sudo modprobe ath5k
```

to load the driver.

Then to make the driver load every time you boot```



gksudo gedit /etc/modules
```

add this to the bottom of the file



```
ath5k
```

save
close
reboot

---

### Post by ugm6hr on 2009-01-11
Agree - as per nothingspecial

Here is the "official" explanation why your wireless drivers are not included as default: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

---

### Post by ugm6hr on 2009-01-11
Agree - as per nothingspecial

Here is the "official" explanation why your wireless drivers are not included as default: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

---

### Post by Lupy on 2009-01-15
I tried doing what nothing special said, and this is what happened:

```
drew@drew-laptop:~$ sudo apt-get install linux-backports-modules-intrepid-generic
[sudo] password for drew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid-generic

```

---

### Post by drs305 on 2009-01-15
I found it listed in synaptic with the normal repositories enabled. Of course, if you aren't getting wireless and can't connect to the interenet with that machine...

The release notes say it is on the Intrepid install cd. If you installed Intpreid with an Intrepid CD, open System, Administration, Software Sources or Synaptic. Settings, Repositories, Third Party Software. Make sure the CD-ROM with which you installed Intrepid is checked.  

If you didn't install Intrepid with an Intrepid cd but have one available, you can add that cd to your repositories.

Here is a link on how to add a cd to the repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by ugm6hr on 2009-01-15
The package is also here:
[http://packages.ubuntu.com/intrepid-updates/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid-updates/linux-backports-modules-intrepid-generic)

Select the correct version (i386 or amd64) near the bottom; download to your "Home" directory; install with:
```
sudo dpkg -i linux-backports-modules-intrepid-generic <press Tab key here to complete name>
sudo apt-get install -f
```

---

