---
title: "Running an old windows installation in virtualbox"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Hospadar on 2008-12-14
I'm in the process of moving my dad to ubuntu, and I've gotten the few windows apps he needs that don't run in wine running great in a virtual machine in VirtualBox, but I'm wondering if there's a way to run his old windows installation inside VirtualBox (it's on a seperate hard drive) so he doesn't have to migrate all the old stuff he has on that machine.

Thanks,
L-tronix

---

### Post by linuxguymarshall on 2008-12-14
I dont know much about visualization but from what I know the file is has is basically just the contents of a hard drive in a container. So Google around.

---

### Post by davec64 on 2008-12-14
Hi,

Have a look at this thread:[http://ubuntuforums.org/showthread.php?t=882170]("http://ubuntuforums.org/showthread.php?t=882170")

It gives a link to a HOWTO that might be of interst to you.

---

### Post by jbrown96 on 2008-12-14
I doubt it's possible. I think that Vmware can convert between the two, but the drm/drivers on Windows won't allow it. It's the same reason that you can't move a hard drive from one computer to another even if it has the exact same hardware because the serial numbers are different. I would imagine it would be even worse since Virtualbox "virtualizes" the hardware into generic devices. It would look like a completely different system to Windows, and I imagine it will refuse to work at all. 
I'd recommend a clean install. It will run much faster, and if he's not going to be using it much, you don't need antivirus either.

---

### Post by solwic on 2008-12-14
> **jbrown96 said:**
> 
I'd recommend a clean install. It will run much faster, and if he's not going to be using it much, you don't need antivirus either.

Ditto.  I'm pretty sure it is possible, but it's hard, and the clean install would be much simpler to both initiate and maintain, I would think.  

Best of luck!

---

### Post by albinootje on 2008-12-14
> **Hospadar said:**
> I'm in the process of moving my dad to ubuntu, and I've gotten the few windows apps he needs that don't run in wine running great in a virtual machine in VirtualBox, but I'm wondering if there's a way to run his old windows installation inside VirtualBox (it's on a seperate hard drive) so he doesn't have to migrate all the old stuff he has on that machine.

Thanks,
L-tronix

I have experience with this, with both VirtualBox and VMware.

I'm not a fan of VMware at all (for various reasons), but their tool makes this pretty easy :
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)
It's a free-of-charge download.

You can use the free-of-charge vmware-server to run it after the conversion. (I find that easier to deal with than their vmware player).

For VirtualBox it can be much harder, but it depends also on the Windows-version.
As far as i know MS-Windows98 could be moved from one machine to another, but with MS-Windows 2000 this was already a problem.

I've managed to migrate a physical Windows2000 installation into VirtualBox for some friend, but that was hard work, and i could not reproduce this usually with success in other places, sometimes spending many hours on it.

---

