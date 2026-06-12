---
title: "Will not detect wireless device"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by uakronkid on 2007-05-07
Hello.  I just installed Ununtu 7.04 for the first time today.  The install went fine and everything was going according to plan.  When I went in to set up my wireless network connection so I can download updates, get drivers, ect. I noticed that it only shows my wired LAN and the modem.  No wireless device at all.  I'm still pretty new to Linux, and have no clue as to what is wrong.  My wireless device is it's own PCI card inserted into the motherboard.  It's an HP 802.11 b/g made by Atheros.  The Google searches have done nothing to help.  Please tell me what the deal is, and how to fix it.  Should I find drivers online and hope that will let the system detect it?  Or is it more complicated than that.  Thanks for the advice.

---

### Post by spd106 on 2007-05-08
The best way to tell is to open a terminal (command prompt) and run this command
```
lspci
```

If it lists an Atheros card then go to this website and see if it is supported [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

If it is listed on the madwifi site then it you will need to check that the linux-restricted-modules package has been installed, which you can do in the Synaptic Package Manager.

---

### Post by Tysn37 on 2007-05-28
I am having the same problem, except when I had version 6.10 it worked fine. it detected my wireless card then, and now with 7.04 it does not.

---

### Post by BatteryCell on 2007-05-30
Same problem here, even though lspci is showing the card:
```

...
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
...

```

---

### Post by Denis Clijsters on 2008-03-02
any solutions found?

My card was working till yesterday. lspci show my card but iwconfig gives me:

lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

Yes, I installed vmware and since then i've lost wlan0 What can I do?

Running on Hardy wtih HP TC1100 wlan = ipw2100

---

