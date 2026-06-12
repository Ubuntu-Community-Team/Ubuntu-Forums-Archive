---
title: "connect two laptops over ethernet"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Justin Holt on 2006-12-23
How or is it possible to connect two laptops, one running windows and one running ubuntu together so that one can recover data and carry it over to the windows box.  
   
   What happened was my friends laptop crashed, he can mount the ntfs partition thru the live cd and the mounting script, but doesn't have a large storage media like an ipod to carry things over on.  Is it possible to hook these to together.

---

### Post by djRobbieF on 2006-12-23
Yes; of course it is.

Either an ethernet switch, router, or a crossover Ethernet cable will do it.

Set up a static IP address on both systems, using the same subnet.

Example:
_System 1_
10.0.0.5  (IP Address)

_System 2_
10.0.0.6  (IP Address)

_Both systems_
255.255.255.0  (Subnet)
10.0.0.1  (Gateway) - won't actually DO anything, but just use that as a filler.

Then, set up a shared folder on the Windows laptop.

Then, bring up nautilus (Places --> Home Folder will get ya there) in Ubuntu.  Press CTRL-L to bring up the address field.  Type smb://10.0.0.5   - assuming 10.0.0.5 is the IP you assigned to the Windows PC.

smb:// specifies for Ubuntu to connect to the computer using the SMB (windows file sharing), aka Samba protocol.

If you have a firewall turned on on the Windows laptop, make sure it's turned off if you can't connect.

Now, you'll see the network share you created on the windows box.  Copy your files into that.

Cheers.

---

