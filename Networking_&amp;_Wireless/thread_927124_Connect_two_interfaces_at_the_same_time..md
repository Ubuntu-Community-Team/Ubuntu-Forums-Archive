---
title: "Connect two interfaces at the same time."
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by EtherBunny on 2008-09-22
So I have these 2 wireless interfaces, wlan0 and rausb0.

What I would like to do is connect both of them at the same time.

I connect wlan0 first. It gets an ip and I can connect to the internet, browse the web, etc.

Then I try to connect rausb0. I set the wireless info to the same as wlan0, then run dhclient on it. After I do dhclient rausb0. The command completes and rausb0 gets an ip (a different one from wlan0).

After this is done, I can't connect to the internet any more. I can't ping anything or browse the web. At this point, ifconfig shows both interfaces as having an ip.

If I take rausb0 back down with "ifconfig rausb0 down", the internet works fine again.

I'd like to know the proper way to have two interfaces up and running at the same time and (if possible) how to select which one to "use".

By the way, I uninstalled networkmanager a while ago. I don't like it. Also, before you post telling me that this is ridiculous and pointless, I know. I'm just seeing what I can do with my laptop and pile of 3 usb wifi adapters.

Thanks!

---

### Post by Iowan on 2008-09-23
> **EtherBunny said:**
> ...this is ridiculous and pointless:lolflag:
Sorry - couldn't resist...
What address are assigned?  If they're in the same subnet, the system will have a problem.

---

### Post by EtherBunny on 2008-09-26
Ah, yeah. They're both in the same subnet. What's the problem?

---

