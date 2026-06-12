---
title: "power consumption"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by skt.diaz on 2010-12-02
my dells core i3 cpu always seems to work alot under ubuntu compared to windows 7. system monitor shows avg. of 13% load on all 4 cores under idle conditions. is this normal?

---

### Post by NightwishFan on 2010-12-02
System Monitor always seems to have a bit of overhead of it's own. Try using top or htop from the terminal, under top look at the IDLE cpu usage above the process list.

---

### Post by Zzl1xndd on 2010-12-02
> **NightwishFan said:**
> System Monitor always seems to have a bit of overhead of it's own. Try using top or htop from the terminal, under top look at the IDLE cpu usage above the process list.

+1 System Monitor normally shows about 8-13%(on one of my cores). Where Top normally shows ~1%.

---

### Post by Crazedpsyc on 2010-12-02
Try getting granola, it says it saves 0.613864104 kWh per day for me and 43.6% CPU energy. I did actually notice both a decrease in temp and CPU usage when I first ran it!
[http://grano.la/](http://grano.la/)
(It's hosted in the US of A, and as far as I know *not* Los Angeles ;)

---

### Post by mcduck on 2010-12-02
> **skt.diaz said:**
> my dells core i3 cpu always seems to work alot under ubuntu compared to windows 7. system monitor shows avg. of 13% load on all 4 cores under idle conditions. is this normal?

Depends on what you are actually doing at the moment. And if the machine is idle, what kind of stuff you are running on your desktop.

Anyway, assuming the machine is idle, and that you aren't running loads of pretty docs and desktop widgets and such, then you definitely shouldn't have that high CPU load on idle..

And the first step in solving the problem is actually pretty simple, find out what is using the CPU. Ignore the pretty graph in System Monitor and instead change to the Processes-tab. Make sure it's set to list processes for all users and you should easily be able to see which one is using the CPU. Alternatively you can of course do the same using top, htop or whatever system monitoring tool you prefer.

---

