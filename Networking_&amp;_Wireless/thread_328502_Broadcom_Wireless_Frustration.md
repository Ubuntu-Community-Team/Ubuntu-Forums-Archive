---
title: "Broadcom Wireless Frustration"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by matt.runion on 2006-12-30
Hi,

I'm pretty new at this.  Just upgraded to Edgy.  Dell D600.  Trying to get the wireless card working.  Haven't had much success in sorting out a true-blue fix.  I attempted the ndiswrapper method, but it claims I have the incorrect driver installed.

> mrunion@ubuntu-laptop-MDR:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
mrunion@ubuntu-laptop-MDR:~$ 

mrunion@ubuntu-laptop-MDR:~$ ndiswrapper -l
Installed drivers:
bcmwl5.sys      invalid driver!
mrunion@ubuntu-laptop-MDR:~$ 

It was downhill from there.

Thanks for any help in advance.

-Matt

---

### Post by brendandonhue on 2006-12-31
It looks like you might have typed "ndiswrapper -i bcmwl5.sys" instead of "ndiswrapper -i bcmwl5.inf"

---

### Post by haiku99 on 2006-12-31
I have had good results setting up ndiswrapper in Dapper and Edgy using this howto--
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
and ising drivers I copied from my widows partition

---

### Post by lbrigman on 2006-12-31
You  can try the following HOWTO's  

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
to get it working w/o the ndiswrapper 
or
[http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092)
for a dell laptop using ndiswrapper.

---

### Post by Skidpad on 2006-12-31
Matt: as a new user myself, take this for what it's worth...

I too had a Broadcom 4309 chipset.  I did lots of reading on here, and realized that the 4306's and 4318's seemed to have a positive success rate, but info on the 4309 seemed spotty, and it was listed as "not supported" on one website I read.

One of the experienced members on here had stated that after he had attempted to install many different network adapters over the years, it was simply easier to buy a supported chipset and be done with it...after lots of reading I came to the same conclusion - life is too short! - and spent $30 on an RT2500 (ASUS WL-107G) chipset that worked out-of-the-box after I updated the drivers from the Ralink wesbite.  

Just my $.02 worth.  :)

---

### Post by matt.runion on 2006-12-31
Well, I've had a bit of success.

When I type

> sudo iwlist scan

...I can see a couple of wireless networks of homes next to me.  The only problem is that I can't see the AP that is directly above me.  It has an SSID that is not broadcast and is 128-bit WEP encryption.

I followed some advice in another post and edited my /etc/network/interface file.

It looks like this...

> auto wlan0
iface wlan0 inet dhcp
wireless-essid BHIVE
wireless-key s:26charactersofACSI

...however, I still can't connect to or "see" this AP.

I believe I will attempt to try non-encrypted temporarily, but I really don't want to broadcast my SSID, nor do I want to run without encryption.

Thanks all for the help,

Matt

---

### Post by matt.runion on 2006-12-31
OK, a bit more success, but probably need some help in deciphering...

First I found this in the ndiswrapper FAQ

> # Enable ESSID broadcast on your station. Make sure your station is listed in iwlist wlan0 scan. If the station is not listed in the scan, you can't associate with that station.
# Note that when setting the ESSID in Managed mode, the ESSID does not show up in iwconfig until the card has successfully associated with the access point! 

I find that a little strange, unless you have to broadcast temporarily to get everything set up properly, but I assume it's not required for the AP to broadcast if WEP and the SSID is set correctly.

Then I found this....

> mrunion@ubuntu-laptop-MDR:~$ iwlist wlan0 key
wlan0     2 key sizes : 40, 104bits
          4 keys available :
Error reading wireless keys (SIOCGIWENCODE): Operation not permitted
          Authentication capabilities :
                WPA
                WPA2
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0x0
          Current cipher_pairwise:0x0
          Current cipher_group:0x0

Is that telling me that 128-bit WEP isn't possible?  Do I need to switch to WPA?

Thanks,

Matt

---

### Post by haiku99 on 2006-12-31
the **s:** before the wireless key might be a problem (though I'm not sure, I did have to remove a **s-** before mine in that file, and my card is a BCM4311 FWIW)    Trying to connect w/o encryption is a good idea to try first, you can temporarily put a # at the start of the wireless key line to comment it out so you don't have to retype the whole thing later.   I got my card going w/ 64 bit WEP and a 10 digit key, have not tried anything else yet.



> **matt.runion said:**
> Well, I've had a bit of success.

When I type



...I can see a couple of wireless networks of homes next to me.  The only problem is that I can't see the AP that is directly above me.  It has an SSID that is not broadcast and is 128-bit WEP encryption.

I followed some advice in another post and edited my /etc/network/interface file.

It looks like this...



...however, I still can't connect to or "see" this AP.

I believe I will attempt to try non-encrypted temporarily, but I really don't want to broadcast my SSID, nor do I want to run without encryption.

Thanks all for the help,

Matt

---

