---
title: "VMWare and Ubuntu NETWORKING"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by DizzyThermal on 2008-02-02
Hey guys, I have successfully installed Windows XP Pro in VMWare under my Ubuntu 7.10 Gusty Gibbon.

I want to bring all my music from Linux to my VMWare Windows XP Pro so I went to network and the Windows Network and went to WORKGROUP and clicked Stephen-VMWIN which I named my VMWare Windows XP Pro computer.  It says: "Sorry, could display all the contents of "Windows Network: stephen-vmwin".

This probably isn't the way I should be doing it right?

In VMWare Windows XP the network places shows everyone but the running Linux system.

Do I need a certain driver or something?

Thanks in advance!!!

**Solved** View my last post!

---

### Post by DizzyThermal on 2008-02-03
Anyone got an idea?  Still stuck :(

---

### Post by gruss on 2008-02-03
Is the vmware file stored on the same partition as your ubuntu load?  I think there are a couple ways you could do this.  
If the files are on a seperate partition you could either add that drive in vmware, or map it in windows, either way I think you'll need to install ifs driver for win:
[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)
OR
you could install samba in the ubuntu machine and share the folder with the music, then windows should be able to find it pretty easily.  just do a net use: <drive letter of your choice> \\hostname\sharename  Are you using NAT for the XP's netowrk or did you give it its own IP address?  this may be helpful in troubleshooting.

---

### Post by DizzyThermal on 2008-02-03
I was successful in doing this.  Just enable **file sharing** on the Windows C drive and it will work.

:) Just in case you guys get stuck like I did!

---

