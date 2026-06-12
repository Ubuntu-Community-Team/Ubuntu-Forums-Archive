---
title: "Dual Boot Windows 7 and Ubuntu 12.04 Internet Connection Issues"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by wishnwonder on 2014-01-25
:confused:Someone Please Help...I am able to connect to the internet when booting under windows 7 but when I boot under Ubuntu 12.04 neither my wireless netgear n300 adapter WNA3100 is detected nor is my modem made by Quest.  I am using a MSI Z87 gd65 gaming motherboard with Ethos Killer Ethernet card. ... Ubuntu is an Awesome OS and I hope to be up and running very soon..any advice on any scale of expertise would be greatly appreciated.

---

### Post by Bucky Ball on 2014-01-26
Hi and welcome. Could you open a terminal and copy/paste this into it, please:

```
sudo lshw -C network
```

Post back the output. That will give us a better look at what you have going on. ;)

Unfortunately, for the moment, these cards are notoriously tricky to get working in Ubuntu. That's the bad news. See here:

[https://duckduckgo.com/?q=WNA3100+ubuntu+12.04](https://duckduckgo.com/?q=WNA3100+ubuntu+12.04)

* Here is a solved thread assisted by one of our resident wireless gurus chilli555:

[http://ubuntuforums.org/showthread.php?t=2055145](http://ubuntuforums.org/showthread.php?t=2055145)

---

### Post by wishnwonder on 2014-01-26
Thank you for your response..I will do that right now..

---

### Post by Bucky Ball on 2014-01-26
In case you missed it (just added to my last post) ...

* Here is a solved thread assisted by one of our resident wireless gurus chilli555:

[http://ubuntuforums.org/showthread.php?t=2055145](http://ubuntuforums.org/showthread.php?t=2055145)

---

### Post by wishnwonder on 2014-01-26
voltron6@ubuntu:~$ sudo lshw -C network
[sudo] password for voltron6:
  *-network UNCLAIMED
           description: Ethernet controller
            product: Atheros Communication Inc.
           vendor: Atheros Communications Inc.
           physical id: 0
           bus info: pci@0000:03:00.0
           version: 13
           width: 64bits
           clock: 33MHz
           capabilities: pm pciexpress msi msix bus_master cap_list
           configuration: latency=0
           resources: memory:f7900000-f793ffff ioport:d000(size=128)
voltron6@ubuntu:~$

---

### Post by wishnwonder on 2014-01-27
I've decieded to purchase a PCI Express Ethernet Card 
[TABLE]
[TR]
               [TD] [ TP-LINK TG-3468 10/100/1000Mbps Gigabit PCI Express Network Adapter ]("http://www.amazon.com/gp/r.html?R=YBSBVQWRGJY7&C=3T5MUR8F9569O&H=RGWXYK0FKOD112LXZ7MZDHHAXBGA&T=C&U=http%3A%2F%2Fwww.amazon.com%2Fdp%2FB003CFATNI%2Fref%3Dpe_385040_30332200_pe_309540_26725410_item") [/TD]
[/TR]
[/TABLE]
it Says in the reviews on Amazon.com that it connects to Ubuntu with no problem..I'll have it in a couple of day and will report with the results...Sometimes it's just better to find the hardware that supports the cause of the OS..

---

### Post by wishnwonder on 2014-02-01
Just recieved the TP-Link model TG-3468 Gigabit PCI Express Network Adapter from Amazon.com...downloaded Realtek drivers from the CD on to the Windows 7 portion of my boot drive and worked like a charm...Linux Ubuntu 12.04 didn't even need the drivers to be installed just plug and play for under $20 bux..Highly recommended if your serious about getting up to speed with Linux but don't have the time to "Trouble Shoot" a device that may take up a whole lot of productivity time away from your projects.

---

### Post by Bucky Ball on 2014-02-01
Good you got this working. Please mark the thread as solved to help others. Instructions in my signature. Enjoy! ;)

---

### Post by benmcneil102 on 2014-02-01
Would all tp-link cards have the same effect I was looking at this one, I'm having a simlar problem

[http://www.amazon.com/dp/B0079XWMEI/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=1FQKAP4SO7278&coliid=I1J7B27G8OGBQU](http://www.amazon.com/dp/B0079XWMEI/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=1FQKAP4SO7278&coliid=I1J7B27G8OGBQU)

---

### Post by Bucky Ball on 2014-02-01
TP-link mostly works out of the box, but do some research. Check the first stanza in my signature. It is VERY easy to find a wireless dongle that works with Ubuntu. ;)

If you're really having issues with this, post a new thread with a descriptive title rather than tagging onto this one (someone else's thread, question, and thread title).

---

