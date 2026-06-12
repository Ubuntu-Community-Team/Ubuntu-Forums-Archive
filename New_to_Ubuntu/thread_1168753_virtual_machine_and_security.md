---
title: "virtual machine and security"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-05-24
Hi,

I am running XP virtual box on ubuntu 9.04. Obviously, XP has many security risks associated with it. However, normal programs like firewalls hogs quite a lot of system resources. My question is, is my Ubuntu OS at risk if I don't install a firewall on my virtual machine?

I don't care much for the virtual machine, as I could just replace the HDD image file at any time. The virtual machine and Ubuntu are connectedthrough a type of "network", and XP connects to the Internet through ubuntu . Is it possible for someone with malicious intent to get to my Ubuntu through my XP?

Thanks.

---

### Post by mellowd on 2009-05-24
There is no risk unless you copy infected files from one to the other. And it's very difficult to get a linux virus from the windows box via a file copy. 

The windows box is protected in that virtual machine, it has no way of 'breaking out' into the host system

---

### Post by jimmy the saint on 2009-05-24
It wouldn't be the easiest thing to do, but the virtual machine is operating inside your Ubuntu OS and sharing resources.  There are likely some risks, especially if you create shared folders or bridge the networks so that the virtual machine shows up as part of your network.  I do not have my xp insallation bridged, and I only share one folder when it is absolutely neccessary.  I also created a snapshot of a clean system that I restore frequently, updatint with new software as it becomes neccessary.  That way, if (when) XP catches digital herpes it doesn't stick.


Edit:  Especially if the virtual machine is bridged to your LAN, the attack would not need to break out of the virtual machine.  It could attack your network machines just as if it had attacked a normal XP machine on the network.

---

### Post by eragon100 on 2009-05-24
Yes, it is possible if you share files. The fact that XP connects to the internet via Ubuntu doesn't matter. However, you say you have "connected" them trough "some kind of network". Do you mean you have virtualbox set to share folders between the virtual and the real machine?

If you have, your ubuntu installation would be seen as a normal drive by your virtual windows, in which case automatically spreading viruses may copy themselves to that "drive" from withing your virtual xp installation.

Ubuntu isn't vulnerable to windows viruses, so it doesn't matter directly. You can safely watch an infected video on ubuntu for example, without any risk of damage or spreading the virus.

Conclusion: no it's not a security risk. You might get infected files on your ubuntu installation, but they can't do any harm against this OS.

---

### Post by jimmy the saint on 2009-05-24
I will stress again though that if the guest XP machine is bridged to your network and is attacked, the attacker WILL be able to gain access to other machines on the network through the XP guest machine.  Viruses are not the only danger on the intertubes.

---

### Post by eragon100 on 2009-05-24
> **jimmy the saint said:**
> I will stress again though that if the guest XP machine is bridged to your network and is attacked, the attacker WILL be able to gain access to other machines on the network through the XP guest machine.  Viruses are not the only danger on the intertubes.

Wouldn't it be quite hard to do this, as he/she would have to hack two systems in a row: first xp, and then ubuntu, via the "network". Somehow, this doesn't sound like a very realistic scenario to me, unless the attacker is very motified to attack this specific pc, i.e. if it's the CIA or something. If it's just a criminal looking for bank accounts and such, don't you think he would find an easier target? Security is good, but you shouldn't make it so thigh that it really starts getting in your way, unless absolutely necessary.

---

### Post by jimmy the saint on 2009-05-24
Unlikely yes, but possible.  The security of a network is only as good as its weakest link.  The question was about what risks there were to running xp in a virtual machine.  This is a risk, albeit a small one.

---

### Post by lovinglinux on 2009-05-24
The OP is not asking about virus or any other kind of infection, is actually asking if his Ubuntu machine (host) could be hacked through Windows running on the virtual machine (guest) without firewall protection.

I also would like to know more about this. I tried to learn about the differences between network connections on a virtual machine, but I wasn't able to find very clear explanations.

For instance, I have iptables configured on my Ubuntu machine (host) and use the "Host Interface" network on my virtual machines. So, do I need a firewall on the virtual machine or the "Host Interface" method of networking will be protected by the host firewall?

How easy would be to gain control of the host machine through an unprotected guest machine?

I understand that sharing folders is a security risk in regards to infections, but could it be used t hack the host machine?

---

### Post by Lolli Pop on 2009-05-24
It's quite easy to infect the host machine through an unprotected guest machine. Make sure you don't bridge your connections. And You Should Put The Files you need In The guest machine then disable sharing in the host machine, and everything will be fine!

---

### Post by walterav on 2009-08-31
> May 24th, 2009 08:20 PM
Lolli Pop 	
Re: virtual machine and security
It's quite easy to infect the host machine through an unprotected guest machine. Make sure you don't bridge your connections. And You Should Put The Files you need In The guest machine then disable sharing in the host machine, and everything will be fine! 

Isn't bridging more save? Because both machines have different IP's on the Internet/network on which they are connected. If you don't bridge the GUEST machine it uses the HOST as a NAT, so every internet activity from the Guest by default runs through the host OS.

Considering the HOST is already connected to the internet/unsecure-network and is therefor already vulnerable for hacking, I don't consider it more vulnerable to be hacked by the network connection of the GUEST OS that is on the same network than by a other machine on that network.

Or if you wan't to protect your local network, but thats a different story... 

But thats just speculation.

---

