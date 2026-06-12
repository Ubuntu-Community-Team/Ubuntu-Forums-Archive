---
title: "My OWN Wifi network is not detected anymore"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by mbrb01 on 2008-09-09
Hello all,

I have a strange problem.
My wifi is up and ok, iwlist scan give me a full list of wifi networks around me, and with network manager i can connect to some of them (public hotsopt).

SO :
-my wifi chipset is working
-my antenna is picking up signals like Arecibo radiotelescope
-wpa_supplicant, network-manager and all that crap can work with wifi.


BUT :
my home wifi network is not detected anymore. 
iwlist scan gives me a lot of networks, but not mine since last day!
Brief check-up of my wifi router: my ssid is not hidden, wifi is activated. AND my leopard imac can detect my wifi home network.

And I ask you, what happens? why my own network is not detected anymore on the computer running ubuntu? very strange because i detect and connect to others wifi network.

Some specs : eeepc701 with built-in Atheros wifi chipset, hardy.
For the ones who knows, my router is a Freebox HD V5 (hi french guys around there!), given by Free, an internet access provider here in France.

Turn your brain up and join your intellect power with mine to resolve this sh*t!

Thank everybody!

---

### Post by Muflon on 2008-09-09
Try rebooting your router.  I know your imac is working but given that everything else looks fine, then it is worth a try.

It is also woth noting that 'iwlist scan' must be run as root (sudo) to update the list rather than just displaying the previous list.

Muflon

---

### Post by Bucky Ball on 2008-09-09
Try:

                                       sudo /etc/init.d/networking restart

---

### Post by mbrb01 on 2008-09-09
> **Muflon said:**
> Try rebooting your router.  I know your imac is working but given that everything else looks fine, then it is worth a try.

It is also woth noting that 'iwlist scan' must be run as root (sudo) to update the list rather than just displaying the previous list.

Muflon
Muflon, router already rebooted, many times...
I will try sudo iwlist scan instead of iwlist scan as simple user, but I suppose the networks are fully rediscovered after a full shut down of the computer...already rebooted many time, too!

---

### Post by mbrb01 on 2008-09-09
> **Bucky Ball said:**
> Try:

                                       sudo /etc/init.d/networking restart
Bucky, no changes after running this command, which is one of the first things I tried.

---

### Post by Muflon on 2008-09-09
The other thing I try when this happens to me is placing the laptop right next to the router when trying to connect.

Muflon

---

### Post by mbrb01 on 2008-09-09
> **Muflon said:**
> The other thing I try when this happens to me is placing the laptop right next to the router when trying to connect.

Muflon
Tried this too Muflon.
Can you confirm this : rebooting computer refresh networks as "sudo iwlist scan" does? I can't try this right now, I am at work :(

Something else : my router is implicated in this problem : my girlfriend rebooted the router because there was freeze problems with TV broadcast (the router supplies internet, TV and phone). Since THIS reboot, my wifi is not detected by Ubuntu (a fresh install of Ubuntu, on external hard drive, does detect my home wifi network).

A bit complicated huh?

---

### Post by Muflon on 2008-09-09
You are implicating your router as the root of this issue, so I would be tempted to reset the router to factory settings and then set it up again.  Obviously you should only do this if you know the correct settings for your router.

Muflon

---

### Post by mbrb01 on 2008-09-09
> **Muflon said:**
> You are implicating your router as the root of this issue, so I would be tempted to reset the router to factory settings and then set it up again.  Obviously you should only do this if you know the correct settings for your router.

Muflon
Factory settings already restored, no changes. Anyway, why THIS installation of ubuntu doesn't detect or connect to my wifi network (and only mine) and detects and connect to other wifi networks in the neighborhood?? Other OS on this computer detects and connect to my wifi, a fresh install of ubuntu on this computer detects and connects to my wifi, OSX on an other computer detects and connects to my wifi network.

---

### Post by mbrb01 on 2008-09-09
I want to say : i tried to restore a previous backup of my ubnutu install. Works fine, my wifi network is detected. So, if my problem is not solved, i restore this backup and that's fine. BUT i want to know what happens.

---

### Post by tnemeth on 2008-11-20
I just installed ubuntu 8.10 and kubuntu 8.10 along my
functionnal kubuntu 8.04.1...

Under 8.04.1, my wifi network is correctly detected and I can
log in, search the web, etc. With either 8.10 versions, my wifi
network is not even detected.

Other networks are. I could even log into a friend's network,
but the connection to my freebox wifi is impossible with 8.10.
8.04 and WXP can fully detect and connect to this network, so
the problem does not come from the router and does not come
from the chipset and hardware either.

Since I could log into another network, the problem does not
come from the driver. I suspect a network manager problem...

T.

---

### Post by tnemeth on 2008-11-20
> **mbrb01 said:**
> Hello all,

I have a strange problem.
My wifi is up and ok, iwlist scan give me a full list of wifi networks around me, and with network manager i can connect to some of them (public hotsopt).

SO :
-my wifi chipset is working
-my antenna is picking up signals like Arecibo radiotelescope
-wpa_supplicant, network-manager and all that crap can work with wifi.


BUT :
my home wifi network is not detected anymore. 
iwlist scan gives me a lot of networks, but not mine since last day!
Brief check-up of my wifi router: my ssid is not hidden, wifi is activated. AND my leopard imac can detect my wifi home network.

And I ask you, what happens? why my own network is not detected anymore on the computer running ubuntu? very strange because i detect and connect to others wifi network.

Some specs : eeepc701 with built-in Atheros wifi chipset, hardy.
For the ones who knows, my router is a Freebox HD V5 (hi french guys around there!), given by Free, an internet access provider here in France.


    Hi. I may have a hint. I just have to try and test the
    possible solution I found. Like you I have a Freebox and
    as you can see in my previous post, I can connect my
    freebox with 8.04 but not with 8.10 and 8.10 can connect
    on some other access point (liveboxes) but is unable to
    detect my own AP.

    I just booted under 8.10 and did a simple iwlist freq :
```

thomas@cixi:~$ sudo iwlist wlan0 freq
wlan0     19 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency:2.412 GHz (Channel 1)

```

    Then I booted back to my kubuntu 8.04 and did the same
    while beeing connected :
```

thomas@cixi:~$ sudo iwlist wlan0 freq
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Current Frequency=2.467 GHz (Channel 12)

```

    As one can see, there is a subtle difference between the
    two outputs. Not only 8.04 supports more frequencies, but
    the one used by my configured freebox (channel 12) is NOT
    supported under intrepid :(

    I'll try to use another channel ASAP just to see if it
    works.

T.

---

