---
title: "Vista NTFS problems"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-12-03
I just bought vista ultimate from a friend because he didn't like it and I am trying to dual boot but when I select where to install an error pops up that says they are not in NTFS format and it wont let me just skip ahead either, how do i change my partions?

---

### Post by Sef on 2008-12-03
You need to use Vista's partitioner to shrink its partition.   Did you use it?  If not, then redo the partitions with Vista's partitioner.

---

### Post by jeromey on 2008-12-03
you can use the ubuntu live cd 


go to system-administration-partiton editor 

now shrink your ubuntu partition to make space for vista (if needed)

you can leave the space that you plan to use for vista unallocated for now

pop in the vista install cd


when it gets to the point where you choose where you want to install you can select "install to the unallocated space"  (just make extra sure that you are not installing over the entire disk)




after installing vista it will replace grub boot loader with vistas default boot loader  (vistas boot loader wont detect ubuntu)

so to reinstall grub after vista clears it you can follow this guide  

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
(follow the very first section where it says  "Quick Start" (1-6))

---

### Post by mr-Kirch on 2008-12-03
> **jeromey said:**
> you can use the ubuntu live cd 


go to system-administration-partiton editor 

now shrink your ubuntu partition to make space for vista (if needed)

you can leave the space that you plan to use for vista unallocated for now

pop in the vista install cd


when it gets to the point where you choose where you want to install you can select "install to the unallocated space"  (just make extra sure that you are not installing over the entire disk)

can i just make it all space for vista and then install ubuntu on my external (when best buy gets a new shipment?)

---

### Post by mr-Kirch on 2008-12-03
Okay guys i changed everything to unallocated so i hope it works or ill just re install ubuntu and sell vista, i still have 6 gigs on a linux swap drive though and it wont let me add it to unallocated or delete it, is that supposed to happen?

---

### Post by tjwoosta on 2008-12-03
> can i just make it all space for vista and then install ubuntu on my external (when best buy gets a new shipment?) 

i dont see why not

> Okay guys i changed everything to unallocated so i hope it works or ill just re install ubuntu and sell vista, i still have 6 gigs on a linux swap drive though and it wont let me add it to unallocated or delete it, is that supposed to happen?

probably because the swap partition is mounted

you will need to right click on it and choose swapoff before you will be able to make any changes to it

---

