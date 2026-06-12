---
title: "IP Address range and port scanning"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Rtedmonston on 2014-02-01
Anyone know of a good tool that will work I can use to do this with? It's for an assignment, we were given a range of ip addresses to scan (71.180.144.0 - 255.255.255.0 specifically) and send in our results, problem is I can't find a scanner to do it in the alloted time we have, AngryIP scanner would take days, I've tried Nmap and it just crashed, I'm about to try with BackTrack as a last resort and see what happens. I've tried several other tools and can't figure out how to do it, netcat via command line maybe? I couldn't find any instructions how to scan a specific range anywhere. 


Can anyone help?

---

### Post by Lars Noodén on 2014-02-01
nmap should be the right tool to do the job and shouldn't crash.  Did you install it from the software repositories?  Another variant would be Zenmap, but that is just a GUI for nmap.  If you have installed nmap from the repositories and can consistently get it to crash then you have found a bug which could be reported.

---

### Post by Rtedmonston on 2014-02-01
Maybe I'm doing it wrong? I installed nMap from software center, should I go back and do it through the repositories? Whenever I enter that IP range as I've shown above in the field and tell it to scan it dies on me, consistently, so does zenmap.

---

### Post by mikewhatever on 2014-02-01
May be you can show us the exact command.

---

### Post by steeldriver on 2014-02-01
Are you sure the second part (255.255.255.0) is not intended to be a netmask i.e. the range is 71.180.144.1 - 71.180.144.254? That would be more likely I think HINT: you can use [CIDR notation]("http://en.wikipedia.org/wiki/CIDR_notation#CIDR_notation") [wikipedia]

---

### Post by Rtedmonston on 2014-02-01
I got Nmap to work through command prompt, installed from repositories. perhaps that is the subnet mask, it wasn't specified, how would I scan that range using Nmap via terminal?

---

### Post by SeijiSensei on 2014-02-01
Nmap allows you to specify a range of IP addresses or a "CIDR" subnet address.  These two are equivalent:
```

nmap -sP 192.168.1.1-254
nmap -sP 192.168.1.0/24

```
Note that the .0 and .255 addresses are reserved as the "network" and "broadcast" addresses respectively.

That runs a ping scan and can be executed by any user.  To scan ports on remote machines requires that you run nmap as the root user with sudo:
```
sudo nmap -sT 192.168.1.0/24
```
runs a simple TCP scan against all the machines in that subnet.

---

