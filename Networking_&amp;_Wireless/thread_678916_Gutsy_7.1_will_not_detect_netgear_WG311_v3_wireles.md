---
title: "Gutsy 7.1 will not detect netgear WG311 v3 wireless pci card"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by jplyons on 2008-01-26
Hello 

I have tried the following and get a "File not found 404" .
 wget [http://www.feeditout.com/marvell/wlandrivers.zip](http://www.feeditout.com/marvell/wlandrivers.zip)

Where can I find a file called wlandrivers.zip. This is supposed to
contain the driver needed to make Gutsy 7.10 detect a netgear WG311 v3
wireliewsws pci card.

Is there any EASY way to get my Gutsy 7.10 to detect the WG311 V3?
I know it works because I can boot under Vista and it is detected.

Thank you for any help you can offer.

Joe

see below for details.


The steps, written in response to a post.
Re: NETGEAR 54 Mbps Wireless PCI Adapter WG311 v3 l
NetGear WG311v3 (marvell chipset)

1) Install Ndiswrapper
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common

2)c Download marvell chipset Drivers (i cant find the link where i got em, so i uploaded them to my own webspace)
 wget [http://www.feeditout.com/marvell/wlandrivers.zip](http://www.feeditout.com/marvell/wlandrivers.zip)

--- I can't go further -- because of this error
-Resolving [www.yahoo.com](www.yahoo.com)... 69.147.114.210
Connecting to www.yahoo.com|69.147.114.210|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:42:32 ERROR 404: Not Found.

----------------------------------------------------------------

 Later steps I could not run.

3)Unzip them
unzip wlandrivers.zip

Load the driver (ini file) (i used the win2k xp drivers)
ndiswrapper -i /path/to/ini

lets see if it is present
ndiswrapper -l
mrv8335 : driver installed
        device (11AB:1FAA) present

Save our settings
sudo ndiswrapper -m

Start the device
sudo modprobe ndiswrapper

once the driver has been installed you can remove the unzipped files, as the needed files have been copied elsewhere
rm -rvf /path/to/folder

---

### Post by b0rka7a on 2008-01-26
It's not Gutsy 7.1, it's 7.10
That means 2007, October (7.10)... not 2007, January (7.1) (:

Ah, and about the netgear wireless card problem - sorry, I don't know (:

---

### Post by cheesepoop on 2008-01-31
I also need this, i cant seem to find it anywhere...does anybody have it?!

---

### Post by FoxOne on 2008-02-03
per request

---

### Post by VicDiez on 2008-02-17
BTW,

Is it possible to do monitor/promiscous mode with this card (v3)?

So far as I know it's possible with v1 same card. (differente firmware)

---

