---
title: "HELP: WG111v2 wireless impossible on 6.10"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by asahani on 2007-03-03
Hi Guys,
This is my forst post on the forums. I am a total newbie to linux and Ubuntu. I got the Netgear WG111v2 USB wireless  adapter. I tried installing but i have been majorly frustrated.
Firstly, I tried the plug and play option. Wlan0 is configured but there are no lights on the adapter and i cannot get a ip from the router using DHCP. then i tried installing the drivers using ndiswrapper ...the lights flashed for a few seconds but still no connection. I cannot even ping my router. I have been very upset for the last couple of days in order to get this to work.

Please help!!! i really need to get this working before the weekend is over.

All help would be greatly appreciated.

Cheers,

Amaan

---

### Post by asahani on 2007-03-03
c'mon guys....some help would be great....please!!!

---

### Post by nyinge on 2007-03-04
Could you please post the output of the following:  ```
 iwconfig wlan0 
``` and ```
 ifconfig wlan0 
``` and ```
 ndiswrapper -l 
```

Thank you.

---

### Post by asahani on 2007-03-04
hey man...thanks for repling....i finally got it working by changing the driver to the win98 driver for the netgear wg111v2.
Now that we are on the topic....how can i associate a nodename for my box so that i can ssh into it from another machine?

any idea?

---

### Post by nyinge on 2007-03-04
I just edited the /etc/hostname, but I've also heard other numerous ways to do it.  I cannot remember at the top of my head for other ways.  However, my router doesn't seem to recognize it, unless I deliberately set a static ip and assign a hostname.  I prefer using the ip for ssh anyway.

---

### Post by phossal on 2007-03-09
kvonb and I wrote a decent tutorial on it. A link is in my signature. Many, many people have used it successfully.

---

