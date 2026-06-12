---
title: "Fluctuating &amp; Poor Gigabit Network Speeds"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Rob_Quads on 2007-04-21
Recently I have moved my server from Windows to Linux. Its a Athlon 600 System with a DLink Gigabit Network card. It has a range of discs, some configured in raid. I have performance transfer tests from Windows -> Ubuntu and the transfers have been fluctuating causing reduced through-put.

Below is a copy of a graphical output from the windows machines when transfering a 500MB file. This was from Windows -> Ubuntu, Gigabit -> Gigabit

[img]http://www.convery.me.uk/temp/transferspeed.jpg[/img]

Below is a copy of the chart when transfering from the same windows machine to another windows one : Gigabit -> 100Mbit

[img]http://www.convery.me.uk/temp/transferspeed2.jpg[/img]

As you can see a solid transfer. Anyone know what could be causing this strange pulsing of transfers?

I have a separate issue of my RAID being slower than normal IDE but below is a table of some of my results

Windows -> Ubunutu
Gbit	     -> Gbit

500MB File

> IDE  - Samba	Max~175Mb
> IDE  - FTP	Max 210Mb	524288000 bytes sent in 29.39Seconds 17838.99Kbytes/sec. 142Mb Av
> RAID - Samba	
> RAID - FTP	Max 198Mb	524288000 bytes sent in 39.17Seconds 13384.25Kbytes/sec. 107Mb Av

Windows -> Windows
Gbit 	-> 100Mb

-> IDE  - Samba Max 80.2Mb
-> IDE  - FTP	Max 99.4Mb	524288000 bytes sent in 49.34Seconds 10625.16Kbytes/sec. 85Mb Av	


Windwos -> Ubuntu
100Mb	-> Gbit

-> IDE	- Samba	Max~72.1Mb
-> RAID	- Samba	Max~72.1Mb
-> IDE	- FTP	Max 98.5Mb	524288000 bytes sent in 49.34Seconds 10625.16Kbytes/sec  85Mb Av
-> RAID	- FTP	Max 98.5Mb	524288000 bytes sent in 55.00Seconds 9532.51Kbytes/sec.  76Mb Av

Previously when the same machine was setup as a windows box I was able to get much closer to 300Mb (I think maybe more in fact)

---

