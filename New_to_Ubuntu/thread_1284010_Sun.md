---
title: "Sun"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by mbzn on 2009-10-06
Hi, I've installed Sun Virtualbox and it failes to boot a newly created box, i called 'k'. 

It comes up with the following:

Failed to start the virtual machine k.
VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).

And i have no idea what to do here to make it work.

Any help appreciated.

---

### Post by alphaniner on 2009-10-06
> **mbzn said:**
> VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).

KVM and VMX are both related to virtualization.  Apparently the Ubuntu UE folks made some changes to the kernel because I've never had a problem running VBox.  IOW, I think you are not running the official Canonical kernel.  As the error states, you're going to have to recompile your kernel.  Or maybe you could try getting an official kernel.

---

### Post by farsight on 2009-10-06
Hi there,

Have you ensured that your Ubuntu user name is part of the virtual box user group. I am not on Ubuntu now but I believe if you look under Administration > Users and Groups, you should be able to unlock the user controls, scroll in to the groups you have access to and highlight virtual box.

Farsight

---

### Post by mbzn on 2009-10-06
Hi,
Thanx for the replies.

I have added myself to the vbox users, so that is not the case, as for the UE theory, The same vbox version runs perfectly fine on both my other systems that has the exact version of UE (ie. 2.3) and it is the exact kernel as UE is only loads of packages and looks that is added to the official release.

Any more ideas?

---

### Post by urugTON on 2009-10-06
The error has to do with the fact that you have VMX capabilities in your CPU, BIOS and Kernel. VirtualBox is not happy with that combination. You'll have to find a way to make VBox happy. You'll likely have to unload the KVM modules in your kernel.

I ran into this as well, but I just moved Virtual Box to an older machine. I've very happy with VBox, BTW. To check that you machine has the virtualization hardware available do the following:

```

egrep '(vmx|svm)' --color=always /proc/cpuinfo

```

If you get any output, the CPU and BIOS support the feature. FWIW, vms is Intel, svm refers to AMD.

VirtualBox's complaint has to do with the KVM kernel module being loaded.  You can check that with:
```
sudo modprobe kvm
```

If you get a response, it'll indicate that two modules are loaded.  One is the generic KVM module and the other is the module specific to either Intel or AMD, depending on your CPU.

Please be careful with the next command.  I'm not where I have access to a machine running KVM to try it for you.  My google search, however, turned this up in a reliable location:
   [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/292588](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/292588)

```
sudo /etc/init.d/kvm stop
```

The alternative is to do a modprobe -r command.  Stopping the service is a much better way of dealing with the issue.

At this point you should be able to start your VirtualBox VM.

Please let us know how this worked for you.

---

### Post by mbzn on 2009-10-07
Thanx urugTON

This worked.

---

