---
title: "ubuntu on windows - virtual box"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by jared29 on 2015-06-07
Hi Everyone,
I am a windows guy and I am new to Ubuntu.  I created a virtual box instance, and it was working correctly on my home network.  I shutdown, etc and it always worked well.  I just came to a coffee shop and had a new public network on my windows box (don't know if that matters).  When I try to use Ubuntu now, "Disconnected - you are now offline". If I click on the icon on the top right and select "Wired connection 1", there is a rotating icon indicating that it is trying to connect, but it doesn't work.

I only use a wireless connection for my windows box by the way.

I am not sure what the Virtual Box network settings should be.  It currently says
Attached to: Bridged Adapter
Name: Intel Wireless-N 7260
Advanced
Promiscouos Mode: Allow All (I've tried them all, not sure what should be here)
Cable Connected: Checked (also tried unchecked)

I've read another post that said I should try: nm-tool...here is the output
jared@jared-VirtualBox:~$ nm-tool


NetworkManager Tool


State: connecting


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        08:00:27:2E:35:BA


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on



1. From my VM's perspective, is this a wired connection?
2. How do I diagnose and fix this?

---

### Post by SeijiSensei on 2015-06-07
You don't want to use a bridged adapter in most cases.  Choose the NAT option in Settings > Network for the virtual machine.  Read this documentation from VirtualBox for more details: [https://www.virtualbox.org/manual/ch06.html#networkingmodes](https://www.virtualbox.org/manual/ch06.html#networkingmodes)

The only reason to use a bridged adapter is if you need to see the virtual machine directly from other machines on your network.  This makes sense if the guest is a server, but not if the guest is a regular desktop machine.  Using NAT treats the VB host as if it were a masquerading router like the one that connects your local network to the Internet.  The guest hands its outbound traffic to the host which forwards it along to the network.

You almost certainly do not want to use a bridged configuration in a public setting like a coffee shop.  It's already bad enough that the Windows machine is exposed to all the other machines on the shop's network.  Be glad that the Linux guest is hiding behind the Windows host in a NAT configuration.

---

