---
title: "Ubuntu 7.04 and Netgear WG111T"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by tiddy on 2007-04-25
Hi, I'm really stuck on this one: I have the notorious Netgear WG111T wireless dongle and It will not work. I have tried the latest ndiswrapper (1.38 ) from the repositories and all seems well until I actually do modprobe ndiswrapper. This does not seem to do anything but gives no errors and when I run modprobe -r ndiswrapper it gives me about a page of errors (something to do with the kernel) exactly the same thing happens when I build ndiswrapper (1.42) from source. I am installing both drivers I have tried from the CD and from the website, with the same results each time.

Thanks for any help.

---

### Post by MissDraven on 2007-07-20
I have the same problem.
I've installed the drivers but the adapter doesn't work.I'm so tired.
What can I do to make it work?
I need your help quickly!..and I'm not an Ubuntu expert..
Can someone tell me,step by step,what I have to do,please??

---

### Post by abstractism on 2007-09-06
I think the reason you're getting errors with 'modprobe -r ndiswrapper' is because that removes it. and that kind of command needs sudo to work properly. 
I'm got 2 of these WG111T USB adapters and I scoff in disapproval at these (so far) nonfunctional networking devices. Feh.

---

