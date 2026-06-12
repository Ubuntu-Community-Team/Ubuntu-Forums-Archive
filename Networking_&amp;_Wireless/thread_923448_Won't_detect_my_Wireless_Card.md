---
title: "Won't detect my Wireless Card"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Bo.. on 2008-09-18
I have a Netgear WG511 54 Mbps Wireless PC Card installed into my laptop, and Xubuntu isn't even detecting it is there.

I'm currently on XP using my Wireless.

I don't think my wireless router modem is the problem, seeing my card isn't even responding to Xubuntu (wireless light isn't turning on, etc)

p.s. Just in case, my wireless router modem is a linksys WAG200G

---

### Post by rlzyoner on 2008-09-18
Have you tried using ndiswrapper to load and use the windows drivers for the wireless card

---

### Post by Bo.. on 2008-09-18
Is there a way to do that without resorting to using Ethernet connection?
(Might sound stupid, but i have to ask it)

---

### Post by rlzyoner on 2008-09-18
Well the handiest way I think is to download ndiswrapper using an ethernet connection.
Once you install that, you can install the windows drivers with the following command

sudo ndiswrapper -i ~/path/to/drivers/drivername.inf

---

### Post by Bo.. on 2008-09-18
Alright. I'll try that later on today (seeing it's 2:41am over here now) 
:P

---

### Post by Ayuthia on 2008-09-18
If you are using Hardy, ndiswrapper is also on the install CD.  To load the CD:
```
sudo apt-cdrom add
```Load the CD when prompted, then do the following:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```
That will update the repository list to have the CD info and then it will install ndiswrapper.

---

### Post by Bo.. on 2008-09-19
I have Hardy, but i installed it using Wubu + downloaded ISO file
Will i still be able to use that command?

---

### Post by Ayuthia on 2008-09-19
I am not for sure.  I am thinking that the downloaded .iso file should contain the packages, but I could be wrong.  I thought that wubi was not that big of an application so the .iso should be the Ubuntu .iso.  If you have that, you will have to make the CD and then you should be able to install the package.

---

