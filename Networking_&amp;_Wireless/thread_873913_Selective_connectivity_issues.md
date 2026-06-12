---
title: "Selective connectivity issues"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by mpcengineering on 2008-07-29
Hi all,

I have fairly recently having intermittent connectivity issues with my ubuntu install which I can only think must have been caused by a fairly recent update?

Basically, my machine sits on a sizeable network at work of a few hundred machines.  There are a few boxes I have discovered recently that I need access to on a day to day basis that I am suddenly unable to reach via ssh, rlogin or even ping (destination unreachable).  The vast majority of hosts are fine from the exact same machine and the hosts that I cannot access are available to others on the network with no problems.  The DNS name of these unreachable machines is resolved successfully and a traceroute and nslookup works.  There is no firewall operating on my local machine to restrict access afaik:

```
sudo iptables -L -v

Chain INPUT (policy ACCEPT 112K packets, 61M bytes)
 pkts bytes target     prot opt in     out     source destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source destination         

Chain OUTPUT (policy ACCEPT 37858 packets, 11M bytes)
 pkts bytes target     prot opt in     out     source destination
```

```
sudo ufw status
Firewall not loaded
```

I am sure it is nothing to do with the network infrastructure, the switch the machine is connected to or anything else external to the ubuntu box itself, as previously the machines in question have been fully accessible and the only thing that has changed has been regular updates applied to my ubuntu box.  I am pretty new to ubuntu and linux as a whole and I am hoping that it is a pretty straightforward solution, but tbh, I am completely stumped on what the problem might be, does anyone have any clues as to what might be wrong here?

Thanks in advance

Jon :confused:

---

### Post by linux6994 on 2008-07-29
Do you have the same GW and DNS set as the rest of the machines that you need to contact?

---

### Post by mpcengineering on 2008-07-29
Hi, thanks for the reply.  We have 2 networks, my machine sits on the IT network and the boxes I have found so far as I can no longer connect to sit on the production network.  The gateways for my machine and the inaccesible machines are different, but the DNS lists both the IT and production addresses in each case.

There are many other machines with similar setups that also sit on the production network that I can access with no problems...

---

### Post by mpcengineering on 2008-07-30
Bump.  So no-one has any ideas on this one?

---

### Post by mpcengineering on 2008-07-30
Ok, thats interesting, this appears to be a kernel issue.  Booting 2.6.24-20 produces this error, but 2.6.22-14 results in proper performance, I can again ping, ssh, rlogin etc to the previously unreachable machine...

UPDATE:  Ok thats just wierd...now having booted once again into 2.6.24-20, the issue appears to have been sorted.  NO idea why but booting an earlier kernel version and then back to the latest resolved the problem.

---

### Post by mpcengineering on 2008-07-30
Right, finally think I have got to the bottom of this.  The reason booting into a different kernel worked was because that meant that vmware server then needed recompiling for the new kernel version.  So, boot back into the normal kernel version, everything works, recompile vmware server and the issues return....so the vmnet1 and vmnet8 network devices are having some very odd effect on a few select network operations when running vmware server.  I upgraded to the latest version of vmware server, but no joy, but installing vmware player seems absolutely fine, so seeing as I have already created the required images, I have kept server uninstalled and will instead go with player.  V wierd.....

---

### Post by chuckbert on 2008-07-30
This sounds like what I've hit and been trying to solve (remotely which is not particularly easy for network issues!).
[http://ubuntuforums.org/showthread.php?p=5487141](http://ubuntuforums.org/showthread.php?p=5487141)

I have no vmware involvement, but next time I'm actually at the machine I'll try and boot into the previous kernel.

(actually, you don't happen to know a straightforward commandline method - that is via a console - of rebooting with a different kernel do you?)

---

### Post by mpcengineering on 2008-07-30
I know what you mean, problems like this are pretty random and hard to track down most of the time.  Its probably worth u trying to boot an earlier kernel version (sorry I dont know how to do this from the command line!) but also bear in mind this was only significant for me because it effectively disabled vmware thus no vmware network devices were running.  In reality, removing vmware would have had the same affect, but its probably still worth a shot for you, it might show something up for a different reason?

---

