---
title: "Monitor Mode"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by digital9ja on 2007-03-14
I've got a ZICOM325HP+ and am running Kubuntu/Edgy. I've been going nuts all night trying to get my card to go into monitor mode so I could run kismet and wepdecrypt. I used this card before and I know it's capable of RFMON so I couldn't understand why I kept getting:

```
xxx@xxxxx:~/Security/Wifi/wepdecrypt-0.8/doc$ iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.

```

I thought the system was using the wrong driver or something. Turns out, luser I am, forgot SUDO! 

Now kismet is happily logging packets, wepdecrypt is churning through it's wordlist and I can finally get to sleep. Been up since 7pm Tuesday!

---

