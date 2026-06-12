---
title: "Preparing a windows network"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by happyhacker on 2008-10-13
I am thinking of adding a Ubuntu server to our currently serverless system. The network have about 3 workgroups and are unused (I do not know how they got there). Anyway, my question is before I plug the server into the network and install the Ubuntu server edition:

1. how should I prepare the PCs (XP and Vista on about 18 of them) before Ubuntu discovers them?

2. initially I want F&P sharing, internet access via a switch and DG834 (currently doing the DHCP)?

3. Can email be done by the server downloading from our ISP provider email accounts and using the Ubuntu system or what is the best arrangement if we keep out ISP facility for now?

---

### Post by Iowan on 2008-10-13
[Here]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP") is a printer-sharing How-to, and [here]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") is a "Perfect Server" setup.  There's another good server-help on help.ubuntu.com but I can't find it at the moment.

---

### Post by happyhacker on 2008-10-14
Hm, that server example is a bit complicated. I will have to find a simpler one to start with so I can understand the need for some of the services installed. I think I see why the ssh is setup - so one can control the server from a windows PC without the need for a display always connected.

Our Printers will be on the network (currently not but that's my intention).

---

### Post by Iowan on 2008-10-14
[This]("http://www.howtoforge.com/ubuntu-home-fileserver") one claims to be a "simple Ubuntu server".

---

### Post by happyhacker on 2008-10-15
A question about drive configurations. The PC we have has only PCI (not express). If I really need SATA can this be added? I also see that RAID5 is recommended for servers. I tend to think configuring two hard drives and copy gives added security with an external dump by some other method.

---

