---
title: "Error after recent updates"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-09
Hi,

I'm getting an error "kernel panic" after a recent set of updates. My steps as follows:

1. Install Ubuntu 8.10 on the system with Unetboot stick

2. Install Railink wireless drivers

3. Run automatic updates (includes a kernel update it seems)

4. Reboot

The result is "Kernel Panic".

I'm not sure if this is caused by the wireless driver or the updates. After this the machine is a write-off until I unplug it and restart with usb-stick-os.

Any ideas?


Richard

---

### Post by RichardCL on 2009-03-09
Here is the exact text of the error:

> Boot from (hd0,0 ext2 43762eaf-512c-4964-906a-71dbcbc603e0
starting up...
[ 0.836097] Kernel panic - not syncing: VFS: Unable to mount root fs on uknown-block (0,0)


---

### Post by Berserker v7 on 2009-03-09
Even if the new kernel causes trouble on your system, you should be able to boot into your old kernel, 2.6.27.7, i believe... you will find the entry in the grub menu... after this you can uninstall the new kernel and maybe wait for the next kernel release :)

---

### Post by binbash on 2009-03-09
Boot with your old kernel

---

### Post by RichardCL on 2009-03-09
Many thanks for the suggestions. I just did a reinstall and ran the updates using a hardwired Internet connection to see whether the problem was the kernel or wireless.

Turns out that everything worked fine. PC reboots with new kernel and all updates.

Then I installed the wireless drivers.

Now it all works. New kernel new wireless. Can't explain it. It just works.

---

