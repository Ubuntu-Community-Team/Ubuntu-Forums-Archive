---
title: "iwconfig problem"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by wk1989 on 2008-02-18
I got my wireless working, now how do I connect to this network?
> 

 Cell 03 - Address: 00:19:5B:93:9B:72
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Doing
```

iwconfig eth1 essid -- "default"

```
sets the essid to off/any, but I couldn't aquire an IP through dhclient. 
Any help would be appreciated!

---

### Post by psyburn on 2008-02-18
Short answer:
First off is to get closer to the AccessPoint/Router
I've had little luck getting a ip unless the signal level is +10dBm above the Noise level

---

### Post by wk1989 on 2008-02-18
My friend was able to connect with his mac and I was able to connect under Windows. I'm using ndiswrapper so the signal strength requirement should be similar to the requirement under windows.

---

### Post by psyburn on 2008-02-18
One would assume that to be the case, but in practice another thing happens...
I call 'em as I see 'em
I got nothing else to add...

---

### Post by wk1989 on 2008-02-18
Well there's always ways to get better signal quality, my question is how I would set up the right parameters using iwconfig.

---

### Post by wk1989 on 2008-02-18
anybody?

---

### Post by kaginken on 2008-02-18
I highly advise typing man iwconfig to get complete information on everything that can be done with the iwconfig command, but here are some of the more common commands you may want to use:

        * iwconfig wlan0 enc < key >: Sets the WEP encryption key to < key >
        * iwconfig wlan0 mode managed: Sets the mode to managed
        * iwconfig essid driveon: Sets the ESSID/SSID to ‘driveon’
        * iwconfig channel 7: Sets the card to use channel 7

          Note that you can put all these commands together, as in: 

        * iwconfig wlan0 enc mode managed essid driveon channel 7

Note that iwconfig is used to set the parameters of the card, it does not bring the card ‘up’ for use. You must use the command:

    ifconfig wlan0 up 

for that.

Hope that helps!!  Rock on  :guitar:

---

