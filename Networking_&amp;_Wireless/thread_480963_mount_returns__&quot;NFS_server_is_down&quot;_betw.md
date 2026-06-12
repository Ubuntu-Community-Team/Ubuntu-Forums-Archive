---
title: "mount returns  &quot;NFS server is down&quot; between Vmware guest and host"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by esekyavuz on 2007-06-22
I run Kubuntu Feisty x64 but want to be able to use my Epson v350 scanner for which only a 32 bit drver exists. So I decided to install 32 bit Feisty as a VM guest and scan there.

Install of (Ubuntu) Feisty as guest went without a hitch. Bridged network allowed connection to the internet and everything is up to date.Yay. Out of the box as usual.

Created NFS share in home directory of guest OS.

I am able to access this share via another computer on the network, but CANNOT on the host. I get error: **mount to NFS server '192.168.0.3' failed: server is down**. No it freaking isn't. I just saw it on my laptop.

trying to mount on the guest a folder shared by the host gives the same result. Server is down.

And I thought I was so clever.

I've tried mounting with the guest network set to the other options (NAT, Private, and so on) and get same result. If I ping from the host, only "bridged" gives timings, the others give "Destination host unreachable". 

Any ideas? TIA.

---

### Post by jpkotta on 2007-06-22
I've had zero luck with networking a host with a vm guest running on the same computer.  I'm almost certain that it's because they're using the same network hardware.  Unless there's a significant latency, it simply won't work, and it will probably never work well.  If you really want it to work, I'd bet a second NIC would fix it, but I'm not 100% sure.

The better solution is to install a 32-bit chroot IF this is a userspace driver.  [http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64](http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64).

---

### Post by esekyavuz on 2007-06-23
Thanks jpkotta, Glad to know it's not just me. And thank you for suggesting chroot, which was a total revelation to me.

There is a section in the VMware Server manual

[http://www.vmware.com/pdf/server_vm_manual.pdf](http://www.vmware.com/pdf/server_vm_manual.pdf)

that describes how to set up a Samba server. "You can then use Windows Explorer to copy files between virtual machine and host..." Perhaps it works samba-to-samba as well. 

I also learned from a blog somewhere that Vmware Workstation (not even free as in beer) gives you automatically a folder for sharing between host and guest. 

I think I'm going to try chroot before I try their samba. I'm Gnoob Number One and the VMware-manual talks about their samba being slightly different from the GNU/Linux samba. I'm not particularly good at getting the normal samba to work. Besides, using chroot would mean I wouldn't need vmware at all and the main idea is to maximize the amount of free software on my machine.

---

