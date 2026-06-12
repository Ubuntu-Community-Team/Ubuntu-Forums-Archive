---
title: "cross cable"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by ryu kun on 2006-10-17
I have two computers running Dapper.

How would I connect them for file transfer or gaming by using a cross over cable? Could you please explain it in detail?

I also have a wireless internet connection. It's secured with WPA so I use NetworkManager. I don't want my internet connection to get affected by cross cable connection, if possible.

---

### Post by peteguhl on 2006-10-17
Simple answer: Just use the wireless network, it won't affect your Internet connection.

Fast transfer answer (200mb/sec - 100mb duplexed):
If you have cable crimpers, crimps, and cable make a crossover cable. Use the following order for one end:
O/W, O, G/W, B, B/W, G, Br/W, Br
and this for the other:
G/W, G, O/W, B, B/W, O, Br/W, Br

Make sure to crimp tab down.

Or just buy a crossover cable.

Next, assign ip address and subnet mask on both computers. For example:
Comp1 - ip:192.168.1.3  subnetmask:255.0.0.0
Comp2 - ip:192.168.1.4  subnetmask:255.0.0.0

---

### Post by ryu kun on 2006-10-17
Thanks for quick reply.

I've connected two computers by a cross cable and assigned ip address and subnet mask on both computers. However, when I try to access a shared folder in the remote computer, a window appears titled "authentication required" and it asks: "You must log in to access username@computername/foldername domain WORKGROUP". I've filled in the fields, username, domain and password but it won't accept. Remote computer (desktop) doesn't even see any folder in my notebook (I've shared some).

By the way, how would I share folders by using my wireless network?

---

### Post by carontis on 2006-10-17
In winXP try to input your Administrator password; if you haven't (as for XP Home Edititon) only write Administrator (name) and nothing at all for password, give OK and you should be in...

---

### Post by Iowan on 2006-10-17
> **ryu kun said:**
> I have two computers running Dapper.
Not XP...

How did you share the folder on the laptop - Samba or NFS?
BTW, does the desktop user have a corresponding acount on the laptop?

---

