---
title: "weird wired network speed issues, who will give me a hint ;)"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by genomebob on 2008-04-27
I've got strange wired network speed issues and i can't get my finger behind whats going wrong here. 
please bear with me, i'll explain my setup and the symptons.

The setup:
workstation: asus p5k mobo, q6600, 4gig ram. with one marvel yukon 1gbit NIC and a generic rtl8139. hardy heron 64bit desktop fresh installed last saturday.
server: ubuntu 7.10 (desktop) pentium4D@3ghz, 1gig ram, 1 intel e1000. runs samba(fileserver).
The machines are connected using a crosslink on their gigabit links.
Both machines are connected to a 100mbit switch, which connects my home network, which connects to a router and internet.
The gigabit nics ofcourse use a different subnet then the 100mbit links.

Symptoms: slow transfers between the workstation and other hosts on the network. but decent internet speed.

If i run the workstation on winXP, network speed over all the NICs is good. The server feeds me about 45Mbyte/s via samba, and maxes out over 100mbit.

If i run the workstation hardy heron 64bit, the samba transfer over gigabit slows to 20k!. when i stop nfs-client, speeds go up to 4to5 MB/s.. ?? weird. If i transfer over the 100mbit line from server to workstation, same thing, 14k, sometimes nothing.

But now it gets weird. From my workstation, downloading something from the internet, i get the max speed of my dsl line (about 12mbit).
trying an http transfer from my server, 12k..

i tested this with all nics enabled, or with just the ones enabled that i was testing at the moment. It didn't change the outcome of the tests.

from my laptop, hardy heron 32 desktop, over 100mbit downloading from my server, everything works fine.
from my workstation, downloading over samba from my worklaptop (xp) .. SLOW..

:confused:

Any clues ? i'm totally lost here, i don't know what to check next. i don't think its a hardware issue because it works in xp. considering that transfers coming from the internet go faster then from a local server, i assume something is set in tcp settings, but where to look?. 
I set all IP adresses statically.

I'm going to try to install hardy heron 32 desktop, just to test, but i rather run 64bit (coz i got the 4 gig ram so i can run many vm's in xen and vmware which weren't enabled at the time of testing)

Thanks.

---

### Post by SilentMobs on 2008-04-27
It could be a multiplexing issue.
Try limiting the Ubuntu 1000Mbs card to 100Mb and see what happens. I had the same issue because my gigabit router just wasn't letting my 2 gigabit cards communicate properly. It was fine if I was transferring 2 files but 1 file took forever.

---

### Post by genomebob on 2008-04-28
unfortunately that didn't work. I installed 64bit debian etch, it fixed the speed issues. next thing i'm going to try is 32 bit hardy, just to see if its just the 64bit ubuntu-made kernel. if that works then i guess its not yet time for me to go 64bit :(

---

### Post by genomebob on 2008-04-28
changing the switch did the trick. now everything is fullspeed again.:lolflag:

---

