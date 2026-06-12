---
title: "Wireless works fine but then is gone"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by GearheadGambler on 2008-07-02
Well my wireless works then all of a sudden it will stop. It shows still connected but nothing happens. Once I disconnect the connection then reconnect it works again. What could be the problem?

---

### Post by untermensch on 2008-07-02
What wireless device do you have? 

can you show the output of iwconfig?

---

### Post by GearheadGambler on 2008-07-02
Broadcome internal wireless. I read through a dozen broadcome threads but all the ones I saw were the device wasn't connecting at all. Mine is intermittently shutting off.

here is iwconfig
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:E5:70:70:D9   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=80/100  Signal level=-53 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by untermensch on 2008-07-03
Did you install the ndiswrapper or the fwcutter to make it work?

---

### Post by GearheadGambler on 2008-07-03
> **untermensch said:**
> Did you install the ndiswrapper or the fwcutter to make it work?The onlything I installed was the network selector so I can disconnect and reconnect easily.

---

### Post by untermensch on 2008-07-03
How close are you to the router?

---

### Post by GearheadGambler on 2008-07-03
> **untermensch said:**
> How close are you to the router?

At my old apartment I was about 1-2ft away and in my house i'm a bit farther. I have constant access when I use my Vista partition so It can't be that i'm to far away.

---

### Post by GearheadGambler on 2008-07-06
anyone have any ideas?

---

### Post by untermensch on 2008-07-08
You still might wanna try installing the ndiswrapper. it usually gives better performance.

---

