---
title: "Firewall appliance"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by ubuEsq on 2014-04-07
I have several Ubuntu servers used as Domain Server and VirtualBox Hosts. The Client Machines are mainly Windows. The setting goes : 
ISP ==> Firewall(bare Metal) ==> then Server, physical and virtual machines; no virtual LAN

I want to go one step further and obtain :

ISP ==> VM Guest as Firewall (pfSense, IpCop , Ubuntu + ufw, or whatever)  ==> then Server, physical and virtual machines; no virtual LAN

So I have Host and Guest using eth0 in the Internal domain and the outside ISP through a modem plugged in eth1. The virtual firewall is bridged to eth2. I have no problem with that.

Now the Question: 
How do I make sure all the traffic on eth1 goes to the firewall and the firewall only; i.e. the host wont see or be seen through eth1 ?

The host is the latest LTS version of Ubuntu

TIA

---

### Post by TheFu on 2014-04-07
VirtualBox isn't up to this task, IMHO. Xen or KVM are more stable and less overhead. These are servers, right?

Making a firewall into a VM is a really bad idea - just because it is possible, doesn't mean it is a good idea.  Firewalls should be single purpose dedicated devices. This is opinion. Virtual machines DO have hidden security considerations that very few people understand. The hostOS will always see all traffic - it must. 

Use pfSense - avoid the Linux-based firewalls if security really matters. A firewall that can do SPI in both directions might be handy. But it really depends on what you are trying to protect.

Or trust what most people claim (without proof) about VM security and do what you like. Your plan sounds bad to me.

---

### Post by SeijiSensei on 2014-04-07
I'd just buy a [decent router with dd-wrt or Tomato support]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190") and use that ahead of the servers.

---

