---
title: "Samba - Gutsy to XP transfers horifically slow"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by niallporter on 2008-03-02
Hi all,

I have an Ubuntu Gutsy x86 machine and a windows XP machine here.  Samba server and client installed on the Gutsy box.  If I copy a file across the network from the Gutsy box to the XP one it works fine, ~600MB ISO file copies in around 2 minutes.  For a 100Mbps LAN that seems about right to me.  Also, it doesn't matter if I initiate the copy from either side, i.e. opening the Samba share from the XP machine, or opening a share on the XP machine from Ubuntu and copying from there, it's the same speed either way

The problem is if I want to copy the same file from the Windows box back to the Ubuntu one.  Exactly the same file takes anything from 80 - 150 mins :(  Again, it doesn't matter which machine I initiate the copy from.

This is making me think it's not a problem specifically with either the Samba client or server on Ubuntu since it's the same "pushing" the file across from Windows or "pulling" it across from Ubuntu.  The network speed on both machines is 100Mbps at full-duplex.  Samba version is 3.0.26a, Ubuntu machine is fully updated and XP is Service Pack 2 with all Windows automatic updates applied.  Any ideas?

TIA
Niall

---

### Post by alenis on 2008-03-02
I had a similar problem with my nas box. I could access it at full speed with windows but transfers to and from the linux box (feisty) were very slow. I solved the problem by disabling the on-board network adapter and installing another one.
the adapter working properly i s a DLINK DGE-530T Gigabit Ethernet Adapter
the onboard adapter NOT working with feisty (I don't know if the situation has improved) was a Realtek RTL8111B

---

