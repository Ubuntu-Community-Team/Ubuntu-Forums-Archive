---
title: "Yet Another Slow Wifi Question (YASWQ!), Asus ROG Zephyrus G GU502, Realtek rtl8821ce"
date: 2020-03-15
forum: Networking &amp; Wireless
---

### Post by jchwenger on 2020-03-15
**UPDATE:**
After installing Ubuntu 18.04, I had zero wifi on my machine. In the end, the following steps worked:
- Tethering from my mobile, I could install and compile the driver rtl8821ce (see links below); that gave me wifi but it remained very patchy.
- Finally, I changed the antenna using [this]("https://askubuntu.com/a/1148065").
- I have seen advice on disabling the power saving mode [here]("https://askubuntu.com/a/1077559") and used that, but I think the two above steps are what solved it for me.


Hi,

I am still relatively new to Linux, with some experience for 1-2 years with Mint, now trying out Ubuntu mostly for GPU/Deep Learning support. Just bought the Asus ROG Zephyrus G GU502DU_GA502DU and am glad that I can run some deep learning libraries on it without too much trouble (my love for Linux is growing as well). I am still struggling a bit with my wifi connection and the suspend thing (a topic for another thread). I'd be very grateful for some advice or pointers, as I'm getting a download speed of a few  kb/s only,  patchily, and need to be close to my router for it to work at all. 

I've already done some research: 

[LIST]
[*]pastebin wifi script available [here]("https://paste.ubuntu.com/p/6v2gkVStKg/"). 
[*]At first I did not have any wifi, but got it to work somehow after I cloned & compiled the independent driver repo [rtl8821ce]("https://github.com/tomaspinho/rtl8821ce") with advice found [here]("https://askubuntu.com/a/1071334") (and [here]("https://ubuntuforums.org/showthread.php?t=2420199"), talking about the same model). 
[*]I fiddled with antennas after reading [this]("https://askubuntu.com/a/1148065"), choosing the second one, thinking it would bring significant improvement, but unsure now it really does. 
[*]nmcli gives me something like this: 
[/LIST]
[INDENT]```
N-USE  SSID         MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       BTHub6-82KP  Infra  1     195 Mbit/s  55      &#9602;&#9604;__  WPA2     
```
[/INDENT]
 
[LIST]
[*]a script found [here]("https://askubuntu.com/a/269821") gives me this: 
[/LIST]
[INDENT]```
Retrieving speedtest.net configuration...
Testing from BT (86.186.14.240)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Structured Communications (London) [4.19 km]: 24.482 ms
Testing download speed................................................................................
Download: 16.40 Mbit/s
Testing upload speed......................................................................................................
Upload: 4.42 Mbit/s
```
[/INDENT]
[INDENT](as mentioned the wifi feels quite slow compared to my other computer/Windows)[/INDENT]

[LIST]
[*]  the answer on [this page]("https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520") gives me GB. Haven't dug so far into WPA etc for my router, as my Lenovo x240 Mint (& windows partition on that machine) work both fine. 
[*]I'm seeing more elaborate option tweaking like [here]("https://ubuntuforums.org/showthread.php?t=2392876"), but that doesn't seem to be the same driver, so unsure what to do. 
[/LIST]

I'd be grateful for any tips on what to do next, as I have a hard time knowing which would be the best course of action (buying a dongle, as mentioned [here]("https://ubuntuforums.org/showthread.php?t=2397914")?) 

Many thanks in advance!
Jeremie

---

### Post by jeremy31 on 2020-03-15
See the wireless script link in my signature and post results

---

### Post by jchwenger on 2020-03-15
Hi,
Thanks so much for the quick response,  I had pasted the result [here]("https://paste.ubuntu.com/p/6v2gkVStKg/")!

Although I fear it might be a waste of your time. After many hours trying things I was quite dispirited, and tried antenna option just as I was writing my post. So far it *seems* to be working. I will update my post if this remains stable, so maybe it can act as a summary for other people.

---

### Post by karlo975 on 2020-04-29
I'd like to know how well Ubuntu works on Asus GU502. Have you everything working well now?

---

