---
title: "Bootloader Location while installing Ubantu on external HD"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Siddhartha.tomar on 2009-04-24
Hi..I am New to Linux...I am trying to Install Ubantu in my Windows machine on External Hard disc..where should I give the bootloader location while installing Ubantu ( I mean On hard Drive 1 i.e. My Laptop hard dics or     Myexternal  Hard-drive ..which i tried and it deleted the bootloader entry frm my Laptop hard drive  so I could not boot into Windows machine and had to get it formetted)
 ..I don't want to disturb my windows that is already set as default OS. I want My Hard Disc to be connect only if I want to use Linux ..not all the time.

---

### Post by scotty2 on 2009-04-24
I have ubuntu on an external drive which allows me to use it on various computers.  The computer must have the option to boot from a USB device (most new computers allow this).  Installing GRUB on the external device allows allows me to run ubuntu without affecting the existing setup on a computers internal disc.

For future reference, it should not have been necessary to format your windows harddrive because grub has been loaded.  It is only the MBR which needs to be reset.

---

### Post by Siddhartha.tomar on 2009-04-27
Hi Scotty2,

       Thanks for your reply.
I am trying to install Gutsy on my external HDD. Could you please give me the series of steps u followed to get ubuntu running on an external HDD.

Thanks in Advance,
Siddhartha

---

