---
title: "Wireless in laptop not working"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by kramer65 on 2011-07-25
Hello,

I am currently running the live CD of Ubuntu 11.04 to see if the wireless card works on this laptop. Unfortunately it doesn't work out of the box. When I run "lspci -v" I see the following:

```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1021
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
```

I guess this is the same as the first one listed on [this page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel"), so it should work, but unfortunately it doesn't.. :( (that is, it doesn't find any networks, where my normal pc finds about 20 wireless networks in this house..)

Could anybody help me out on how to get wifi working on this laptop? All tips and hints are appreciated!

---

### Post by roger_1960 on 2011-07-25
Hi

Based on the driver its using, it would seem to be the 7th one listed on the page rather than the first.  In that case, it needs a backport and I'm not sure you can do that when running a live CD - I think you have to install it first.

Roger

---

### Post by kramer65 on 2011-07-25
ok, in that case I install it first.

I don't really know how to "install backports" (I don't even know what it is to be honest). Any idea how I could do this..?

---

### Post by roger_1960 on 2011-07-25
Hi

I think now that the info is a bit out of date.  Have a look at this link:

[http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/](http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/)

Should help hopefully

Roger

---

### Post by Mcjohnnson on 2011-07-25
Is ethernet working?

After installing open a terminal and update your packages.

```
sudo apt-get update

```
```
sudo apt-get upgrade
```

It may be that support for you wifi comes with these updates.

---

### Post by moorhead98 on 2011-07-25
I'd bet you have to install it first. I've tried live Cd's before (not 11.04 though) and a handful of things didn't work on it, but after installation, i could fix them. So if you can, install it. Then see if there is a problem and diagnose it. That should make it easier to fix it if necessary.
Also make sure that you didn't hit an external switch on the laptop that turned off wi-fi 
I know that's probably not the problem, but just make sure ;)

---

### Post by kramer65 on 2011-07-25
> **moorhead98 said:**
> 
Also make sure that you didn't hit an external switch on the laptop that turned off wi-fi 
I know that's probably not the problem, but just make sure ;)

:shock:  :oops:    #-o Excuse me. Sometimes things are so simple..

Thanks for all the help anyway! =D> :KS :P  :-\"

---

