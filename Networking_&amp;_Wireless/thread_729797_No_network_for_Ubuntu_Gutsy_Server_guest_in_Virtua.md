---
title: "No network for Ubuntu Gutsy Server guest in Virtualbox on XP host"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by cebesius on 2008-03-20
Hi,

I have an Ubuntu Gutsy 7.10 Server guest installed in a Virtualbox VM on an XP Pro host.  I ran into a problem where Virtualbox doesn't support part of the instruction set assumed to be present by the server kernel that is installed by default, so it wouldn't boot.  I followed [these instructions to get it to boot](http://www.brainyautomation.com/blog/post/Ubuntu-710-(Gutsy)-Server-on-VirtualBox.aspx), downloaded (read: used the network OK) the 2.6.22-14-generic kernel, made the grub menu changes, and now it boots to the generic (non-server) kernel OK.  The problem I'm having now is that Ubuntu doesn't detect the network adapter.  If I boot the Ubuntu Server install CD into recovery mode, I can get network access.

I couldn't figure out how to copy text out of the virtual machine without the guest additions, and no network access.  Below is a screenshot of uname -a, ifconfig, and lspci.  Any ideas?

[IMG]http://img508.imageshack.us/img508/3610/virtualboxlampkp5.png[/IMG]

---

### Post by cebesius on 2008-03-20
I also just tried installing the linux-virtual package, then booted the 2.6.22-14-virtual kernel that was installed, and that booted OK, but still no network was detected.  The installer rescue environment detected the network card OK and got a DHCP lease OK, and worked to download that kernel.

I wonder if there is some kernel module that isn't being loaded that should be.  As you can see in my first screenshot, it has an AMD 79c970 PCnet32 LANCE ethernet controller.  I did lsmod | grep pcn and got this output:

```
pcnet32		34180	0
mii		6528	1	pcnet32
```

---

### Post by cebesius on 2008-03-20
Problem solved!  I found some inspiration in [this older thread]("http://ubuntuforums.org/showthread.php?t=221768") (for Dapper).  While it seems /etc/iftab no longer exists in Gutsy, I found the problem was related to the fact that the MAC address on the network adapter changed when I moved it from one Virtualbox host to the other.  When I made the changed to the virtual machine's network card's MAC address to make it identical to what it was on the other host, all was well.

---

