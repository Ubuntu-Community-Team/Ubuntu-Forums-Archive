---
title: "vbox shared folder..."
date: 2008-12-20
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-12-20
Ive setup a shared folder via the VirtualBox GUI and am now trying to get xp pro to see it by typing the following into the command box:

```
net use x: \\vboxsvr\share
```

but I get the error:

```
System error 67 has occurred.

The network name cannot be found.
```

---

### Post by jimmy the saint on 2008-12-20
It sounds like your Virtual Machine cannot connect to the network.  Do you have firewall software installed on the VM?  Is the virtual network adapter enabled?  Can you open a web browser and connect to the internet?  
The virtual machine communicates with the host via a virtual network interface, so the guest and the host must be able to communicate with one another via the network interfaces.

---

### Post by kamitsukai on 2008-12-20
yep online

---

### Post by jimmy the saint on 2008-12-20
hmm.  I did it graphically rather than using the cmd prompt.  try to use the map network drive option by right-clicking on "My Computer" and selecting "Map Network Drive"

My share looks like "\\VBOXSVR\vboxshare

Also, did you add the folder you want to serve as your share to the shared folder dialoge in the virtualbox manager application?  You have to add it there first before it is made available to your guests.  Also, you have to install guest additions.  I assume you did all that, but I thought they should be mentioned.

---

### Post by Therion on 2008-12-20
If you created the shared folder in your VM, you should be able to find it listed in XP under My Network Places.  

Expand **Entire Network\VirtualBox Shared Folders** and you should see your shared folders under **vboxsvr\username**.

---

### Post by kamitsukai on 2008-12-20
I've already added it to the shared folders bit in vbox and i tried it the grphical way by right clicking on my computer and get a simmlar error to before. also it's nowhere to be seen in network places...

---

