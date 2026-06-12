---
title: "VMware Server disables network folder"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by What The Deuce on 2007-08-15
I am running Ubuntu Feisty and I have installed vmware server with XP running.

I first used virtualbox and networking worked great.  I could detect all other computers on my network (SMB).  I then moved to vmware because virtualbox crashed too much.  And I now cannot see any computers or shared folders in my "network" folder.  Other computers on my network can see my samba shared folders and use them, but I can't see them anymore.

This happened to my computer once before.  Anyone have any idea?  Could all the network bridges and whatnot installed by vmware be messing with me.

---

### Post by ihristov on 2007-08-17
Is the VM configured with an IP address in "Bridged" mode? If it's in "NAT" mode you will be able to see other shares from the VM, but not the shares on the VM. Acording to your post it's the other way around which is strange.

Have you installed VMWare Tools inside the VM? Not sure if it's related, but could be.

Also, is it only a matter of not being able to browse the network? In other words can you open a particular computer by just typing it's name or it's IP address \\computer or \\192.168.1.1 ?

Also check the firewall inside your VM.

I have the same setup - Ubuntu is the host OS, VMWare Server and one VM that has WinXP installed and when the VM is in bridged mode all works fine. I can open and browse other shares from the VM and I can browser and open the shares on the VM WinXP.

---

