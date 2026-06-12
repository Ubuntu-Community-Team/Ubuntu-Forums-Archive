---
title: "Use USB Ubuntu with Virtual Box"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-25
Hi Forum,

I'm having all sorts of issues installing from a USB with Karmic on my 64bit desktop.

Meanwhile my main machine (32bit laptop) is working fine with 9.04 and also running virtual box.

Can I use Virtual box to test my USB key? I'd need to boot from and run with the x64 installation on the virtual machine, even though the host hardware is 32bit.

I tried the boot options and only get options HDD, CD or flopppy. I'm using PUEL version and the filter is on so that Virtual Box can see the USB key.

Thanks


Richard

---

### Post by longtom on 2009-10-25
> **RichardCL said:**
> Hi Forum,

I'm having all sorts of issues installing from a USB with Karmic on my 64bit desktop.

Meanwhile my main machine (32bit laptop) is working fine with 9.04 and also running virtual box.

Can I use Virtual box to test my USB key? I'd need to boot from and run with the x64 installation on the virtual machine, even though the host hardware is 32bit.

I tried the boot options and only get options HDD, CD or flopppy. I'm using PUEL version and the filter is on so that Virtual Box can see the USB key.

Thanks


Richard

On my VirtualBox in settings > CD I can check "Enable Passthrough".  After that I can use any .iso file I choose from a mounted drive.

Good luck.

---

### Post by RichardCL on 2009-10-25
> **longtom said:**
> On my VirtualBox in settings > CD I can check "Enable Passthrough".  After that I can use any .iso file I choose from a mounted drive.

Good luck.

Thanks for the answer. I'm not sure I've understood though.

Once I use the "create USB" to make the USB disk there is no ISO on the USB disk. What I need to do is boot the LiveUSB from Virtual Box but I don't see a way to make the system look to the USB for a boot image (like a missing BIOS setting on a PC).

---

### Post by longtom on 2009-10-25
> **RichardCL said:**
> Thanks for the answer. I'm not sure I've understood though.

Once I use the "create USB" to make the USB disk there is no ISO on the USB disk. What I need to do is boot the LiveUSB from Virtual Box but I don't see a way to make the system look to the USB for a boot image (like a missing BIOS setting on a PC).

Sorry - I misunderstood you.  I have never done that.  That is probably like integrating an existing installation into a virtual machine.  There is a way - but way above my fireplace.

Hope you find somebody more knowledgeable.

Maybe try the Virtualization Forum.

---

