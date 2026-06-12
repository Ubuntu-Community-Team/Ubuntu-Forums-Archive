---
title: "Out Of Network IPs"
date: 2015-11-08
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2015-11-08
I'm just curios on how to get out of network IPs that are on your computer.  I'm using Ubuntu 15.10 and I know about using arp-scan command on the Terminal to get internal IP's, but was wondering how to get external IP's?  I know on Windows in the Command Prompt you just do a netstat -an | find /i "established", but was wondering how you do the same on Ubuntu!

---

### Post by The Cog on 2015-11-08
Sorry, but what are you trying to find out? 
netstat -an | find /i "established" on windows will just list the current connections to/from the PC. The Linux equivalent would be
```
netstat -ntu
```
the arguments mean numeric (not names), tcp and udp.

Arp scan is more for discovering what IP addresses are currently connected to your local network, whether or not they are making connections to your PC.

---

### Post by shane_faulkinbury2 on 2015-11-08
But arp-scan gives you 192.168.1.X, I want the originating IP!

---

### Post by The Cog on 2015-11-08
What do you mean? I don't understand what you are looking for. Spell it out, like to an idiot.

---

### Post by shane_faulkinbury2 on 2015-11-08
Sorry, I don't want internal network IPs like 192.168.1.1 I want incoming external IPs like 76.288.132.72!

Like Google's IP!

---

### Post by matt_symes on 2015-11-08
Hi

You want the external IP addresses of ESTABLISHED TCP and UDP connections ?

You are a bit unclear. Assuming this is the case then try this. (You can copy and paste it into the terminal)

```
netstat -ntu | awk '/ESTABLISHED/{print $5;}'
```

ESTABLISHED is upper case above.

Kind regards

---

### Post by shane_faulkinbury2 on 2015-11-08
Thanks, that's exactly what I wanted!  Man I have a ton of IPv6 IP's on there!

---

