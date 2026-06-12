---
title: "[SOLVED] Crossover Cable  - Transfer Protocol?"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Sutur on 2008-11-09
Just a question on the next step of using a crossover cable on the protocol:

I've tried SSH to transfer a large volume of files (120GB) from a desktop to a laptop. However, if using **scp **the session will hang, and I have to close and restart it. If using **gftp **(with ssh protocol) the program just crashes after about 1300 directories (and maybe 30 files).

Is my solution to set up an ftp server instead? I just want an easy transfer method that will get the job done as fast as my systems can send & recieve.

What protocol/applications should I use?

---

### Post by huwnet on 2008-11-09
The fastest thing for me has always been netcat. Checkout this tutorial: [http://compsoc.dur.ac.uk/~djw/tarpipe.html](http://compsoc.dur.ac.uk/~djw/tarpipe.html)

It is in the ubuntu repos if you don't have it installed by default

---

### Post by jflaker on 2008-11-09
I have never tried it, but if you set a static IP on each computer of like

Computer A: 10.10.10.1
Computer B: 10.10.10.2

You should be able to transfer like if you were on a network.  If you have a router, just plug both systems into the router and transfer....

---

### Post by Sutur on 2008-11-10
> **huwnet said:**
> The fastest thing for me has always been netcat. Checkout this tutorial: [http://compsoc.dur.ac.uk/~djw/tarpipe.html](http://compsoc.dur.ac.uk/~djw/tarpipe.html)

It is in the ubuntu repos if you don't have it installed by default
[B][I]
[SIZE="5"]EXCELLENT.[/SIZE][/I][/B]

Thank you huwnet, - the speed is outstanding.

I wonder if I added the "-v" verbose switch if I would ged feedback on what it's doing and where it is?

---

