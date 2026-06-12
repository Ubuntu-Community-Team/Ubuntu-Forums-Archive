---
title: "eee 1000 wireless not working"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by terry f on 2008-07-20
does any one know how to get the wireless working in Ubuntu?  I can't get it to work.  Does any one know how to get it to work.

---

### Post by terry f on 2008-07-20
any one?

---

### Post by vrazix on 2008-08-06
Uh oh! I'm running an ubuntu install on my EEE 1000 right now.

If driver support for the wireless isn't there yet... how can it be created? :x

---

### Post by chris09 on 2008-08-06
ok man just to make sure there are buttons on the keyboard that you have to press(not the keys) after you have tried getting signal from your radio i.e.the button might say connect channel located on the botttom


or if the ports are ps2 and not usb you need te restart the computer and if that doesnt work you need to check your lspci and check your slot. if that doesnt work just post another

---

### Post by vrazix on 2008-08-06
Wireless card is internal; blue wireless light is on (the one that sits next to drive activity/power LEDs, etc).

I ran lspci and

01:00.0 Network controller: RaLink Unknown device 0781
03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

---

### Post by Chonnawonga on 2008-08-07
Try this guide: [http://www.ubuntu-eee.com/index.php5?title=EeePC_901]("http://www.ubuntu-eee.com/index.php5?title=EeePC_901")

You'll need a working Windows install somewhere to extract the driver from your XP Support CD.

---

### Post by comradekingu on 2009-01-03
You need the kernel from [array.org]("http://www.array.org/ubuntu/setup.html") Works with 8.04 and 8.10.
Edit: I should say that the kernel from array.org is now redundant and old, support is in the mainline kernel.

---

