---
title: "sharing CD drive"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-04-06
Can I use the cd drive on my Laptop to load into my netbook..????

---

### Post by lavinog on 2010-04-06
What do you mean by "load into"?

If you are asking if you can install ubuntu from your laptop drive to your netbook, then the answer is no.
You can, however use the install cd on the laptop to make a usb installer that will work on the netbook.

---

### Post by drzoo2 on 2010-04-06
> **lavinog said:**
> What do you mean by "load into"?

If you are asking if you can install ubuntu from your laptop drive to your netbook, then the answer is no.
You can, however use the install cd on the laptop to make a usb installer that will work on the netbook.

I think what he is after is using it as a shared resource. 

While I haven't actually done this, I see no reason you couldn't share the mount point like you would any file. Either with Samba or NFS. When the CD/DVD is inserted and mounted it should be available like any network resource.

z

---

### Post by yetiman64 on 2010-04-07
For installing Ubuntu to the netbook post #2 sounds like the way to go (make a usb installer).

For sharing a cdrom over samba check out towards the bottom of the file /etc/samba/smb.conf for an example of how to share cdroms. (How I've managed in the past, before discovering "system-config-samba".) You may need to install additional samba packages depending on your setup and if this is what you're wanting to do.

An easier way than editing smb.conf directly, to share cdroms, is to install the package "system-config-samba", mentioned above. Its a GUI tool for samba settings, and you can access it from System > Administration > Samba.

---

