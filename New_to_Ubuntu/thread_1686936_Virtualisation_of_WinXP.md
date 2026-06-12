---
title: "Virtualisation of WinXP"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Brad wilkinson on 2011-02-13
Hello,

I've tried to set up a virtualised Windows XP (32 bit) OS on my Ubuntu 10.04 x86-64 Phenom x6 PC. I got the windows install to run through (it is a clean XP sp3 install from original media), but after shutting down the whole PC, now when I restart and go into the Virtual Machine Manager in Applications->System tools and go to localhost (QEMU) and then try to start the winXP image, I end up with the following error message:

Error starting domain: monitor socket did not show up.: Connection refused

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused


I posted this in the virtualisation subforum, but didn't get replies. Can anyone help?

---

### Post by Paqman on 2011-02-13
I've not really ever used QEMU much so can't help there, but if you don't get it sorted you might want to take a look at Virtualbox. I've never had any kind of hassle from it setting up any kind of VM.

---

### Post by wep940 on 2011-02-13
+1 for VirtualBox - very easy to setup and use, no hassles.

---

### Post by RJ12 on 2011-02-13
As everyone is saying, using VirtualBox will help you a lot more. I have never had any problems using VirtualBox, or even VMware Player. Never have tried QEMU though.

---

### Post by shunan on 2011-02-13
have a look at /var/log/libvirt/qemu/virtual_machine_name.log

---

