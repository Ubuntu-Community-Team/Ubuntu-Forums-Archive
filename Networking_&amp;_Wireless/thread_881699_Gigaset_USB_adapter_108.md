---
title: "Gigaset USB adapter 108"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by dijxtra on 2008-08-06
Yesterday I installed kubuntu 8.4.1 on a machine that uses  Gigaset USB adapter 108 to connect to Gigaset SE555 WLAN dsl. I installed ndiswrapper and the driver for the adapter (net5523.inf) and the connection to the SE55 was successfully established the moment ndisgtk loaded the driver. Excellent. Then I ran pppoeconf and got my Internet connection up and running. I installed synaptic and firefox and rebooted.

And then the nightmare started. Adapter won't get recognised. Most of the time :-D That is, it is sometimes recognised as wlan0 and most of the time not.

So, in, say 15% of time adapter is recognised as wlan0. Then in 50% of the time it successfully connects to SE555 and in 50% of time I have to do it manually. And then when connection to SE555 is established, then I have to run pppoeconf to connect to the Net. Just "pon dsl-provider" won't do it. And once even ppoeconf didn't do the work.

In the rest 85% of time adapter is not recognised at all. ifconfig doesn't show it. lshw doesn't have a close about it. Fun, eh?

Anyway, does anybody know what I have to do to make my  Gigaset USB adapter 108 work?

Thanks,
dijxtra

---

### Post by dmizer on 2008-08-06
When the adapter works, take a look at these commands:
```
lshw -C network
```
```
lsmod
```
```
lsusb
```

Then run the same commands when the adapter does not work, and compare the differences.  Post here if you are unsure of what to look for. From the sound of things, you've simply neglected to blacklist the native driver for the adapter.

---

### Post by dijxtra on 2008-08-06
> **dmizer said:**
> From the sound of things, you've simply neglected to blacklist the native driver for the adapter.
It'd be very nice if that was the problem. I've already started considering buying a brand new wifi network card ;-)

Anyway, here is what the commands you requested have to say:

This one is when wlan0 is not recognised at all: [http://fly.srk.fer.hr/~nick/pub/log0.txt](http://fly.srk.fer.hr/~nick/pub/log0.txt)

I was lucky, so in the few reboots I did, I managed to get wlan0 recognised. Here is the log when wlan0 was recognised, the situation as it was just after the machine booted: [http://fly.srk.fer.hr/~nick/pub/log1.txt](http://fly.srk.fer.hr/~nick/pub/log1.txt)

Here is what I did next: I chose "manual configuration" from right-click KNetworkManager menu and then manually configured wlan0 for automatic IP retrieval using DHPC. When I clicked OK, KNetworkManager turned to that icon showing strength of wireless signal. Some 30 seconds afterwards I was connected to the Internet (no pppoeconf, no nothing, it happened all by itself).

After that I did the commands you requested once again. Here's what those had to say: [http://fly.srk.fer.hr/~nick/pub/log2.txt](http://fly.srk.fer.hr/~nick/pub/log2.txt)

I hope you can figure out what happened here from the output I provided. I unfortunately didn't manage to produce the situation when I have wireless signal, but no Internet connection.

Thanks for helping, it means a lot to me!

Regards,
dijxtra

---

### Post by dijxtra on 2008-08-27
OK, we figured out that if we boot Windows, connect to the Internet and then reboot to Ubuntu - everything works. But, if connection wasn't established on Windows - not Internet. Any ideas where to look for problems?

---

### Post by dmizer on 2008-08-27
Check the USB power settings (or other settings) in the bios. I had this problem with a wireless mouse. I was never able to solve that problem though ...

Sorry, your earlier post slipped through my backlog :(

---

### Post by dijxtra on 2008-09-06
Hm, right, that didn't help since I understand noting about this settings.Can I solve this issue by buying a new PCI wireless card? Is there a list of wireless cards that work with Linux?

---

### Post by dmizer on 2008-09-06
> **dijxtra said:**
> Can I solve this issue by buying a new PCI wireless card? Is there a list of wireless cards that work with Linux?
A PCI network adapter would certainly avoid the USB issue.

Right at the top of the Networking and Wireless forum, "Supported wireless cards list" is one of the stickies: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

