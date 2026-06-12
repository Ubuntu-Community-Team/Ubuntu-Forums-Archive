---
title: "Can't connect to wireless 5G broadband"
date: 2020-02-23
forum: Networking &amp; Wireless
---

### Post by dbee on 2020-02-23
I'm running an install of 19.10 ubuntu on a new laptop. I had to install the nvidia proprietary drivers manually after install.

I can't seem to connect to the wireless 5G broadband network in my home. I can connect to the 2.5 Ghz frequency no problem.

I've dual booted with windows and windows has no problem connecting through 5G and getting the higher speeds.

I disabled the 2.5Ghz frequency on the router yesterday to see what would happen. And linux connected to 5g. But when I rebooted this morning. Linux couldn't connect to 5g or even to my mobile hotspot connection.

When i re-enabled 2.5Ghz this morning from windows and rebooted linux. I was able to connect linux to 2.5 Ghz but not to 5g.

Also - when i booted linux this morning. It prompted me for my password and login details and then just froze on a black screen. Even the pointer froze. 

I booted up into recovery mode and went on from there and it seems to be working now.
```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~$ iwconfig
eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:"VM913FC33"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: AC:22:05:CA:E1:FB   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0

```

```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~$ iwlist chan
eno1      no frequency information.

lo        no frequency information.

wlo1      32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
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
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Current Frequency=2.437 GHz (Channel 6)


```

---

### Post by TheFu on 2020-02-23
Please clarify if you mean **5G broadband** or **5.8 Ghz WiFi**.  We don't have any 5G broadband available here, only 4G.  Do they make routers with 5G wireless already?

I suspect nobody can help with 5G connections. We might be able to help with 5.8Ghz wifi, however.

OTOH, there's lots and lots of 5Ghz equipment.  5Ghz doesn't go through walls.  To get the highest wifi connection speeds requires an AP that multi-plexes 2.4Ghz and 5.8 Ghz wifi bands usually with multiple antennas and transmitters.  In general, wifi bandwidth is, at best, 50% of whatever the claimed speed on the box says and that is only under ideal situations.

Different APs have different capabilities. Same for different laptop wifi adaptors.

BTW, it would help readability if the "quote" tags above were changed to "code" tags.

There is a sticky thread in the  *networking and wireless* subforum that has an information gathering script. Get that, run it, post the link or output. Use 'code tags', please.

More about wifi stuff: [https://arstechnica.com/gadgets/2020/02/the-ars-technica-semi-scientific-guide-to-wi-fi-access-point-placement/](https://arstechnica.com/gadgets/2020/02/the-ars-technica-semi-scientific-guide-to-wi-fi-access-point-placement/)

---

### Post by coffeecat on 2020-02-23
@dbee, I've changed quote tags in your post to code tags. Please use code tags for terminal output, contents of config files, code, and where vertical formatting is achieved by the use of spaces. If you post such things in quote tags or in the main body of your text, you lose the columnar formatting, thus making the code/output nigh-impossible to read.

---

### Post by dbee on 2020-02-23
> 
Please clarify if you mean 5G broadband or 5.8 Ghz WiFi. We don't have any 5G broadband available here, only 4G. Do they make routers with 5G wireless already?


I was under the impression that it's 5G broadband. For a start it is faster and also the ssid is labelled '5g'. My (old) smartphone can't pick up the network either ...

I'm getting cable broadband in Ireland. I presume the router is 5G enabled. It's a virgin media hub 3.0.

If not - and i'm mistaken - then i guess it could be just a 5Ghz channel.

---

### Post by TheFu on 2020-02-24
Yes, it can be confusing.

Normally, 5G broadband would be from the router to the ISP.  Issues with this connection are an ISP phone call.  If the laptop has a 5G connection, it isn't to the router. The laptop would have a SIM card provided by the data provider/ISP. Does it?  Only the laptop with the SIM card will connect to the internet.

5 Ghz wifi would be from the laptop to the router.  No SIM card.  Some sort of SSID + passphrase (usually). Any laptop with wifi (5 Ghz) can connect, no SIM card/device needed.

SSID is just a name, meaningless or for marketing.  Can be anything.

Anyways, if the router is configured with a 5.8 GHz SSID and passphrase, does connecting to it with the correct credentials not work?
```
sudo iwlist scan| egrep 'SSID|wlan|Channel|Quality|Cell'
```
will show the available SSIDs on the channels. Can't hurt.  Wifi info script?

---

