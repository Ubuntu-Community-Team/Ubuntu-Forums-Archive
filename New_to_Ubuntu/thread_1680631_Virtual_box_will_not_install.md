---
title: "Virtual box will not install"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by degarb on 2011-02-02
I have tried virtual box 4, ose and ose dkms.  I have recompiled and updated kernel, apt update.  It is telling me vbox driver not found.

I have tried numberous directions of various googled sites.   

error:  addgroup: The group `vboxusers' already exists as a system group. Exiting.
update-rc.d: warning: vboxdrv stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                 
Error! Your kernel headers for kernel 2.6.35-25-generic cannot be found at
/lib/modules/2.6.35-25-generic/build or /lib/modules/2.6.35-25-generic/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                       
 * Look at /var/log/vbox-install.log to find out what went wrong
Processing triggers for python-central ...

---

### Post by quesadilla on 2011-02-02
have you tried loading it from the Ubuntu forums? that's how I got it. it should run perfectly from there

---

### Post by wilee-nilee on 2011-02-02
If you want a usb connection, for a HD or thumb you need the puel version off the site. You also need to add yourself to the vbox in users=system-admin-users and groups-manage groups, navigate to vbox users, click properties, open and tick you user name.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by degarb on 2011-02-03
> **quesadilla said:**
> have you tried loading it from the Ubuntu forums? that's how I got it. it should run perfectly from there

What is url?

---

### Post by SeijiSensei on 2011-02-03
> **degarb said:**
> I have tried virtual box 4, ose and ose dkms.  I have recompiled and updated kernel, apt update.  It is telling me vbox driver not found.

 * Trying to register the VirtualBox kernel modules using DKMS                 
Error! Your kernel headers for kernel 2.6.35-25-generic cannot be found at
/lib/modules/2.6.35-25-generic/build or /lib/modules/2.6.35-25-generic/source.


Are you using a kernel you compiled yourself, or the stock 2.6.35-25-generic?  If it's your own kernel, you'll need to muck with the Virtualbox kernel module code to point it to the kernel source so it can find the needed headers.

If you're using the stock kernel, you need to install linux-headers-2.6.35-25-generic.

---

### Post by degarb on 2011-02-03
> **SeijiSensei said:**
> Are you using a kernel you compiled yourself, or the stock 2.6.35-25-generic?  If it's your own kernel, you'll need to muck with the Virtualbox kernel module code to point it to the kernel source so it can find the needed headers.

If you're using the stock kernel, you need to install linux-headers-2.6.35-25-generic.
 
This is very helpful. 
Some other pinhead customized it, perhaps compiling the kernel with the bcm drivers.  I will try and report back.

---

### Post by degarb on 2011-02-04
> **SeijiSensei said:**
> 

If you're using the stock kernel, you need to install linux-headers-2.6.35-25-generic.

Thanks, That did it!  Some relief at last.

Now, since I installed ose and xp under, I need to know how to upgrade without removing my vdi.

---

