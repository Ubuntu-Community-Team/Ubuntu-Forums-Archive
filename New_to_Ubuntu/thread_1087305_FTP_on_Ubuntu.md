---
title: "FTP on Ubuntu"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by ClaytonOT on 2009-03-04
I'm trying to load a phpbb3 board onto my server and I keep running into upload errors while doing it. (error uploading (insertnamehere).gif or .jpg) its been mostly like images but it's common enough that I've hit skip all on every error. I'll have to piece together what messed up and what didn't later.

I'm using the Places>Connect to Server

I've not experienced any issues with uploading through FTP on Winblows so I'm wondering if there's some configuration I need. I also am getting an insanely slow upload speed - I'm on wifi but there's no reason I should only be uploading at 1kbps.

> 
1  dlink.dir450 (192.168.0.1)  2.210 ms  2.287 ms  2.558 ms
 2  192.sub-66-174-112.myvzw.com (66.174.112.192)  131.488 ms  131.687 ms  160.196 ms
 3  127.sub-66-174-112.myvzw.com (66.174.112.127)  161.207 ms  201.173 ms  202.123 ms
 4  82.sub-66-174-15.myvzw.com (66.174.15.82)  203.146 ms  226.429 ms  227.863 ms
 5  194.sub-66-174-15.myvzw.com (66.174.15.194)  229.780 ms  230.770 ms *
 6  * 106.sub-66-174-14.myvzw.com (66.174.14.106)  240.563 ms *
 7  * 253.sub-69-83-18.myvzw.com (69.83.18.253)  158.035 ms  177.162 ms
 8  GigabitEthernet5-1.GW4.PHL6.ALTER.NET (157.130.48.49)  199.006 ms *  232.838 ms
 9  0.so-4-2-0.XL1.PHL6.ALTER.NET (152.63.37.174)  234.081 ms  268.792 ms  269.803 ms
10  0.so-5-2-0.XL3.IAD8.ALTER.NET (152.63.36.25)  293.466 ms  320.109 ms  320.073 ms
11  0.ge-6-1-0.BR2.IAD8.ALTER.NET (152.63.41.153)  356.296 ms * *
12  xe-2-1-0.er2.iad10.us.above.net (64.125.13.173)  159.526 ms  155.904 ms  155.730 ms
13  * ge-3-0-0.mpr2.dca2.above.net (64.125.26.241)  136.995 ms  133.386 ms
14  ge-3-3-0.mpr2.dca2.us.above.net (64.125.27.30)  161.569 ms  180.323 ms  145.727 ms
15  so-1-0-0.mpr4.iah1.us.above.net (64.125.28.50)  183.387 ms  171.563 ms  167.068 ms
16  xe-1-1-0.er2.iah1.above.net (64.125.26.226)  179.781 ms  177.674 ms  198.762 ms
17  xe-0-0-0.er1.iah1.us.above.net (64.125.26.217)  202.767 ms  226.106 ms  187.659 ms
18  * 209.66.99.94.available.above.net (209.66.99.94)  170.277 ms  174.502 ms
19  et1-3.ibr02.hstntx2.theplanet.com (70.87.253.58)  160.743 ms  481.668 ms  460.042 ms
20  po2.car06.hstntx2.theplanet.com (74.55.252.114)  439.351 ms  455.811 ms  455.651 ms
21  * * *


---

### Post by sujoy on 2009-03-04
try gftp its a nice app :)

---

### Post by ClaytonOT on 2009-03-04
> **sujoy said:**
> try gftp its a nice app :)

I saw that was an option - I'll give it a shot thanks.

---

### Post by DGortze380 on 2009-03-04
or 

places -> connect to server

---

### Post by ClaytonOT on 2009-03-04
> **DGortze380 said:**
> or 

places -> connect to server

...thats what I originally did - doesn't work well for me.

I am using GFTP now and it works great. Thanks.

These matters are closed.

---

