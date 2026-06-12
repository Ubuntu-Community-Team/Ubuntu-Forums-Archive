---
title: "Particular Website Not Working (Not The Websites Fault)"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by invixus on 2007-07-10
Ok, basically a month or so ago i stopped being able to access a particular website (Muselive.com) yet the website remains ok to what seems like everyone else.

I have:
[LIST]
[*]Contacted my ISP - "not their problem, works for them"
[*]Got one of the other people who manage the server to have a look around - seemed ok
[*]Contacted the datacenter - no network issues
[*]Tried a different ADSL modem locally - no difference
[*]Isolated a PC to be soley connected to the internet - no difference
[*]Tried 3 computers 2 OS's 3 browsers - all with the same error
[/LIST]

Now, i know this pretty much proves the problem is not with ubuntu but i know that there are quite a lot of clever people here who might still be able to help.

The interesting thing is that instantly after resetting my modem/router, the website seems to work for about half an hour or so. But i have to reset all settings on the router. This is why i was stumped when a friends modem/router didn't work.

If it would help people, here are a couple of traceroutes, the first when it doesn't work and the second when its in the window of time working:
```
traceroute to muselive.com (72.232.90.234), 30 hops max, 40 byte packets
 1  192.168.0.5 (192.168.0.5)  26.644 ms  21.213 ms  19.226 ms
 2  ###.###.uk.easynet.net (82.108.###.###)  21.043 ms  20.261 ms  20.448ms
 3  ip-89-200-130-27.ov.easynet.net (89.200.130.27)  22.058 ms  19.559ms  19.260 ms
 4  ip-89-200-134-117.ov.easynet.net (89.200.134.117)  23.395 ms  21.393ms  20.656 ms
 5  te-3-3.r00.londen05.uk.bb.gin.ntt.net (83.231.146.65)  181.233 ms 251.111 ms  216.870 ms
 6  xe-3-2.r00.londen03.uk.bb.gin.ntt.net (129.250.3.46)  239.395 ms 242.536 ms  244.528 ms
 7  xe-0-1-0.r22.londen03.uk.bb.gin.ntt.net (129.250.2.77)  160.303 ms 156.123 ms  161.036 ms
 8  p64-2-1-0.r21.nycmny01.us.bb.gin.ntt.net (129.250.2.38)  236.282 ms 229.409 ms  228.706 ms
 9  p16-1-0-0.r05.nycmny01.us.bb.gin.ntt.net (129.250.3.49)  227.856 ms 226.264 ms  227.139 ms
10  acr1-so-5-1-0.NewYork.savvis.net (129.250.9.78)  93.458 ms  93.994ms  94.043 ms
11  bcs1-so-3-0-0.NewYork.savvis.net (204.70.192.194)  94.032 ms bcs2-so-1-1-0.NewYork.savvis.net (204.70.192.210)  94.292 ms bcs1-so-1-1-0.NewYork.savvis.net (204.70.192.186)  94.454 ms
12  bcs1-so-6-0-0.NewYork.savvis.net (204.70.192.37)  96.576 ms dcr2-so-3-0-0.Chicago.savvis.net (204.70.192.101)  119.185 ms bcs1-so-6-0-0.NewYork.savvis.net (204.70.192.37)  112.424 ms
13  dcr1-so-3-0-0.Atlanta.savvis.net (204.70.192.53)  147.971 ms dcr2-so-3-0-0.Chicago.savvis.net (204.70.192.101)  135.029 ms dcr1-so-3-0-0.Atlanta.savvis.net (204.70.192.53)  139.314 ms
14  dcr1-so-3-0-0.Atlanta.savvis.net (204.70.192.53)  138.476 ms bhr1-pos-1-0.fortworthda1.savvis.net (208.172.129.230)  145.247 ms dcr2-so-0-0-0.dallas.savvis.net (204.70.192.98)  145.539 ms
15  bhr1-pos-12-0.fortworthda1.savvis.net (208.172.131.82)  141.828 ms dcr2-as0-0.Atlanta.savvis.net (204.70.192.42)  140.792 ms hr1-vlan-245.FortWorthda1.savvis.net (208.172.131.46)  146.164 ms
16  hr1-vlan-245.FortWorthda1.savvis.net (208.172.131.46)  143.830 ms dcr2-so-2-0-0.dallas.savvis.net (204.70.192.70)  141.332 ms  141.209 ms
17  216.39.81.50 (216.39.81.50)  140.808 ms dcr1-so-6-0-0.dallas.savvis.net (204.70.192.49)  140.695 ms 216.39.81.50 (216.39.81.50)  142.890 ms
18  * bhr1-pos-12-0.fortworthda1.savvis.net (208.172.131.82)  142.707 ms *
19  hr1-vlan-245.FortWorthda1.savvis.net (208.172.131.46)  141.879 ms 299.358 ms *
20  216.39.81.50 (216.39.81.50)  140.010 ms * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```

```
traceroute to muselive.com (72.232.90.234), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  27.989 ms  25.311 ms  25.478 ms
 2  ###.###.uk.easynet.net (82.108.###.###)  24.176 ms  26.148 ms  31.023 ms
 3  ip-89-200-130-27.ov.easynet.net (89.200.130.27)  34.360 ms  26.918 ms  23.450 ms
 4  * ip-89-200-132-80.ov.easynet.net (89.200.132.80)  22.640 ms  26.914 ms
 5  te-3-3.r00.londen05.uk.bb.gin.ntt.net (83.231.146.65)  28.410 ms  21.656 ms *
 6  xe-3-2.r00.londen03.uk.bb.gin.ntt.net (129.250.3.46)  102.525 ms  104.160 ms  102.160 ms
 7  xe-0-1-0.r22.londen03.uk.bb.gin.ntt.net (129.250.2.77)  24.294 ms  22.680 ms  22.934 ms
 8  * p64-2-1-0.r21.nycmny01.us.bb.gin.ntt.net (129.250.2.38)  104.286 ms  120.603 ms
 9  p16-1-0-0.r05.nycmny01.us.bb.gin.ntt.net (129.250.3.49)  102.018 ms *  101.801 ms
10  acr1-so-5-1-0.NewYork.savvis.net (129.250.9.78)  93.667 ms acr1-so-6-0-0.NewYork.savvis.net (129.250.9.50)  102.318 ms acr1-so-5-1-0.NewYork.savvis.net (129.250.9.78)  99.929 ms
11  * * bcs2-ge-4-3-3.newyork.savvis.net (204.70.193.81)  95.905 ms
12  bcs1-so-1-1-0.newyork.savvis.net (204.70.195.2)  100.076 ms bcs2-so-3-1-0.newyork.savvis.net (204.70.195.50)  97.316 ms  101.881 ms
13  * dcr2-so-3-0-0.Chicago.savvis.net (204.70.192.101)  132.529 ms bcs1-so-6-0-0.NewYork.savvis.net (204.70.192.37)  114.570 ms
14  bcs1-so-6-2-0.Washington.savvis.net (204.70.192.13)  140.776 ms dcr1-so-3-0-0.Atlanta.savvis.net (204.70.192.53)  141.204 ms dcr2-so-3-0-0.Chicago.savvis.net (204.70.192.101)  121.084 ms
15  bhr1-pos-1-0.fortworthda1.savvis.net (208.172.129.230)  143.163 ms dcr1-so-3-2-0.dallas.savvis.net (204.70.192.82)  139.132 ms dcr1-so-3-0-0.Atlanta.savvis.net (204.70.192.53)  141.925 ms
16  hr1-vlan-245.FortWorthda1.savvis.net (208.172.131.46)  144.343 ms bhr1-pos-1-0.fortworthda1.savvis.net (208.172.129.230)  147.138 ms hr1-vlan-245.FortWorthda1.savvis.net (208.172.131.46)  145.890 ms
17  hr1-vlan-245.FortWorthda1.savvis.net (208.172.131.46)  281.724 ms  145.505 ms dcr2-so-2-0-0.dallas.savvis.net (204.70.192.70)  138.250 ms
18  216.39.81.118 (216.39.81.118)  138.618 ms dcr1-so-6-0-0.dallas.savvis.net (204.70.192.49)  136.903 ms 216.39.81.118 (216.39.81.118)  213.255 ms
19  * * bhr1-pos-12-0.fortworthda1.savvis.net (208.172.131.82)  139.061 ms
20  srv45.serverwin.info (72.232.90.234)  150.188 ms  153.167 ms  150.144 ms
```

Due to the nature of this problem it may be something way beond my understanding or it might be something staring me in the face which i am simply overlooking. Any help on the matter would be massively appreciated.

Thanks in advance,
Lewis

---

### Post by tturrisi on 2007-07-10
Try using the ip address in the browser address bar: 72.232.90.234
That site uses a redirect to load the page.

---

### Post by Mr. C. on 2007-07-11
See my post here:

[http://ubuntuforums.org/showthread.php?t=477659&highlight=mrc+tcp&page=2](http://ubuntuforums.org/showthread.php?t=477659&highlight=mrc+tcp&page=2)

MrC

---

### Post by invixus on 2007-07-11
Ok, well for some reason, things seem to be working today... I cant think of anything i have done differently, and it has taken a month or so to start working.

Thanks for your suggestions, i will keep them in mind incase the issue rears its head again in the near future.

---

