---
title: "Networking win2003 server with Ubuntu 8.04"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by qryzzy on 2008-05-01
Hi,
I'm really new to Linux, i have a network (wired) with a Win 2003 server and w2k/xp workstations. I have installed 8.04 on one workstation but the problem is that i cannot access shared folders on the server. although i can access the shared folders on all the other machines.

i really need to be able to do so and later share my hp printer across the network.(no idea how).

Kindly assist

---

### Post by superprash2003 on 2008-05-01
are you able to ping the server? in nautilus type smb://(ip address of server)

---

### Post by qryzzy on 2008-05-01
i can see it in my network( form file browser) but if i open it it is blank

PS how do you get to Nautilus?

---

### Post by superprash2003 on 2008-05-01
go to places->computer and type smb://(ip address of server) in the Location field.

---

### Post by meadmarc on 2008-05-01
Printer networking can be a bit complicated, depending on how your network is set up.

We have HP Directjet printers here at work, which was fairly easy to set up using the GUI in Ubuntu.

If you have a printer that is shared from a windows computer, I would suggest that you try the Linux Reality podcast on printer networking.  This was a HUGE help to me. 

Actually, as a new Linux user, you might want to check out other episodes that relate to what you're working on!  I learned Linux with this podcast on my 45 minute commute!

[http://www.linuxreality.com/podcast/episode-29-printer-networking/](http://www.linuxreality.com/podcast/episode-29-printer-networking/)

---

### Post by meadmarc on 2008-05-01
> **qryzzy said:**
> Hi,
 the problem is that i cannot access shared folders on the server. although i can access the shared folders on all the other machines.

i really need to be able to do so and later share my hp printer across the network.(no idea how).

Kindly assist

Use the Synaptic packet manager to make sure SAMBA is installed.  It's often needed to navigate Windows networks!

---

### Post by qryzzy on 2008-05-03
Thanks guys. esp Meadmarc you've been a great help.
got to Samba but first have to go through the lit. will update you once through.
so far i can now see the Ubuntu comp on the network, need to configure permissions and add it into the domain.

Once again thanks.:biggrin:

---

### Post by meadmarc on 2008-05-08
If you are going to try to join your Ubuntu client to a windows domain, I would highly suggest a packet called Likewise, again available via synaptic.

It has a GUI that you can also install (they should both pop up in synaptic), which makes it amazingly easy.  Again, Samba must be installed, but you have that now.

I spent a year trying to join Linux to a windows domain without success.  Likewise took about 10 minutes!

Hope that helps, and you are welcome!

---

