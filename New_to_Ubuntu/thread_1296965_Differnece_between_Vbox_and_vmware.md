---
title: "Differnece between Vbox and vmware ??"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-10-21
my distro is ubuntu jaunty ,and i want to host window$ xp on an virtual machine ,so i need to know what's the difference between VB and VMware in order to chose the  appropriate one for host such OS ?? THNXXX

---

### Post by MelDJ on 2009-10-21
you pay for vmware but virtualbox is free. 
vmware has better directX support

---

### Post by konqueror7 on 2009-10-21
well, theres really no difference, only maybe the version and per functions they offer with each. but both do provide virtualization.

personally, i would recommend using vbox, as it is, say, much faster as compared to its counterpart, but nevertheless, its still dependent on your hardware, a multi-core cpu and minimum of 2gb of ram would do...

---

### Post by Dougie187 on 2009-10-21
You only have to pay for vmware server, which is what you use to make the guest. However there is a free trial you can use to make your guest, and then you could use vmware player to use the guest vm.

---

### Post by howefield on 2009-10-21
Feature comparison here

[http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

---

### Post by MBG1987 on 2009-10-21
THNXXX , I really like the free software ,even if it's not better than the non-free one !
so my choice after these nice replies will be vmwa...  o0ps I mean  Vbox ,lol

---

### Post by alphaniner on 2009-10-21
> **Dougie187 said:**
> You only have to pay for vmware server, which is what you use to make the guest.

No.

[100% Free VMware Server]("https://www.vmware.com/products/server/")

I use it at work because I need to directly access SCSI devices, which VBox cannot do.  That said, VMware Server has not had an update in many months, and the java-based web interface is a lethargic, buggy PITA.  At home I use VBox.

---

### Post by cwmoser on 2009-10-21
I use VMware - its great, but I would like to use VirtualBox if I can find a tool to migrate my Virtual Machines to VirtualBox.

A lot of VMware is free - both the VMware player and server are free.  You use the server to make VM's and play them.  The player just plays the VMs.  After the VM's are created, I prefer the look and feel of the player.

I use VMware server 1.06 because all the later versions just plain suck - i.e. slow, buggy, etc.   1.06 works great on Windows at work and on Ubuntu at home.

There is another VMware free tool - VMware Convert which will convert a physical machine to a virtual machine.  I find this tool to be very useful to migrate working OS's to VM format.

VMWare runs pretty fast on both Windows and Ubuntu - but I read that VirtualBox and KVM are faster.

Carl

---

### Post by howefield on 2009-10-21
> **cwmoser said:**
> I use VMware - its great, but I would like to use VirtualBox if I can find a tool to migrate my Virtual Machines to VirtualBox.

I believe virtualbox supports VMware virtual machines. (as per feature list link supplied above)

---

### Post by Dougie187 on 2009-10-21
> **alphaniner said:**
> No.

[100% Free VMware Server]("https://www.vmware.com/products/server/")

I use it at work because I need to directly access SCSI devices, which VBox cannot do.  That said, VMware Server has not had an update in many months, and the java-based web interface is a lethargic, buggy PITA.  At home I use VBox.

Thats pretty cool. Thanks, However, that link that someone posted previously says that Vbox supports SCSI devices. Though that might not be quite what you meant, I just thought I would point it out.

---

### Post by niteshifter on 2009-10-21
> **Dougie187 said:**
> Thats pretty cool. Thanks, However, that link that someone posted previously says that Vbox supports SCSI devices. Though that might not be quite what you meant, I just thought I would point it out.

Vbox supports *virtual* SCSI devices (it emulates SCSI controllers from LsiLogic and BusLogic), *directly accessing* SCSI: No.

What's the use of Vbox' SCSI emulation? So you can import a VMWare VMDK that was built using SCSI.

---

