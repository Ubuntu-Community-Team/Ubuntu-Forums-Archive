---
title: "connect to wireless network"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by kasra_k on 2008-05-09
Hello guys!
I want to connect to a wireless network!
when in termianl i type
```
iwlist scan
```
it shows me it:
```
eth0      Scan completed :
          Cell 01 - Address: 32:00:5D:01:B0:01
                    ESSID:"HomeNet"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=92/100  Signal level=-57 dBm  Noise level=-65 dBm
                    Extra: Last beacon: 28ms ago


```

I want to connect to that network without network-manager applet!
anyone know how can i connect to that in Terminal?:confused:

I advance my wireless card in boradcom 4306 linksys!
and the laptop('HomeNet' network)is cisco PCMSIA card!
my OS os Gusty but the laptop is feisty!

---

### Post by kasra_k on 2008-05-09
anyone can't help me?

---

### Post by kasra_k on 2008-05-10
Not anyone?

---

### Post by gsalem on 2008-05-10
Did you look into iwconfig (man it to do iwconfig --help)?

---

### Post by kasra_k on 2008-05-10
Yes.I have read that but it hasen't sloved my problem yet!

---

### Post by kasra_k on 2008-05-10
Waiting for response...

---

### Post by kasra_k on 2008-05-12
guys please!
I need that!

---

### Post by cubeist on 2008-05-12
First, my advice would be to connect via network manager... it is easier than iwconfig.

Second, are you sure you read through the help pages for iwconfig (man iwconfig) because they are fairly straight forward.

For example, to connect using iwconfig you would type something like

iwconfig etho essid "HomeNet"

if it password protected you will also need to add the key... see the section marked key in the man pages...

---

