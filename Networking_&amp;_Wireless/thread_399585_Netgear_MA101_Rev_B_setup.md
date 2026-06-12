---
title: "Netgear MA101 Rev B setup"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by super.rad on 2007-04-02
I just installed ubuntu 6.10 on my girlfriends pc (trying to convert her) and she is using a netgear ma101 rev b usb wireless adaptor, i think its installed the drivers fine but im not too sure and also dont know how to configure it
The name of her wireless network is G604T_WIRELESS
The security (sorry dont know what type it is wpa/w...etc) is a 25 digit number.

```
em@em-ubuntu:~$ lsusb
Bus 002 Device 002: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter

em@em-ubuntu:~$ lshw
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:30:5a:d7
      capabilities: ethernet physical wireless
       configuration: broadcast=yes wireless=IEEE 802.11-DS

em@em-ubuntu:~$ iwconfig
wlan0     IEEE 802.11-DS  ESSID:"G604T_WIRELESS"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Could someone please tell me if 
a) the drivers are all installed
b) i have set the essid correctly, i did 
```
sudo iwconfig wlan0 essid G604T_WIRELESS
```
and finally
c) how i would enter the security for the network (25 digit number)

Thank a lot

---

### Post by super.rad on 2007-04-02
could i just use networking to put the essid and security in? i've heard this causes it to freeze when booting?

---

### Post by super.rad on 2007-04-02
i have now got it working, im writing this from ubuntu. my next problem is, even though the internet works i cant seem to update, i've gone to synaptic and clicked reload but it just times out and i've tried sudo apt-get update but it says it could not connect to.....connection timed out. any ideas how i can solve this? thanks

---

### Post by super.rad on 2007-04-04
anyone know whats going on? i cant update anything or install new programs. any help would be much appreciated

---

### Post by FrozenFOXX on 2007-04-04
See if you can ping the repositories you've got listed.  I wasn't able to update anything one day using the Portuguese repositories (they decided to block me for some reason, no idea why).  If you can't ping the repository but you can get somewhere else like Google.com then you know where the problem lies.

---

### Post by super.rad on 2007-04-04
how would i find out the address of the repositories to ping?

---

### Post by super.rad on 2007-04-05
i still need to know the answer to the above question, but also have a new one....does this card work straight away in feisty? as i'm still having the problem with not being able to update at all so considering trying feisty to see if that works but only if the wireless card will work without any hassle

---

### Post by promet on 2007-04-05
> **super.rad said:**
> i have now got it working, im writing this from ubuntu....

Hey Super.rad, I'm glad you've got your MA101 working. Could you please go into a little more detail? I'm having trouble with mine and any pointers you might have could go along way.

P

---

### Post by super.rad on 2007-04-06
i had managed to set it up but had a dns problem so couldnt download any updates, in the end i reinstalled ubuntu 6.10 and just put in the network essid, key and set it to dhcp in system>administration>networking. everything is now working perfect.

---

