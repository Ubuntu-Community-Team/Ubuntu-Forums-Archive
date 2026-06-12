---
title: "DELL Latitude E6420, ubuntu 14.04 - Wifi adapter not detected"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by Michael_Delatte on 2016-02-04
Hello,

I ve just installed Ubuntu 14.04 LTS on a DELL Latitude E6420 laptop, everything ok except the Wifi adapter :(.

No drivers found on Dell Support for this version of Ubuntu.  The Service Tag is [FONT=Trebuchet MS]86C4DS1.

The wifi network adapter is a [/FONT]EMEA Dell Wireless 1530.

Is it a know issue, is there a fix ? 

thank you 
Michael

---

### Post by Hadaka on 2016-02-04
Hi,please open a terminal ctrl/at/t and then copy and paste
```
lspci -nnk | grep -iA2 net
rfkill list all
```
post the output..
thanks.

---

### Post by Vladlenin5000 on 2016-02-04
The results from the above commands are what we really need in order to start troubleshooting. Those will inform us about the actual hardware.
Unfortunately Dell (like ACER and others) has the bad habit of modifying the firmware of certain components often for no other reason than to masquerade the real hardware underneath so on the surface it looks like they - Dell - are manufacturing lots of things. They aren't... Therefore,
> [FONT=Trebuchet MS] The wifi network adapter is a [/FONT]EMEA Dell Wireless 1530.
isn't useful.

Consider this just a side comment. You have the Richard Dawkins of Networking helping you already. I can try to help too but considering that I'm just a middle-schooler compared to Hadaka, my eventual contribution won't probably add any value. I couldn't help but comment though because I hate this practices by some vendors that are bad to customers like us.

---

### Post by justinwpartain1 on 2016-03-10
Not OP, but I think I'm having the same problem and would love to see what kind of solutions there are. Laptop is also E6420 and wifi is not working.

$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Dell Device [1028:0493]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Wireless 1530 Half-size Mini PCIe Card [1028:0011]
    Kernel driver in use: bcma-pci-bridge
$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by Bucky Ball on 2016-03-10
> **justinwpartain1 said:**
> Not OP ...

Best to observe or post your own thread. Actively posting for support in this thread will be both confusing and unfair to the original poster.

See what happens and if it works for you, great. If you find a fix or something that might help here and can throw it in here, great. If not, post a new thread (or do that anyway). Good luck.

---

### Post by justinwpartain1 on 2016-03-11
I needed to update to their propriety driver through the Dash>Additional Drivers>Additional Drivers tool. Then after trying to turn on/override the hard switch for Wireless LAN through BIOS, I finally switched the hardware switch on the right side of the laptop :o Wireless is working for me now.

---

