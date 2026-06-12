---
title: "Connecting to Wifi signals from the terminal"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by S15_88 on 2007-07-31
Hey i've got a quick question regarding connecting to wifi signals through the terminal.  when i do iwlist scan i get a bunch of signals, two of which have the SAME NAME, as in ESSID.  Using  ~$ sudo iwconfig wlan0 essid "linksys" THEN ~$ sudo dhclient wlan0
how would i distinguish between the twoi signals?!?! is there another parameter i can add in order to specify which signal i wish to connect to.I've quoted the two signals below with all their info, if anyone's got any answers that'd be great!  

Thanks, Alain

> 
Cell 02 - Address: 00:18:F8:5E:8E:F7
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


> 
Cell 08 - Address: 00:06:25:76:52:ED
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


---

### Post by bash4fun on 2007-08-01
it looks like that there are
two wireless networks with
the same name
but one of them seems to be encrypted
and they are also using different protocols.
so which one do you want to connect to?

if you are trying to connect to the encrypted one
try entering "sudo iwconfig wlan0 essid "linksys" key s:your ASCII key

---

### Post by S15_88 on 2007-08-01
i want the one with no encryption,  can i specify that by putting key:off?

---

### Post by bash4fun on 2007-08-08
i'll take a look as soon as i'm back home again. maybe there are specific parameters for iwconfig to set the protocol used. you can also try "man iwconfig" and look for all valuable parameters fitting your cell.

---

### Post by walkerk on 2007-08-08
> **S15_88 said:**
> Hey i've got a quick question regarding connecting to wifi signals through the terminal.  when i do iwlist scan i get a bunch of signals, two of which have the SAME NAME, as in ESSID.  Using  ~$ sudo iwconfig wlan0 essid "linksys" THEN ~$ sudo dhclient wlan0
how would i distinguish between the twoi signals?!?! is there another parameter i can add in order to specify which signal i wish to connect to.I've quoted the two signals below with all their info, if anyone's got any answers that'd be great!  

Thanks, Alain

Try hard coding your Wifi card to register w/ your AP:
```

sudo iwconfig essid "linksys"
sudo iwconfig wlan0 ap 00:06:25:76:52:ED
sudo ifup wlan0

```

---

### Post by Junglizer on 2007-08-08
Just use the MAC to specify, I can't tell you what it is off the top of my head, its in the man.

---

### Post by walkerk on 2007-08-09
> **Junglizer said:**
> Just use the MAC to specify, I can't tell you what it is off the top of my head, its in the man.

see the previous post.

iwconfig wlan0 ap xx:xx:xx:xx (is the routers mac)

---

