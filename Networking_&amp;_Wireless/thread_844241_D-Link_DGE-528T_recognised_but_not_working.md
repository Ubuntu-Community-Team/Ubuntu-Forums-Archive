---
title: "D-Link DGE-528T recognised but not working"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by jedi_monkey on 2008-06-29
Hi Everyone 

I have looked at loads of forums to try to solve this issue but none seem to have given a working solution to my problem.

I'm having problems trying to get Ubuntu 8.02 (32bit) to recognise my D-Link DGE-528T as a network adapter (Wired).

Unlike some problems it seems (looking at the dmesg output) that my network card is being recognised:

[FONT="Courier New"]r8169 Gigabit Ethernet driver 2.2LK loaded[/FONT]

But then it all goes wrong on next next two lines:

[FONT="Courier New"]r8169 0000:00:0c.0: could not request regions

r8169: probe of 0000:00:0c.0 failed with error - 16[/FONT]

I'm not sure what that means.

Any ideas?

My motherboard is a Gigbyte GA-71xE4

I've tried to install the drivers but they are for kernal version 2.4 so a bit out of date (and won't run anyway)?

Also it has been noted on one of the document pages that the network card gets recogised automatically without any need for drivers.

Here is some other info to help diagnose what could be wrong:

[FONT="Courier New"]
lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=64 mingnt=32

--------
ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65500 (63.9 KB)  TX bytes:65500 (63.9 KB)

[/FONT]

I also do not have the file: 

/etc/iftab  


Thanks in advance

---

### Post by kaingeo on 2008-10-01
I have set an Ubuntu LTSP server with the same network card (D-link DGE-528T). It's working for some time and then its disconnecting and all my network crashes. One friend told me that it uses the realtek chip that has many issues. I solve my problem by buying a new card. If you find anything let us know.

---

