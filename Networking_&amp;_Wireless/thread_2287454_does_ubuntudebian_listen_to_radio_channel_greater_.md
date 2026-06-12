---
title: "does ubuntu/debian listen to radio channel greater than 9"
date: 2015-07-19
forum: Networking &amp; Wireless
---

### Post by Peter_Baaij on 2015-07-19
I have a modem with wich i can connect to a network, wired and wireless. The modem WLAN radio channel was set on automatic. The modem has up to 13 channels. On  most channels i found other wifi sources being active, or other activities causing noise.  The automatic configuration didn't cope with that - it keeps setting on channel 1 - so, i made it send on channel 13. From this point i couldn't wireless connect with my debian anymore. I am using wicd; the interface didn't show channel 13, but channel 0 and (therefor) kept idle. If i change the mode settings to radio channel 1-9, the connection works, above 9 not. 
I didn' check it yet, but i have the idea that debian/ubuntu can't cope with radio channels greater than 9 ? If i deinstall wicd and install network-manager i have the same problem.
Is this a bug?

---

### Post by kerry_s on 2015-07-19
certain channels are blocked in certain states/countries, modems are made to use all over the world so some would have extra channels for other places.

---

### Post by Peter_Baaij on 2015-07-19
The strange thing is, that on other wireless devices like a windows and a fedora there is no problem, so this is not a blocking matter.

---

### Post by jeremy31 on 2015-07-19
Check ```
iw reg get; iwlist chan
```

---

### Post by Peter_Baaij on 2015-07-19
Okay, here it comes [indeed up to channel 11, why no 12 and 13 - go have a look in the modem settings...]

$ sudo iw reg get
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

$ iwlist chan
eth1      11 channels in total; available frequencies :
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
          Current Channel:0

---

### Post by Peter_Baaij on 2015-07-19
So now i know the system listens to channels 1 up to 11. So, i can't use the channel 13 to transmit on my modem - while yhis channel has the least interference. My modem help tells abou ch 12/13:
"Please note that some WLAN devices (like notebooks, for example) may not  be able to use the channels 12 and 13 due to erroneous configurations.  Establishing a WLAN connection to the FRITZ!Box via one of these  channels will not be possible in such a case."
Can someone tell me what is misconfigures? And how to make it right?

---

### Post by jeremy31 on 2015-07-19
What country do you live in?

---

### Post by Peter_Baaij on 2015-07-19
Netherlands [NL]

---

### Post by jeremy31 on 2015-07-19
```
sudo iw reg set NL
```
```
sudo gedit /etc/default/crda
```
And look at the last line to see if it reads ```
REGDOMAIN=NL
```
If it doesn't, change it, save and reboot.  Hopefully iwlist chan will show channels 12 and 13 after the reboot

---

### Post by Peter_Baaij on 2015-07-19
Jeremy, thank you for your help so far. I did the "iw reg set NL" and the REGDOMAIN in /etc/default/crda was empty and i made it NL. After the reboot i changed transmitting channel on the modem to ch13. Wifi broke, but didn't reconnect on the debian. I started up a Fedora and it got connected easily wireless on ch13. On the Fedora  i connected again to the modem and changed the channel back to ch 11. A few sec later the Debian could reconnected. Hmmm? Any new sugestion would be very welcome. Here it's 02h00, and i have to work at nine. Forgive me, i will visit the forum again tomorrow. Again, thank you very much for your efforts sofar ;-) By the way "iwlist chan" only showed 11 chanels

---

### Post by Peter_Baaij on 2015-07-19
By the way, "iwlist chan" again only showed 11 chanels.

---

### Post by jeremy31 on 2015-07-19
Is your wifi card made by Broadcom?  Post the result of ```
lspci -nnk | grep -iA2 net
```

---

