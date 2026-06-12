---
title: "configure networking on ubuntu server 13.10 with GUI????"
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by fred-lorrain on 2013-11-22
Hello folks,
I need some help setting up networking on my xubuntu server 13.10 box. To put it simply, how do I configure eth0 to connect to the internet by  dhcp provided by the dsl modem/router, then share the internet and  internal network connections through eth1 to a switch?
I have a gui on my server, I installed xfce desktop. Networking is working fine when i connect auto by dhcp to one of my nics, i have internet and my Samba shares are working. I now want to move the server up the chain, connect directly to the dsl modem/router and pass along the internet and internal networking by connecting my second nic to the switch. I have tried to set up eth1 as a bridge, but am doing it wrong i guess, because the clients connected to the switch arent getting ips. Thanks in advance for a link to a walkthrough, or a noob friendly explanation of how to achieve this!

---

### Post by fred-lorrain on 2013-11-22
*******Update*********
I used network manager to delete my original configuration for both nics, then I set up eth0 again and chose "shared with other computers" as the connection type, instead of automatic via dhcp, then i set up eth1 as a bridge, left everything at default auto by dhcp, and voila!! Clints connected to the switch have internet! They also can connect to my Samba share, the only thing to hash out is that my virtualized win7 client is not visible to other clients on the network, where it was before. So now if anybody has any idea why my virtual machine isn't showing up on the network, i'd like some help with THAT! Thanks..

---

### Post by fred-lorrain on 2013-11-22
*******Update #2!*******
I went into the network settings on Virtualbox and changed the connection to eth1, where before i had it on "bridged" in order for it to work, and that fixed it! So I have achieved what I set out to do all via GUI, and some fearless noodling : ) I will post back if I run into any problems once the server is put to use by multiple clients who will depend on the server for internet access, shared files, and a program hosted on the VM.

---

