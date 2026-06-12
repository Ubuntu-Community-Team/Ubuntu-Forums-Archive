---
title: "Boot Server"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by helives95 on 2008-05-10
I would like to make a boot server that will allow me to do a network boot and access the computer and use it from the network (boot to LAN). What are the steps I need to complete to do this?

---

### Post by nixscripter on 2008-05-11
If you are talking about a diskless client-server set, here is how to do it with Gentoo to give you an idea:
[http://www.gentoo.org/doc/en/diskless-howto.xml](http://www.gentoo.org/doc/en/diskless-howto.xml)

Though it is quite complicated, here are the basic steps (having done this myself):

The server will need to serve: NFS (the hard drive), TFTP (for clients to download boot files), and DHCP (so clients can get an IP and the location of the boot files).

Each client will need to have PXE boot. Most BIOSes are smart enough to nowadays if the machines are new.

The boot files in question are a pxegrub, which is a boot loader designed for this, and the kernel you wish to boot from. Creating these files are somewhat complex, whic his why the HOWTO above is so long. Gentoo has a pretty good process, being a from-source distribution for hackers.

Also, if the clients do have their own hard disks, the NFS server is not necessary, but the rest of it is.

If you need more specific directions, I might be able to walk you through it, but it will be quite long.

---

