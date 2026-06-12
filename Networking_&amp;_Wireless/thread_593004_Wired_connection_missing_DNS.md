---
title: "Wired connection missing DNS?"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Sparkster185 on 2007-10-26
Hey all,

I have KUbuntu 7.04 installed on my desktop (using GNOME desktop, wired) and Kubuntu 7.04 installed on my laptop (wireless).

All of the sudden, my desktop fails to get an internet connection.  I cannot view web pages and I cannot check my email. I'm guessing I'm having DNS issues, specific to my desktop (ethernet).

What's weird is that my laptop works perfectly fine.  I can browse the web (writing this from my laptop, actually) and do everything just fine.

What's even weirder, is that earlier in the day, everything was working just fine.  Later on, I tried to open a URL in Firefox and it failed to find the host.

I've tried doing 'dig' commands on various domain names on my desktop and I get 'timed out' errors.

Any ideas will be appreciated.

EDIT:

```

clarkb:$ ifconfig eth0
eth0 Link encap: Ethernet  HWaddr <blah>
inet6 addr: <hex>
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes: 32205 (31.4 KiB)
Interrupt: 17

```

---

### Post by uhlive on 2007-10-26
You have no ip address... according to what you posted

---

### Post by Sparkster185 on 2007-10-26
I suspected that as well.  I've tried re-booting my PC, as well my cable modem and my router (using all permutations).  Nothing helped.

I've tried doing ```
sudo ifconfig eth0 down 
``` followed by ```
sudo ifconfig eth0 up
```, both before all components were shut down and after all of them were shut down.

I notice that I see a "inet6 addr" in my "ifconfig eth0" output, but nothing related to "inet4".

---

### Post by FXEF on 2007-10-26
Sparkster185

Power cycle your router, then shutdown PC and re-boot. Hopefully you'll regain your connection.

FXEF

---

### Post by Sparkster185 on 2007-10-26
I've already tried unplugging both my router and the modem, waiting ten seconds and powering back on, with no results.  Did you mean something different?

---

### Post by FXEF on 2007-10-26
> **Sparkster185 said:**
> I've already tried unplugging both my router and the modem, waiting ten seconds and powering back on, with no results.  Did you mean something different?

That's right. Did you reboot your computer?

FXEF

---

### Post by Sparkster185 on 2007-10-27
I most certainly did.

I had to manually go into my router settings and Release/Obtain DHCP information.  Both machines are working perfectly now.

---

### Post by qbox on 2007-10-27
COOL :D
you help me either :D

---

