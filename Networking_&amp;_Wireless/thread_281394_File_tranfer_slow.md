---
title: "File tranfer slow"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by fernando_lopes_jr on 2006-10-21
I have 4 computers in my home network and one of them was ubuntu 6.06 installed with Samba share its working as a home nas while in windows the share works fine download and upload to the computer are quick in my other ubuntu machine file tranfer is realy slow.I bought 1 gbit nic for each of the computers so speed should not be a problem but a 4 giga transfer takes 2 houres to transfer.The problem must be in my ubuntu computer because when I'am in windows transfer is quick. I've looked in the forum for people with the same problem but found no solution.

---

### Post by fernando_lopes_jr on 2006-10-21
One more thing my router is a D-Link DGL-4300 its supports 1 gbit nic

---

### Post by TheWizzard on 2006-10-21
what's in the log-files? if you can't find a clue here, increase the level of detail. 

try: 
http://www.google.nl/search?q='samba+optimization'
$ man samba

---

### Post by fernando_lopes_jr on 2006-10-21
I don't think it's a samba problem since the samba shares works fine on my windows pcs.Let me make it more clear:
  Server                Client PC
Ubuntu samba share<---->Windows    Transfer works fine   
Ubuntu Samba share<---->Ubuntu     Transter mega slow

The problem is samewhere in my client ubuntu pc.

---

### Post by TheWizzard on 2006-10-22
> **fernando_lopes_jr said:**
> I don't think it's a samba problem since the samba shares works fine on my windows pcs.Let me make it more clear:
  Server                Client PC
Ubuntu samba share<---->Windows    Transfer works fine   
Ubuntu Samba share<---->Ubuntu     Transter mega slow

The problem is samewhere in my client ubuntu pc.

this is exactly why i think it is a samba problem.

---

### Post by fernando_lopes_jr on 2006-10-23
Founs solution in this thread [http://ubuntuforums.org/showthread.php?t=143982&highlight=duplex](http://ubuntuforums.org/showthread.php?t=143982&highlight=duplex)

I did this:

If it is loaded then there's the chance that r8169 has grabbed the NIC ... however, you can force r1000 to be used by a small "hack".

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/
This will move the r8169 kernel module into your home directory.

# sudo depmod -a
Rebuild the kernel module dependencies.

# sudo mv /boot/initrd.img-`uname-r` /boot/initrd.img-`uname -r`.ubuntu
make a backup of the original initrd.

# sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
Create a new initrd WITHOUT the r8169 module

# sudo gedit /etc/modules

Add "r1000" (without the quotes) at the end of the file.

Save the file.

Upon reboot you are using r1000 for sure as there's no more r8169.

---

