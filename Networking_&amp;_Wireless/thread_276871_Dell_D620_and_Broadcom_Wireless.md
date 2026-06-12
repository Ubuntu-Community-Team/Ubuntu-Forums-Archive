---
title: "Dell D620 and Broadcom Wireless"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by sean on 2006-10-13
Hi,

I have a brand new Dell D620 ( Core Duo ) with Broadcom 4310 chipset.  I am able to get ndiswrapper to work.  However, I cannot for the life of me get NetworkManager to work with it.  It clearly has the driver loaded as I can scan from NetworkManager.  It just never connects if I select one.

Has anyone had success with Ndiswrapper, NetworkManager, and Broadcom?

Sean

---

### Post by Deathmoon on 2006-10-29
I have the same issue...

I upgraded from dapper that's been working for a few weeks now.  The upgrade went well, however my wireless did not work.  I tried everything that I knew (not much 'cause I'm a newb)...

So, I formatted and started over with Edgy and still nothing...

In network manager it sees the wireless device but it will not connect.  Therefore I install the OEM drivers via WINE and utilize the ndiswrapper, reboot, and still no dice.

I'm going to have to go back to dapper until I get this resolved.  :evil:

---

### Post by jimmyk on 2006-10-29
I think there is a conflict with the bcm43xx driver that comes with Dapper and Edgy, try:

```

sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```

---

### Post by Deathmoon on 2006-10-29
:D 

After trying:
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

it worked!  thanks!

---

### Post by Deathmoon on 2006-10-29
I was too quick to post last time...

although the commands above work; after you reboot you have to do them again.

After that I have to go into Network Settings and inactivate the wlan and then activate it again before it works.

How do I get this to happen during the boot process?

---

### Post by paul5082 on 2006-10-29
If you do this:

Run  "echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist" (without the quotes)
	to add bcm43xx to the blacklist to avoid starting on boot.

It will put the system driver on the blacklist and won't load, and will let your "wrapped" driver to load on boot.

Also, read this page - could be very helpful!

I found this useful link:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by Deathmoon on 2006-10-29
thank you paul5082!!!
:D 
the script resolved the problem!  I just rebooted twice and my wlan was active both times.  thank you  :D

---

