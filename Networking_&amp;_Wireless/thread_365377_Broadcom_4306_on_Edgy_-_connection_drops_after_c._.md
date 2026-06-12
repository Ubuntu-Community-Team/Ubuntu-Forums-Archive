---
title: "Broadcom 4306 on Edgy - connection drops after c. 30 mins"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by plumstead21 on 2007-02-19
Hello,

I've recently installed Edgy and set up my wireless connection - I have a Broadcom 4306 card.  It works fine for a while then the connection drops after about half an hour, with no obvious cause.  I'm a Linux n00b so please go easy on me :-)

Here is the output of sudo iwconfig eth1 when it's working (I've xx'd out the encryption key):

```
eth1      IEEE 802.11b/g  ESSID:"BachNByte"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:50:79:C2:7D   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Link Quality=106/100  Signal level=-29 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:44  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Last time it stopped working I ran iwconfig again (forgot to do sudo iwconfig but hopefully this will be enough info) and got the following

```
eth1      IEEE 802.11b/g  ESSID:"BachNByte"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:11:50:79:C2:7D   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=106/100  Signal level=-30 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:532  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I've never had a problem with it in Windows XP.

I'd be very grateful for any help or advice, or any other diagnostic commands I could run!  Many thanks.

---

### Post by teaker1s on 2007-02-20
are you using ndiswrapper? or native kernel module or bcmcutter?

good link for ndiswrapper in my signature

---

### Post by plumstead21 on 2007-02-21
Hello,

Thanks for the reply.  I think I'm using the native kernel module, as I certainly haven't installed ndiswrapper and I don't think I'm using bcmcutter.  Thanks for the link about setting up ndiswrapper with the card: would you recommend doing it this way instead?

---

### Post by teaker1s on 2007-02-21
if it works natively then it is better to do it that way, if on the other hand you find that it is unresolvable then ndiswrapper is a good reliable alternative.
reason i asked about bcmcutter is it's been found to be extremely unreliable on some models

---

### Post by plumstead21 on 2007-02-23
Update: it turns out I was using bcmcutter.  (I think I just panicked when I couldn't get the card to work and tried lots of alternatives without clearing up properly...)  I've now uninstalled it and followed the [step-by-step guide for Broadcom 4306 on ndiswrapper by maclenin]("http://ubuntuforums.org/showthread.php?t=340689") which seems to have worked a treat.  Speed seems faster now too :) 
Thanks!

---

