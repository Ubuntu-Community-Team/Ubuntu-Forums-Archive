---
title: "Ubuntu server old network config still active?!"
date: 2019-03-26
forum: Networking &amp; Wireless
---

### Post by mattiash on 2019-03-26
So... I have a peculiar problem.
I have a Ubuntu Server 18.04.2 running as my Docker and Virtual Machine host, it I an HP Proliant G6 with 5 NICs. 4 to use and one for administration work.
enp2s0f0, enp2s0f1, enp3s0f0, enp3s0f1

Last week I felt the need to redo the network config from scratch since the old one started to look like a jungle.
I took the time to really plan my new setup making it more logical and such, so this is what I came up with:
[https://pastebin.com/c6CUibz6]("https://pastebin.com/c6CUibz6")

It works as intended but.... when I login to the server and it shows the network setup I get this:
[https://pastebin.com/T20wCSe7]("https://pastebin.com/T20wCSe7")
Look closely enp2s0f1 is missing and I get a bond from the old config bond0.

What?! Quickly I run ip a, so here that is:
[https://pastebin.com/WfSbxxPk]("https://pastebin.com/WfSbxxPk")
Here I can see enp2s0f1 and that bond0...

bond0 has the same MAC-address as enp3s0f0 and enp3s0f1 - how is that possible?
And how is bond0 created? It is not configured in the setup.

I am bewildered please help!

---

### Post by mattiash on 2019-03-26
The mystery continues... I decided to restart the server, after the reboot, the network yml was redacted to an way older one. Not even the one with bond0.
What the ****?

---

### Post by houstonbofh on 2019-03-27
Several things...  First, you are pulling dhcp on both the bond and the interface.  Pick one.  Second, the file is the base config.  Now you have to check and apply it.  Did you "sudo netplan --debug apply" after the changes?  Some examples here. [https://netplan.io/examples](https://netplan.io/examples)

---

### Post by mattiash on 2019-03-28
Thing is I cant go either debug or try since teh parameters I use arnt supported in netplan, but works when applied. The config has changed alot.
I will post it here later, among other things I have done as you said with bond and interfaces.

---

### Post by mattiash on 2019-03-28
So here is the current netplan-config.
[https://pastebin.com/bsnh4Rt0](https://pastebin.com/bsnh4Rt0)

Working like a charm.

---

### Post by houstonbofh on 2019-03-29
I guess doing dhcp twice is a bad thing. :)

---

