---
title: "Exactly how should I respond to VMWare server install to properly config my network?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by anotherlinuxnewbie on 2009-08-06
I'm running Ubuntu 9.04 on my laptop and last night went through the process of installing VMware Server.  But when it asked me about how to configure the network, I didn't know what I was doing, and the result was that it kept my laptop from being able to get to the internet (ironically, the VM could get out just fine).  ifconfig showed vmnet1 with the ip 192.168.0.1, which is the address of my router (!), so I figured that was the problem.  There were no other "vmnet" records listed in ifconfig.

So here's all I want to do: allow the virtual machine to connect to my home network (and from there, out to the web) just like any other machine via the wireless adapter in my laptop,  without interfering with the network operation of Ubuntu. 

If anyone can give me explicit instructions on how to respond to the prompts during the vmware install in order to achieve this, I'd be most grateful.  The rest of the process went fine, so all I need is that one little part.  My wireless card is eth1, if that helps.

Thank you!

---

### Post by anotherlinuxnewbie on 2009-08-06
Nevermind, figured it out: when asked for which adapter for "bridged", I entered eth1, and said no to making more connections (e.g., hostonly and nat).

---

