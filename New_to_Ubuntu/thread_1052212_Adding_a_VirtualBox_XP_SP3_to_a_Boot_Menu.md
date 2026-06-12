---
title: "Adding a VirtualBox XP SP3 to a Boot Menu?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by wildfire95 on 2009-01-27
A week ago, I had a Vista and then i used Wubi to add Ubuntu to create a Dual-Boot.

I recently saw the application:
VirtualBox OSE

I created a 10GB partition, and im installing WindowsXP SP3, but is there a way to add that option to the Grub boot up menu? Or can I only access it via Ubuntu?

Thanks,
Cameron.

---

### Post by Locke_99GS on 2009-01-27
You can't boot directly into a VM without having another minimal linux install with scripts loading the VM.

The partition Vbox made for your Windows install isn't a real partition, rather it is a file that Vbox treats like a partition. 

To install Windows and have it bootable from GRUB, you'll want to create another real partition, do a conventional install of Windows to it, repair GRUB, and alter menu.lst to reflect the added OS.

---

### Post by wildfire95 on 2009-01-27
Yea well.. partitions always screw up for me =S 

But ill try :)

---

### Post by theozzlives on 2009-01-27
I think they make a VirtualBox for Vista that you can run XP under go [here]("http://www.virtualbox.org/") to find out more about VirtualBox.

---

