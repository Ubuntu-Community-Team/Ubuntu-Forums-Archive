---
title: "Repeat &quot;authentication required for wifi network&quot; Ubuntu 14.04 LTS"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by muhsin2 on 2015-05-06
I&#8217;m new to Ubuntu and today I&#8217;ve decided to install Ubuntu 14.04 LTS onto my PC. But I&#8217;m having trouble connecting to the internet via my home network. I&#8217;ve managed to get my Netgear wireless adaptor (model: N-300 WNA3100) to work on Ubuntu (thanks to: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)) but when I try to connect to my home wifi, I repeatedly get &#8220;Authentication required by Wi-Fi network&#8221; and it asks for the password again and again without connecting. I thought it might be my wireless adaptor, but I can connect fine via my iPhone (when it&#8217;s used as a hotspot) and via another Wi-Fi network.


My Wi-fi settings:
    Mode: Infrastructure
    Wi-Fi security: WPA & WPA2 Personal


I&#8217;ve had a look around on the internet for similar problems but it doesn&#8217;t seem to work. Does anybody know how to solve this issue?


P.S: I&#8217;ve tried resetting the router and turning off and on my PC a couple of times. Still get this problem.

**EDIT:** I forgot to mention that the Netgear adapter can connect to my home wifi perfectly fine from the same PC when I'm running Windows.

---

### Post by praseodym on 2015-05-06
Hi,

check with
```

iwlist chan
```

how many channels are shown. You may also change the router to b/g-mode and to pure WPA2-AES. Check the router manual. The driver does not support dualband or draft-N.

---

### Post by muhsin2 on 2015-05-06
Oh hey man! Thanks for posting the guide on how to get the Netgear adapter working on Ubuntu! That&#8217;s been super helpful.

When I type in &#8220;iwlist chan&#8221;, this is the output I get:

```
eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

lo        no frequency information.
```


Btw, the router operates both on 2.4GHz and 5GHz, with 2.4GHz on channel 6 (the Netgear adapter only picks up 2.4GHz). I forgot to mention that I can connect perfectly fine with the Netgear adapter to my home wifi from the same PC when I&#8217;m using Windows.

---

### Post by muhsin2 on 2015-05-07
> **praseodym said:**
> Hi,

check with
```

iwlist chan
```

how many channels are shown. You may also change the router to b/g-mode and to pure WPA2-AES. Check the router manual. The driver does not support dualband or draft-N.

My router supports both 2.4GHz and 5GHz, so I'm guessing my router is dualband? If so, that means that the driver won't work? Is it possible to get the Netgear adapter to work in another way or should I buy a different adapter now?

Cheers

---

### Post by grahammechanical on 2015-05-07
> it asks for the password again and again without connecting.

Just to eliminate the obvious, What password are you putting in? It is not our user password but the pass phrase or wireless key or WPA-PSK key to authenticate an encrypted connection to the router.

Regards.

---

### Post by muhsin2 on 2015-05-07
> **grahammechanical said:**
> Just to eliminate the obvious, What password are you putting in? It is not our user password but the pass phrase or wireless key or WPA-PSK key to authenticate an encrypted connection to the router.

Regards.
Hi, I'm putting in the router's passphrase, which works with all other devices in the house.

---

### Post by muhsin2 on 2015-05-08
I've bought a new wifi adapter. That works perfectly!

---

