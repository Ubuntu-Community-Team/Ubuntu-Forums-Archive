---
title: "Internet on my VirtualBox Stopped Working"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by punkiishmob on 2009-01-14
Well, there were a series of network-based events I messed around with, and now I finally have everything running fine.

-Installed Firestarter
-Set up samba
-Samba and Firestarter didnt like eachother, so I uninstalled Firestarter
-Installed Moblock

None of these apps are running right now, but the samba server. I connect to my VM running Windows XP, and the network/internet suddenly stopped working. I've tried switching different types of network adapters but no luck... could these programs have messed up my internet in a VM?

---

### Post by Peter09 on 2009-01-14
Do ifconfig in your VM, see if its sees an NIC.

---

### Post by niteshifter on 2009-01-14
Hi,

You'll probably get better results moving this into the Virtualization area and tell us:
What version of Ubuntu you're using.
What version of Virtualbox you're using.
How the Guest OS (XP?) networking is setup: NAT, Host I/F, Virtual, etc.

---

### Post by superprash2003 on 2009-01-14
are the machines able to ping each other? or ping the router?

---

### Post by senor_smile on 2009-01-15
Hi, I have a virtual machine in virtualbox 2.10 that stopped working as of this morning as well.  I have two other virtual machines that are working fine however.  

Host: ubuntu 8.10 32 bit
guest: windows xp pro 

I have one virtual nic as NAT, another as HOST(bridged networking). 

Another virtual machine running xp pro as well works just fine. It is set up with NAT.  I have tried restarting guest and host.  I have tried disabling and re-enabling nic's.

---

### Post by jre on 2009-01-17
I guess MoBlock is blocking your traffic. Check /var/log/moblock.log to see if this is the case. AFAIK VirtualBox uses the iptables FORWARD chain. So you can allow some traffic in this chain. Have a look at /etc/moblock/moblock.conf to see which options are available and then make your changes in /etc/default/moblock.

Quick solution: If you want Moblock to only check your Linux traffic, but not your VirtualBox traffic, then you might set in /etc/default/moblock:
```
REJECT_FW="RETURN"
```
This way the traffic still gets checked (also in the forward chain), but no further measure will be taken for matched packets. (Curretnly matched packets would be DROPped).

---

