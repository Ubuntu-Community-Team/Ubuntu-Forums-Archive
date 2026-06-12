---
title: "Dual-boot from server"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-10-26
Hey,

I've been considering the implementation of a diskless system that will boot from a server. Using Ubuntu, this is extremely feasible.

Ideally, I will have my terminal boot off the server's drives. My confusion lies in the usage of the grub loader across the network, as I would like to still have the option to boot into Ubuntu or Windows at startup.

Is this possible to implement?

All help is appreciated.

Thanks,
Kurt

---

### Post by CharlesA on 2010-10-26
Thought you'd have to boot off of PBX to do a diskless boot?

---

### Post by jkurtisr32 on 2010-10-26
> **CharlesA said:**
> Thought you'd have to boot off of PBX to do a diskless boot?

REQUIREMENTS FOR DISKLESS BOOT:
-> An Ubuntu system with (preferably) nfs-kernel-server and tftpd server (the server)
-> At least one PXE-bootable system (the client)
-> It helps to have the client set up in its final configuration before you start
-> Enough disk space on the server to hold the client filesystem
-> A fast network connection between the client and the server
-> A DHCP server which is capable of supporting PXE clients, or a separate network segment where you can run a dedicated DHCP server
-> A good understanding of Linux

I lack the last item on the list.

I found this at the link below:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

-Kurt

---

### Post by CharlesA on 2010-10-26
Oh I thought it was P-something. :P

That how-to pretty much covers it. What do you have questions about?

---

### Post by jkurtisr32 on 2010-10-26
> **CharlesA said:**
> Oh I thought it was P-something. :P

That how-to pretty much covers it. What do you have questions about?

If this is going to be my solution for my workstation, I will also need to know how to dual-boot Windows off the same server. I will need to know how to initialize the GRUB bootloader across the network on startup

---

### Post by ArgusVision on 2010-10-26
We have some XP thinclients at work as well as some linux thinclients. I don't think they are booted off of the same server, but I'm petty sure it can be done... not sure how you'd select between the images?

I'll try to get more info at work tomorrow. Hopfully you'll get an answer before then.

Best of luck.

---

### Post by CharlesA on 2010-10-26
> **jkurtisr32 said:**
> If this is going to be my solution for my workstation, I will also need to know how to dual-boot Windows off the same server. I will need to know how to initialize the GRUB bootloader across the network on startup

Sorry, I don't know enough about how that sort of thing works to give you any hints. Only thing I know is that it's possible to boot an OS like that. I don't know if it'll work with Windows or if it's just a Linux thing tho.

---

