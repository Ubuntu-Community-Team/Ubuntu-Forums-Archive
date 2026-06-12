---
title: "Sharing folders on a Linux-only network."
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by lowlymarine on 2008-10-13
This should be the easiest thing in the world, but for the life of me I can't get it to work.  I have Ubuntu on every machine on my network (that I care about seeing; just as well if my roommates' Vista boxes can't touch my Linux-y goodness).  That is, a desktop connected by wire to the router (D-Link DI-524) running Hardy, a laptop connected wirelessly running Hardy, and a laptop connected wirelessly running Intrepid.  (I've tried adding wires to the laptops to no noticeable effect.)
I have tried every tutorial I could find on these forums and beyond, but they're all focused on getting Windows boxes to see Samba shares or Samba to see Windows shares, neither of which I care about and none of which worked to make Samba see Samba shares.  How far I can get in Nautilus appears to change randomly - sometimes I click "Network" from the Places menu and nothing happens, other times I can go into the workgroup and see all the computers but they're all empty when I click on them (despite having multiple shared folders).  My workgroup is "WORKGROUP," the computers all had valid hostnames defined during installation (desktop is "Stationerybob", laptops are "Spottedbob" and "Thinkinbob" respectively), and my router has static IPs assigned to my Linux boxes.  I have Samba, smbfs, and SWAT (which doesn't work, by the way - "swat" and "sudo swat" in terminal do nothing) installed.  I tried turning the firewalls off (sudo ufw disable), but again that made no difference.

But the most bizarre (and frustrating) thing is that if I boot into the WinXP x64 installation on my desktop, the laptops can see shared directories from it!  So I seem to have no issue with that apparently difficult problem of getting Linux and Windows to cooperate, but I can't get Ubuntu to cooperate with itself.  Any ideas?  Ideally something human-friendly - I mean, ssh servers are an option I suppose but if that really the only way then I'd appreciate it if someone could point me in the direction of a howto on that...

---

### Post by Ayuthia on 2008-10-13
I usually use NFS:
[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)

It doesn't really answer your samba problem though but it is another way to share files in Linux but won't really work with Windows.  Sorry.

---

### Post by iponeverything on 2008-10-13
The problem might be there is no master for your work group. Add these to one of the samba configs -- so that machine will be the master.

```

local master = yes
os level = 33
domain master = yes
preferred master = auto
wins proxy = yes
browseable = yes

```

---

### Post by lowlymarine on 2008-10-13
Hmm, I tried what you said iponeverything, no luck.  Nautilus will open the "Network" window, in which there is an item called "Windows Network", but it's empty, even after a reboot.  Also tried ```
sudo /etc/init.d/samba stop && sudo /etc/init.d/samba start
``` a few times with no luck.  I've attached my smb.conf; I followed [this guide]("http://ubuntuforums.org/showthread.php?t=202605"), but it is pretty out of date.  Irritatingly, though, "sudo dpkg-reconfigure samba" refuses to generate a new stock smb.conf, and my old one from before that tutorial is so messed up I doubt it'd be much use to go back to.

---

