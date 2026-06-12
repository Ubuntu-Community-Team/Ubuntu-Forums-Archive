---
title: "How do I install Windows XP on VMware Player on Ubuntu 8.10"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-28
:( I can't find out how anywhere. I downloaded VMware Player 2.5.1 and installed it. But how do I install Windows XP into it? I really need to so I can use some of its software. Thanks :)

---

### Post by albinootje on 2009-01-28
> **gymophett said:**
> :( I can't find out how anywhere. I downloaded VMware Player 2.5.1 and installed it. But how do I install Windows XP into it? I really need to so I can use some of its software. Thanks :)

I recommend VirtualBox, or if you really want VMware, then install the free-of-charge VMware server to do the installation of your guest VM.
VMware player is just a player for pre-created guest VMs.

---

### Post by kk0sse54 on 2009-01-28
You need to install Vmware Server (either 2 or 1) because other wise for vmware player you can't make your own vm's and have to instead download premade ones from the vmware website. For installing xp check out [http://www.vmware.com/support/pubs/server_pubs.html](http://www.vmware.com/support/pubs/server_pubs.html) under the user guide there should be instructions.

> I recommend VirtualBox, or if you really want VMware, then install the free-of-charge VMware server to do the installation of your guest VM.
VMware player is just a player for pre-created guest VMs.
Virtualbox is fine until you want to try out one of the *BSDs and then it fails miserably.

---

### Post by gymophett on 2009-01-28
> **albinootje said:**
> I recommend VirtualBox, or if you really want VMware, then install the free-of-charge VMware server to do the installation of your guest VM.
VMware player is just a player for pre-created guest VMs.

Oh, okay.. VMware server is lagging. So I'll go with virtualbox. Thanks :)

---

### Post by ww711 on 2009-01-28
> **gymophett said:**
> :( I can't find out how anywhere. I downloaded***  VMware Player 2.5.1*** and installed it. But how do I install Windows XP into it? I really need to so I can use some of its software. Thanks :)

VMware player only lets you 'run' an OS; it's not designed to create. VMWare workstation will let you create and edit the specifications of your virtual machine.

You could try virtualbox as an alternative.

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by kk0sse54 on 2009-01-28
You can also check out this [ubuntu virtualization mega thread]("http://ubuntuforums.org/showthread.php?t=973756")
and this other **_[link]("http://www.techthrob.com/tech/linux_virtualization.php")_** for a list and comparison of all the major virtualization software available for linux.

---

### Post by albinootje on 2009-01-28
> **gymophett said:**
> Oh, okay.. VMware server is lagging. So I'll go with virtualbox. Thanks :)

Good :)
I'd like to add that I personally really dislike the layout of VMware server, and the CLI installation can be annoying too sometimes (kernel module building problems, and vmware dhcp server problems in the LAN). 

Apart from that the download size of VirtualBox is much smaller.

---

