---
title: "Gigabit network performance"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by bsh on 2008-04-12
i have a ubuntu 7.04 server pc (semrpon 2300 on a nforce2 mobo, and a pci realtek 8169s gigabit card), and a xp desktop (athlon64 x2 4200 on a nforce4ultra mobo, using the onboard gigabit lan), connected through a dlink gigabit switch. all supporting jumbo frames up to 9000 bytes (tried this but didn't improve the speeds)
i have tweaked samba a bit, so i get 35mb/s when downloading things from the ubuntu server to the desktop, but only 20-25mb/s when uploading from the destop to the server.
i also tried iperf, and found a strange thing:
when iperf runs in server mode on the desktop and the clien is running on ubuntu, i get 530mbit/s speeds over tcp
in the opposite way (server runs on ubuntu, client on xp), i get 460mbit/s tcp.
cpu usage is minimal in both cases.
i don't understand, why the different speeds in the opposite directions? what's causing this?
and can i squeeze out more from the network?
any help is appreciated.

---

### Post by Rhubarb on 2008-04-12
Well, you may have hit the maximum reading / writing speeds of your hard disk drives in your server / client.

Another possibility is that samba is just not efficient in transferring files accross fast (there's probably a lot of overhead).

This is just speculation, so I could indeed be very wrong.

I use ssh to share between my server and ubuntu clients here over gigabit, ssh is very fast imho.
If you can, perhaps you can try transferring files via ssh?  On your windows box you could try a free program called winscp
[http://winscp.net/](http://winscp.net/)

---

### Post by bsh on 2008-04-12
samba performance is one thing, i have tweaked it to the max (afaik)
but iperf doesn't test the hard disks etc, it just sends random data between the two interfaces, from memory to memory, ie. hard disk is no bottleneck there.

---

