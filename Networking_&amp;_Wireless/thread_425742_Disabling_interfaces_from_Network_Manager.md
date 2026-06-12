---
title: "Disabling interfaces from Network Manager"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by golfing22 on 2007-04-27
So far I love NetworkManager except for one thing.  I have two wifi cards in my laptop, one I use for connecting to Access Points and the other I use for kismet.  The problem is that after a minute kismet locks up because NetworkManager tries to use the card.  I was wondering if there was a way to disabling NetworkManager from using that interface (rausb0)? 

Thanks for the help,

-golfing22

---

### Post by joshbuss on 2007-06-24
I am having a similar issue, what is happening is it looks like Network-manager is taking the cards out of monitor mode and reconnecting to networks. I am looking for a fix or way to solve this issue. Any help is greatly apreciated

Thx,  DaBuss

---

### Post by kevdog on 2007-06-24
Why dont you just comment out the rausb settings in the /etc/network/interfaces file?? As a root user (gksu gedit /etc/network/interfaces) Add a # sign in front of the lines you do not want, then save the file.  Restart the network with
sudo /etc/init.d/networking restart

Hopefully that works.

---

### Post by joshbuss on 2007-06-25
I still want Network-Manager to be able too use and configure this device. However I also want to tell network manager to not try to configure it when i'm trying to use monitor mode. from what I know of linux, won't what you told me to do just have the card shutoff on bootup?

---

### Post by joshbuss on 2007-06-25
Ok, so i was playing around abit with this, and the way that I have to do it is disable Roaming for my wireless adapter in network settings, and enter a fake ESSID, then i can uncheck the wireless card from letting network-manager control it. I then have full manual control over what I want it to do, and to use network manager again i just check it and reenable roaming. I have saved the two configs as location setings, so it's quick, easy and painless :-)

thx for the help
peace
DaBuss

---

### Post by golfing22 on 2007-07-02
Sweet, joshbuss's fix works perfectly for me.  Now Network Manager doesn't try to control my other wifi card.

Thanks,
golfing22

---

