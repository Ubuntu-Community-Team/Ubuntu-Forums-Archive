---
title: "How to set up WiFi hotspot in 18.04, similar to mobile hotspot in Windows 10?"
date: 2023-06-06
forum: Networking &amp; Wireless
---

### Post by fadijosh on 2023-06-06
[COLOR=#000000]Hello all,[/COLOR]

[COLOR=#000000]I'm new to the forum here. I've searched for the exact query already and didn't seem to find suitable answers[,]("https://ebillwizard.com/") thus posting this. Windows 10 has nifty trick called Mobile Hotspot which shares the computer's internet (Wired or Wireless) with upto 8 devices by creating a Wifi hotspot. ebill Searching for its equivalent in Ubuntu, I found answers for creating a hotspot (which disconnects from the connected network, thus a hotspot without internet) and for routing Ethernet to Wifi hotspot, but not for this. Any suggestions are welcome.[/COLOR]

[COLOR=#000000]To clarify, I already use mobile hotspot in Windows 10, so I'm confident my laptop's hardware supports this feature: simultaneously connected to a Wifi and routing its internet through a hotspot. If it is a case of lack of driver support in Ubuntu, then there's not much that can be done. However, if there is some option to enable this feature or if its already present that I've blindly overlooked, please enlighten.[/COLOR]

---

### Post by coffeecat on 2023-06-07
Support question, not chat. *Thread moved to **Networking & Wireless** sub-forum.*

---

### Post by guiverc on 2023-06-07
You do realize Ubuntu 18.04 LTS, which was released in 2018-April (*thus the 18.04*) had 5 years of *standard *support, which has ended (*even with an additional month that extended life until May 2023*)

- [https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/](https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/)
- [https://ubuntu.com//blog/18-04-end-of-standard-support](https://ubuntu.com//blog/18-04-end-of-standard-support)

Why would you want to use an EOSS system for such a task?  I'd suggest instead installing a *supported* system, or are you researching malware spread?

FYI:  You can use `ubuntu-support-status` to confirm the status of your actual system.

---

### Post by TheFu on 2023-06-07
To setup what you want, this is called "a router".  There are many, many, how-to guides for accomplishing it.  In general, it is a really bad idea for security reason to run this on a computer that is used for other tasks. Definitely avoid doing it on a desktop.

But you may not have any other choice, so google found these guides from reputable sources: 
[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-adhoc.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-adhoc.html.en)
[https://www.omgubuntu.co.uk/2023/05/create-wifi-hotspot-on-ubuntu](https://www.omgubuntu.co.uk/2023/05/create-wifi-hotspot-on-ubuntu)

If it were me, I'd reconsider.  Maybe getting a small _travel router_ would be a better answer?  I had one for travel that was smaller than most external SSD -to- USB enclosures.  Used it all over Europe, Central/South America, Africa and in Asia.  Think it was about $50, but that was about 15 yrs ago. I haven't used it in a very long time. Certainly it is full of security failures due to age.

+1 on not using 18.04 as the base.  Probably should use 22.04 on any new install to physical hardware these days, unless you have a really, really, good reason.  You can always put 18.04 into an lxd/lxc container, which wouldn't risk nearly as much as 18.04 does.

---

