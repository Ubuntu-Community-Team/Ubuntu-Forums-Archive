---
title: "Ubuntu Mate 16.04 wifi login problem?"
date: 2017-12-24
forum: Networking &amp; Wireless
---

### Post by ken0069 on 2017-12-24
I've done several searches online for something that would resolve this issue but found nothing to date.  Search here also didn't find anything so here goes.

Ubuntu Mate 16.04 won't login to my wifi connections?  The drivers for the RT8191 USB wireless adapter I'm using are obviously there as I can see the 3 different wireless router connections available to me but NONE of them will connect?  I can put the password in and it tries to connect but never does on any of the 3 connections that I have.  It sits there for a minute or two then the login screen appears again like the password is wrong, but it's not.  I've used that wireless adapter on other systems including Mint 17.2 and .3 along with Ubuntu 14.04 with no problems.  It also works fine with the various flavors of Windowz that I have loaded.  

FYI this seems to be a problem with anything 16.04 as I tried Lubuntu 16.04 back a couple of weeks ago and got the same results.  

So can someone tell me how to get this Ubuntu Mate 16.04 to log in to my routers?

Thanks

---

### Post by praseodym on 2017-12-24
Please check if the MAC address is allowed in your router, enough IP addresses are available, encryption mode to pure WPA2-AES (CCMP), fixed channel (1-11 in the US), bandwidth to 20 MHz instead of 20/40MHz, and network not hidden.

Additionally, please run the wireless script from the sticky thread and show the outputs here.

---

### Post by ken0069 on 2017-12-27
Sorry for the late reply but the Holidays and "real life" have somewhat interrupted my free time.  It's going to be a few days before I can get all this accomplished so just hang on and I'll get that info posted as soon as I can.  

And thanks for the Reply!

Merry Christmas and Happy New Year!!

---

### Post by ken0069 on 2017-12-31
1.  Please check if the MAC address is allowed in your router 

This wireless adapter works in Windows on this router so the MAC address can't be blocked.

2.  enough IP addresses are available

This is the only computer currently connected to that router at the moment but will accomidate up to 10 devices and I've had about 6 connected to it at one point before now so IPs are plentiful.  

3.  encryption mode to pure WPA2-AES (CCMP)

WPA2-AES (CCMP) is not shown as an option??  It's currently set to WPA-WPA2 personal

4.  fixed channel (1-11 in the US), bandwidth to 20 MHz instead of 20/40MHz, and network not hidden.

Network is NOT hidden??  Don't know how to do the rest?

pastebinit done  paste.ubuntu.com/26296514/

Anything else?  I'm sure I probably forgot something!

---

### Post by praseodym on 2018-01-01
WPA-WPA2 Personal is the network-manager setting, which is correct. Change the encryption mode in your router. Check the manual. Same for hidden network, bandwidth and fixed channel.

For this driver (r8712u) these module parameters often help:

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
Re-plug the stick.

14 channels are not correct, in the US (time zone) it must be 11 by law (?!). Please run

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
and reboot. Change "US" in that line if you are located in another country according to these country codes

[https://en.wikipedia.org/wiki/ISO_3166-1](https://en.wikipedia.org/wiki/ISO_3166-1)

---

### Post by ken0069 on 2018-01-03
Changed the encryption to AES and that WIFI connection did connect to my Franklin R850 hotspot, which is called Sprnit1 in the data.  Bad news is when I did that I LOST MY INTERNET CONNECTION to the cell tower???  Took it a half hour to come back AFTER I changed the encryption back like it was??

So I fixed it..........I broke that Ubuntu Mate 16.04 DVD into pieces then threw the pieces of the DVD in the trash!  I also DELETED that ISO image off my storage drive so I won't make this mistake again!!  Then I loaded Linux Mint 17.3 on it and I'm done!

Thanks for your help and sorry it didn't work out.

Ken

---

