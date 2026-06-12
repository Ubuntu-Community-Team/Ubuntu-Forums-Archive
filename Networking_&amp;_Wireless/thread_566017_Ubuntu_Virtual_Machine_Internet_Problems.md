---
title: "Ubuntu Virtual Machine Internet Problems"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by ArmyOfOrr42 on 2007-10-02
Hey everyone. 

Let me start off by saying I am not a new Ubuntu user, but I am by no means an expert.  Anyway, I'm forced to use vista at school because i have to regularly use NX5 (CAD), matlab/maple, and a few other programs in class that are not compatible with linux, and are too complex to run in a virtual machine.  Ive decided not to try to dual boot because i dont want to risk losing data i already have during the partitioning process because i dont have any of the install CDs for the software i use (School has right to use liscences, and they imaged my laptop with the programs) so it would be a pain in the *** to lose all that.  

I decided to give a virtual machine a try so i downloaded VMware and a VMware feisty fawn image and loaded it up.  it worked beautifully, and surprisingly it runs fast and smooth.  however, there is one problem:

Ubuntu thinks it establishes a network connection, (network bubble pops up saying its connected) but it isn't actually connected to the internet.  There is no IP assigned and i (obviously) can't get on the internet. 

Anyone have a solution to this problem?  its pretty much my only hope for staying with linux!

---

### Post by helgman on 2007-10-03
Did you download VMware Player or VMware Server?

I've never used VMware Player so I'm not sure how networking works in that one but in VMware Server you have a virtual NIC connected to the machine. That NIC can be set to use different virtual network, on of them is using NAT via an interface on the host machine and one of the uses one of the hosts NIC as a bridge. For the NAT network and also the default internal (host only) I'm pretty sure that VMware Server runs it's own DHCP server so the IP address assignment should not be a problem.

After a quick glance at the [documentation]("http://www.vmware.com/pdf/vmware_player200.pdf") (PDF) and [FAQ]("http://www.vmware.com/products/player/faqs.html") for VMware Player gives no hints as to how networking is done in the Player. There is nothing clearly said about networking but there are some hints about it. The main thing is to try and figure out if the Player (if that is what you use) bridges directly over one of you NICs (allowing you to connect directly to the network) or if it uses NAT (making the guestOS share your hostOS IP address). In the first case you should be able to get an IP address via DHCP or you should be able to set a static address. In the second case I guess you'll need to find out what network address the Player uses for the virtual network (but that should really be in the documentation then, if you don't tell it during installation).

Reading the long part about VMware Player makes me wonder how it really works. It's not at true virtualization platform, but it can take machines created in VMware Server - then it must be able to support the network settings made there.

If I don't make any sense please let me know and we'll try it again, also please do tell if you are using VMware Server or VMware Player.

Regards,
Helgman

---

### Post by ArmyOfOrr42 on 2007-10-03
Ok, i am using Player, and i found out that it was trying to use a bridged connection, which for some reason wasnt working.  i switched it to NAT and its working now!  

Thanks for your help

---

