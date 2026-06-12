---
title: "Wont detect wireless conncection"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by ciph3rzer0 on 2008-03-18
I installed the windows driver for my wireless card, and if I use ndiswrapper -l, it says the driver installed.  But in the network config thing on the top bar, it doesn't show any available networks.  I don't know what else to do, everything seems to be correct.

---

### Post by wolfwood707 on 2008-03-18
I think we're having the same issue, heh.

---

### Post by ciph3rzer0 on 2008-03-18
if i type iwconfig, it says there are no wireless extensions.  for both eth0 and lo.

---

### Post by Astura on 2008-03-18
> 
astral@velio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



..Yeah, I get that too

---

### Post by Captain M on 2008-03-18
What kind of cards are you using? Are you sure that you have to use ndiswrapper? What kind of encryption do you have (wep, wpa, etc.)? Is your ip static or dhcp?

---

### Post by wolfwood707 on 2008-03-18
You can see what I've done so far in the thread "noob needs help". Thanks.

---

### Post by ciph3rzer0 on 2008-03-18
my card is rtl8187B.  I don't think it recognises the card.  the networks encryption is wep.  But I think the problem is with it recognising the card.

---

### Post by Captain M on 2008-03-18
So if you go into network connections, does it show anything for a wireless connection?

---

### Post by wolfwood707 on 2008-03-18
Not for me, just Wired Connection and Modem Connection.

---

### Post by ciph3rzer0 on 2008-03-18
yep, same

---

### Post by wolfwood707 on 2008-03-18
I'm going to try this:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

### Post by ciph3rzer0 on 2008-03-19
I'm actually pretty sure now that it's not working because I'm using the 64 bit version of ubuntu.

---

### Post by Tomatz on 2008-03-19
Found a driver for you apparently the Linux drivers for the RTL8187 chipset don't include the B model. It's functionally compatible, just not recognized by the driver.

The link below contains the rtl8187B driver (source):

[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

The readme in that link should provide all the information for you to compile the driver and get your card working. :)

---

