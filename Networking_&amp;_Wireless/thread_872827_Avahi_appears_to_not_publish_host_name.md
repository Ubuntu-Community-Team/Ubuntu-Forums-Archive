---
title: "Avahi appears to not publish host name"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by praeceptum on 2008-07-28
OS: 8.0.4 LTS

Even after stopping the Firestarter firewall I can't ping my Ubuntu workstation from the LAN.

"ping mymac.local" works on the Ubuntu box named "ubuntustation". "ping ubuntustation.local" works on the Ubuntu box. "ping ubuntustation.local" results in

ping: cannot resolve ubuntustation.local: Unknown host

when run on my Mac (mymac.local). If I do "ping 10.101.30.42", it works, however.

Both hosts are plugged into the same dumb network switch. Any ideas, why this might not be working?

---

### Post by praeceptum on 2008-07-29
It appears to be intermittent. Currently, I can ping the Ubuntu box via its zeroconf name.

---

### Post by krismatth3 on 2008-08-19
I have this same problem too. 

Ubuntu machine = zen.local
Mac 1 and 2 = earth.local and jupiter.local
Vista + Bonjour machine = ark.local

When avahi-daemon first starts (on zen), all machines are able to ping zen.local. After about 10 minutes, only zen.local is able to resolve "zen.local". No other machines are. If I restart avahi-daemon, all machines are able to ping zen.local again.

Here's the interesting thing: after 10 minutes, when no external machine can ping zen.local; if zen.local pings itself, other machines are again able to ping it for another 10 minutes or so.

---

### Post by vicaya on 2008-09-17
Any progress on this one?

Have the same problem on fedora 9 inside a VM as well. restart avahi-daemon will make the local binding visible for a few minutes and then the registration seems to disappear.

---

### Post by Brian Vaughan on 2008-10-21
This sounds like the difficulties I've been having.

I have a desktop running Ubuntu 8.04, which is connected to a LAN via a wireless card -- a Linksys WMP300N, with the Broadcom 4329 chipset. My family members are using Macs, two of them laptops and one an old desktop, all running OS X, though not all the same version. The Avahi services running on my Ubuntu desktop -- Rhythmbox's shared music library via DAAP, and the shared CUPS printer -- disappear intermittently from the OS X machines, and likewise, the services on the OS X machines also intermittently disappear. Also, the OS X machines don't seem to notice any shared folders via Avahi or Samba, though they can sometimes connect if I type in the URL directly into Finder's Connect to Server dialogue. I haven't been able to tell if restarting avahi-daemon or rebooting helps consistently.

I am transitioning from Windows XP to Ubuntu, and I had pretty much the same trouble in Windows XP -- shared music libraries would disappear, and so would the shared printer. The recent Linux kernel upgrade included the Broadcom STA driver, which made for an enormous improvement in wireless connectivity over the ndiswrapper setup I'd used previously, and I notice no trouble connecting to the Internet through the wireless router now.

I seem to have the most trouble with one laptop in particular, which happens to be running the latest version of OS X. I'm guessing that somehow its firewall is interfering with Avahi/Bonjour, so my next project is to find out how to disable its firewall. Our wireless router is firewalled already, so firewalls on the computers within the LAN are mostly redundant.

---

