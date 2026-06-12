---
title: "Hdd help"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by DarinB on 2011-08-17
I don't know where this would go but I am stuck and need some basic computer help. 
I was using an old laptop with a toshiba hdd2d38 small laptop hdd. 
the laptop died i think motherboard... I got a new pc installed lucid lts. runs great. now i need the files off this hdd. I can't seem to find out what type of interface it has I got a sata, iede to usb and was able to get the data of other HDDs but this tiny one has a 7 pins but small than my fullsize sata drives. I am trying to figure out what type of adapter to get. so I can usb it to my new pc. I was wondering if anybody can help me with this. is it a slim form or micro form or just serial ATA 7 pin....and is that the same as a slim or micro. 
maybe there is a simple source I can find to learn about the different interfaces. so far I have not found one. 

Please forgive me if this is not so ubuntu-ish!!!

---

### Post by aeiah on 2011-08-17
googling around tends to suggest its sata :-?

---

### Post by HereInOz on 2011-08-17
If it is sata, it will have 4 small pins at one end, then a small spade type connector with 7 connector strips on it, then another spade type connector with 15 connector strips on it.

Does this help any?

---

### Post by seawolf167 on 2011-08-17
There are only three hard drive connection types:

[LIST]
[*]PATA
[*]SATA
[*]SCSI
[/LIST]
It won't be PATA if it was new within the past 6 years or so, and it won't be SCSI since it was a laptop and not a server, so I'm sure it is a SATA connection. So something [like this ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002")would work as an adapter (I actually have this one, you'll need a SATA cable to connect it and a 4pin molex to SATA power adapter to power the drive separately)

---

### Post by DarinB on 2011-08-17
I bought the one mentioned above with the adapter for two types of connectors and the red wire for the sata. but they don't fit on this hard drive the connections are much smaller on the toshiba hdd2d38. 

I am wondering if it is a slim form factor or micro form factor.

---

### Post by pi.boy.travis on 2011-08-17
I've never had a Toshiba laptop. Maybe it's a proprietary connector?

---

### Post by linuxman94 on 2011-08-17
Maybe check out this one. The power and data cables are separated on it.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156014]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812156014")

---

### Post by DarinB on 2011-08-17
hi folks I am still trying to figure this out it is an old hdd from a compaq laptop maybe 5 years old. 
here are some pictures I did buy the sata/ide to usb kit but nothing fits it. [ATTACH]200236[/ATTACH]

[ATTACH]200237[/ATTACH]

[ATTACH]200238[/ATTACH]

[ATTACH]200239[/ATTACH]

---

### Post by elgordodude on 2011-08-17
Yes SATA

[http://www.amazon.com/Toshiba-MK8034GSX-internal-SATA-150-buffer/dp/B000YIWP1U](http://www.amazon.com/Toshiba-MK8034GSX-internal-SATA-150-buffer/dp/B000YIWP1U)

---

### Post by dave01945 on 2011-08-17
the number of pins mathches a sata connection ide(pata) are 40 pin i believe but that doesn't look like a standard sata connection

is there maybe another piece that broke of maybe in the laptop

or there is an extra piece still on the hdd that maybe can pull of to reveal a standard sata connector

---

### Post by DarinB on 2011-08-17
OMG you are a genius!!!! there was a piece attached to it with a tiny screw. awesome now I have access to the hdd.

---

### Post by Kixtosh on 2011-08-17
Clever detective work folks! It's possible to see the piece that is still stuck on the drive from the images posted. Just for clarity, in case of future need, the correct designation of that hard drive is not HDD2D38, but:

**MK8034GSX**

It's quite a standard drive for laptops.

[http://sdd.toshiba.com/main.aspx?Path=StorageSolutions/2.5-inchHardDiskDrives/MK8034GSXPage/MK8034GSXSpecifications](http://sdd.toshiba.com/main.aspx?Path=StorageSolutions/2.5-inchHardDiskDrives/MK8034GSXPage/MK8034GSXSpecifications)

---

