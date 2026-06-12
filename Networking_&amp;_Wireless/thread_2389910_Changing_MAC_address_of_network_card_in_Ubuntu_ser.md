---
title: "Changing MAC address of network card in Ubuntu server (17.10)"
date: 2018-04-23
forum: Networking &amp; Wireless
---

### Post by user_of_gnomes on 2018-04-23
I just cloned a virtual machine and told it to generate a new MAC address but Ubuntu still thinks I'm on the old MAC address. 
This conflicts with the way my router dishes out reserved addresses and I'd like to fix that.
 
How do I permanently change the MAC address?

Thanks.

---

### Post by TheFu on 2018-04-23
That is set by the hypervisor hardware settings for the NIC. Which are you using?

---

### Post by user_of_gnomes on 2018-04-24
> **TheFu said:**
> That is set by the hypervisor hardware settings for the NIC. Which are you using?

VirtualBox 5. Linux Ubuntu stil thinks the old MAC address is in use despite VirtualBox claiming otherwise.

[ATTACH=CONFIG]279428[/ATTACH]

```
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:23:4d:66 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.3/24 brd 192.168.1.255 scope global dynamic enp0s3
       valid_lft 86339sec preferred_lft 86339sec
    inet6 fe80::a00:27ff:fe23:4d66/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by TheFu on 2018-04-24
Well, those aren't the same devices. I'd check that you are using the correct device inside the VM.  Wouldn't hurt to check that udev isn't overwriting it. Also, systemd has a method for assigning NIC names usually based on the MAC, so I'd check if that was in-play too.

A full ifconfig would be helpful - please use code tags.  Not interested in images.

---

### Post by user_of_gnomes on 2018-04-26
> **TheFu said:**
> Well, those aren't the same devices. I'd check that you are using the correct device inside the VM.  Wouldn't hurt to check that udev isn't overwriting it. Also, systemd has a method for assigning NIC names usually based on the MAC, so I'd check if that was in-play too.

A full ifconfig would be helpful - please use code tags.  Not interested in images.

I solved the problem by restarting the virtual machine. 
I have the habit of saving machine states and it hit me that I was constantly doing that (although I am fairly certain that I had reset the system at least once when I changed network name, not sure why it didn't take that time).

The device name under Linux still isn't the same as mentioned by VirtualBox but the MAC address has now successfully changed. 

So next time just ask me to turn it off and on again!

Thanks.

---

### Post by TheFu on 2018-04-26
> **user_of_gnomes said:**
> So next time just ask me to turn it off and on again!

Thanks.

That is a foreign concept to me. Sorry.  I use Linux and only reboot when a new kernel has been installed.  BTW, I patch on Saturday mornings and there WAS a new kernel this week for 14.04 and 16.04 lines.

In 16.04 and later, NIC device names are likely based on the MAC if systemd hasn't been forced to use some other name. That normally happens either because an upgrade-install or manually through grub config settings.

---

