---
title: "IP address assignment"
date: 2022-02-10
forum: Networking &amp; Wireless
---

### Post by abarson on 2022-02-10
Greetings!
I'm no stranger to networking and IP, but I'm just learning Ubuntu and I'm in a situation where I need a bit of guidance.
I've got Ubuntu installed on a dedicated laptop, along with Oracle Virtualbox in order to create a "network" of Arista switches. As far as IP allocation goes, 
vboxnet0 = 10.10.10.1/24 ("ip -br address" = DOWN, but responds to ping? net-tools is already installed)
Arista1 = 10.10.10.2/24
Arista2 = 10.10.10.3/24
Arista3 = 10.10.10.4/24

What is the best way to configure a loopback interface in order to "remotely" manage these virtual devices?

---

### Post by TheFu on 2022-02-11
bridge mode.
The virtualbox documentation has a full chapter about this and it is extremely clearly written (which is odd). ;)

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by abarson on 2022-02-11
@TheFu Thanks for the link, I've got some reading to do.
I figured this was a Ubuntu issue, not Virtualbox.

---

### Post by TheFu on 2022-02-11
> **abarson said:**
> @TheFu Thanks for the link, I've got some reading to do.
I figured this was a Ubuntu issue, not Virtualbox.

Nope. It is a network architecture tied into a virtual machine issue.

There is the LAN connection for the hostOS. Then there are multiple ways that each VM can connect (or not) to the hostOS.  In general, I use Linux bridges to connect all VMs to the same subnet as my VM hosts. This makes life easier, but for someone hoping to learn layer2 switching, there are probably complexities beyond my knowledge that will be important.  Hence, why the options in the virtualbox manual are important to consider. It isn't really that much reading. If you understand bridges, routing, and subnetting, nothing new, just that they are possible with a checkbox in vbox.

I haven't used vbox in about a decade. I prefer the enterprise hypervisor that is part of the Linux kernel, kvm/qemu.  However, KVM doesn't bring any fancy networking GUI checkbox with it. We are expected to use native tools to setup whatever we need.  As you can imaging since pretty much every router in the world used at home runs Linux, there isn't anything in networking that Linux cannot do, if you have the skillz.  Not really good for someone new to Linux to attempt, but if someone has a few network design/architecture courses already, it should be easy, since you'll already know what is possible. Just figuring out the tools and commands remains. I always have to look up the bridge commands, because once I set it up, I don't really have to deal with it for 4+ yrs again.

---

