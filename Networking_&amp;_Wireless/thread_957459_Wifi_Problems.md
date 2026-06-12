---
title: "Wifi Problems"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by donaldshelton on 2008-10-24
--------------------------------------------------------------------------------

Thanks mainly to the users of this site, I was able to set up and use my wireless adapter.

Now, however, the computer doesn't recognize the adapter. I am currently plugged into the ethernet card.

I have an Atheros wireless card. It shows up on the device manager.

What can I do to get this back up and running? What info do people need in order to help me?

Thanks again for everyone's help

Don:guitar:

---

### Post by donaldshelton on 2008-10-24
[SIZE="5"]I hate to complain, especially since I received such good and kind advice in recent days, but.....

I see that this post has had 11 views, but I haven't yet received any help to resolve the issue.

I posted the same issue (wifi difficulties) last night, and got the same results.

If anyone can help me, I'd appreciate it.  I do make it a practice to send thanks to those who do!!

D[/SIZE]

---

### Post by analog_G on 2008-10-24
These are the things I would do.

Check to see if the correct module has been loaded
```
$ lsmod | grep 'ath_pci'
```

if not then
```
$ sudo modprobe ath_pci
```

see if there is an interface listed in ifconfig
```
$ ifconfig
```
look for ath0

see if the wireless interface is associated with an access point.
```
$ iwconfig
```

search for access points in range
```
$ sudo iwlist ath0 scan
```

use iwconfig to connect to your desired access point
for instructions
```
$ man iwconfig
```

I apologize for the simple answer, but maybe this will inspire more experienced users to offer some advice.

---

### Post by linux4me on 2008-10-24
> **donaldshelton said:**
> I hate to complain, especially since I received such good and kind advice in recent days, but.....

I see that this post has had 11 views, but I haven't yet received any help to resolve the issue.

Maybe you were being shunned because there's an [Atheros tutorial]("http://ubuntuforums.org/showpost.php?p=4999962&postcount=1")? You might need to adjust the procedure a bit if you have a different version Atheros card/chip.

---

### Post by donaldshelton on 2008-10-24
The strange thing is I was able to connect and use the internet, now all of a sudden it doesn't even recognize that there is an ath0

---

### Post by Frenske on 2008-10-24
> **donaldshelton said:**
> The strange thing is I was able to connect and use the internet, now all of a sudden it doesn't even recognize that there is an ath0

Have you plugged in anything else? I had problems with a dodgy usb card reader. When the card reader was plugged Ubuntu did not see the usb wireless adapter.

---

### Post by linux4me on 2008-10-24
> **donaldshelton said:**
> The strange thing is I was able to connect and use the internet, now all of a sudden it doesn't even recognize that there is an ath0

I had the same problem on a new install of Hardy on a Toshiba laptop. Once I followed the tutorial to install madwifi and set the manual network configuration to "roaming" mode I was able to connect to available networks.

---

### Post by donaldshelton on 2008-10-24
I tried all of the suggestions.

Ath0 doesn't appear on the list of devices.

I copied and pasted the codes, but nothing worked.

Help!!!!!:lolflag:

---

### Post by linux4me on 2008-10-25
I'd suggest starting by posting information about your system; i.e., make, model, etc. for your computer, the version of Ubuntu you're running, and the results of:
```
ifconfig
```

Also, tell us what's shown in System->Administration->Hardware Drivers and whether the driver for your wireless card--if any is listed there--shows "enabled" and "in use."

That info will make it easier for people to help you out.

---

### Post by donaldshelton on 2008-10-25
> **linux4me said:**
> I'd suggest starting by posting information about your system; i.e., make, model, etc. for your computer, the version of Ubuntu you're running, and the results of:
```
ifconfig
```

Also, tell us what's shown in System->Administration->Hardware Drivers and whether the driver for your wireless card--if any is listed there--shows "enabled" and "in use."

That info will make it easier for people to help you out.
Acer Extensa 5620Z with 2gig ram
Ubuntu 8.10 and Kubuntu 8.04

eth0      Link encap:Ethernet  HWaddr 00:1d:72:14:2c:06
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe14:2c06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:414321 (404.6 KB)  TX bytes:128120 (125.1 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Notice no mention of Ath0

Atheros Wireless shows up as AR242x 802.11 abg Wireless

213 Gig hard drive split evenly between Ubuntu 8.10 and Kubuntu 8.04

---

### Post by melojo on 2008-10-25
[http://ubuntuforums.org/showthread.php?t=956417](http://ubuntuforums.org/showthread.php?t=956417)

I pointed someone to a thread in this post and it seems they got it working

---

### Post by donaldshelton on 2008-10-25
Attached is the terminal text as I attempted to follow the directions.

Everything was great until I typed MAKE

Don

---

### Post by melojo on 2008-10-26
There were several links did you goto the correct one.  You had to read through the post and find out what worked for others.

---

