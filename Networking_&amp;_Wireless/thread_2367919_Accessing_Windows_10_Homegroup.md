---
title: "Accessing Windows 10 Homegroup?"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by dynmetalworks on 2017-08-04
I have a desktop in my shop with Xubuntu on it to control a cnc plasma table. Want to to join the Homegroup I have setup on my Office PC running Windows 10. Both are connected to the same wifi router in the shop. I have zero experience with Linux so please explain it as simple as possible. Thanks

---

### Post by gordintoronto on 2017-08-05
What version of Xubuntu? 

After joining the homegroup, what do you want to do? Most people want to access files in a shared folder on either the Windows computer or the Linux computer.

If the Xubuntu computer has synaptic package manager installed, you can use it to install smbclient. It might need a reboot for the file manager to show "browse network" on the left side. Click it once, and it should show computers which have shared folders. Double-click the one you want, then the folder you want to access. At some point you will probably need to enter the Windows username and password for the computer.

Sharing a folder in Xubuntu is a bit complicated. You need to install system-config-samba.

---

### Post by Morbius1 on 2017-08-06
> Want to to join the Homegroup I have setup on my Office PC running Windows 10.
No can do. 

A Windows HomeGroup is a peer-to-peer networking protocol that uses Web Services on Devices (WSD)
to publish and discover resources on a local network. There is no such thing as WSD in Linux.

Here is a HowTo that does a little bait-and-switch: How to Add a Mac to a Homegroup: [http://www.wikihow.com/Add-a-Mac-to-a-Homegroup](http://www.wikihow.com/Add-a-Mac-to-a-Homegroup)

You cannot access a HomeGroup from a Mac either so instead it shows you how to create a real Windows share for the Mac or Linux machine to access. Just ignore the macOS references.

---

### Post by dynmetalworks on 2017-08-09
> **Morbius1 said:**
> No can do. 

A Windows HomeGroup is a peer-to-peer networking protocol that uses Web Services on Devices (WSD)
to publish and discover resources on a local network. There is no such thing as WSD in Linux.

Here is a HowTo that does a little bait-and-switch: How to Add a Mac to a Homegroup: [http://www.wikihow.com/Add-a-Mac-to-a-Homegroup](http://www.wikihow.com/Add-a-Mac-to-a-Homegroup)

You cannot access a HomeGroup from a Mac either so instead it shows you how to create a real Windows share for the Mac or Linux machine to access. Just ignore the macOS references.


That worked! Thanks!

---

### Post by mörgæs on 2017-08-09
Good, please mark the thread solved.

---

