---
title: "What Gives??"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by superyounan1 on 2007-03-25
my /etc/network/interfaces looks like this:

[INDENT]
iface rausb0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid "Younan"

auto rausb0[/INDENT]

but when I turn on my computer, I connect to 192.168.1.*100* or 192.168.1.*105* instead, is it going through the DHCP even though its supposed to have a static ip? This is problem because i have ports forwarded and my laptop sometimes has the other IPs.

I think i tried taking out the "auto rausb0" since I'm not sure what that does, and in some code snippets online, the auto field isnt there for a static ip, but it just pops up again.

---

### Post by lloyd_b on 2007-03-25
Suggestion: In a terminal window:
```
sudo /etc/init.d/networking restart
```
This will stop and restart the network.  Doing this will display info that may help diagnose the problem (for instance, if it's calling DHCP, it should be clearly visible in the output from this command).

Lloyd B.

---

### Post by Mr. C. on 2007-03-25
I am not certain of this, but it is possible that an implementation could attempt to use DHCP when an IP address is already is currently in use.  Have you verified that .101 is not in use?

(when you say "I connect to", I presume you mean "This IP address was assigned configured:")

Check /var/log/syslog for DHCP messages.

Curious, are you also certain that .101 is *outside* the range of valid DHCP addresses.   Your system being assigned 100 or 105, which bracket your choice of 101 seems to indicate you are selecting a static IP within the same range as your router's reserved dynamic IP range.

MrC

---

### Post by superyounan1 on 2007-03-26
hmm, i never realized that you shouldn't set a static IP address that is within the DHCP range - I've been doing it in windows for many years and never had a problem, more specifically, my routers never tried to dynamically assign an ip via DHCP that I was using as static.

my current range is 192.168.1.100 ~ 192.168.1.149

Typically what I need to do to get the IP i need, once I log on and get assigned a dynamic IP (always seems to bee either 192.168.1.100 or 192.168.1.105 for some reason, I've never seen it give me anything else), is to go to the networking interface tool in ubunutu, disable the wifi card, and re-enable it. This always gives me the appropriate IP, but I would still not have access to the network, I need to tell it my ssid with the following:


```
sudo iwconfig rausb0 essid "MyRoutersName"
```


at which time I have complete access.

I will follow the recommendation to run this command next time i restart into ubuntu to see what exactly is happening, maybe it will help

```
sudo /etc/init.d/networking restart
```

but I've found that when I do this:

```
sudo ifconfig rausb0 inet down
sudo ifconfig rausb0 inet up

```
to restart the device, it has no effect, I stay with the original, dynamic ip.

Sorry, i think this message is a bit hard to follow

---

### Post by Mr. C. on 2007-03-26
The DHCP protocol suggests that a DHCP *should* attempt to determine if an IP address it offers is in use.  Most of the better DHCP implementations do this, but not all.  Yours does, and that's why you have never had a conflict.

In addition, DHCP servers *must* retain a client to IP mapping of previously assigned IPs.  This is why you often get the same address over and over.

DHCP servers own the IP range given to them - never use an IP from that range; it is asking for trouble.

I think you mean "ifup / ifdown", not inet up/down.

Restarting the network via /etc/init.d/networking does exactly ifdown -a ; ifup -a, excluding loopback.

MrC

---

### Post by dawv on 2007-03-26
well your *first* problem is your looking at this the wrong way... sorta....


iface rausb0 inet static <-----you** are** connected as static.....
address 192.168.1.101<-----this is _***YOUR***_ IP address, not what your connecting too (routers assighn this so they know exactly which computer in the network to send certain packets of data to.
netmask 255.255.255.0 
gateway 192.168.1.1<---- now **THIS **is what your connecting too
wireless-essid "Younan"<---dunno, I'm a n00b

---

### Post by dawv on 2007-03-26
idea... try making your static IP be 192.168.0.9

wild guess... i guess

---

### Post by superyounan1 on 2007-03-27
> **dawv said:**
> well your *first* problem is your looking at this the wrong way... sorta....


iface rausb0 inet static <-----you** are** connected as static.....
address 192.168.1.101<-----this is _***YOUR***_ IP address, not what your connecting too (routers assighn this so they know exactly which computer in the network to send certain packets of data to.
netmask 255.255.255.0 
gateway 192.168.1.1<---- now **THIS **is what your connecting too
wireless-essid "Younan"<---dunno, I'm a n00b

thanks for the reply, but that is from my /etc/network/interfaces file - these are the settings that I *WANT*, or what I've configured it to do when the wifi adapter starts, its NOT my network status. So my computer is supposed to connect according to these settings, but it doesnt, i have to fiddle with it despite having it configured properly (or so i thought). 

Thanks though

---

