---
title: "copying between virtual machines running ubuntu"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by zubani05 on 2011-08-10
Hi,

Please, I am currently using a windows7 laptop on which I created 3 virtual machines using vmware. Please how do I copy documents and programs from one virtual machine to another.

Cheers,
Zuby.

---

### Post by stefangr1 on 2011-08-10
As the free versions of vmware do not support a shared drive, this is always a little invonvenient. What I suggest is you share a directory on the windows host to the network. The Ubuntu vm's should then be able to find it easily.

---

### Post by penguintower4245 on 2011-08-10
Try using virtualbox its as good as vmware and its free .

---

### Post by haqking on 2011-08-10
> **zubani05 said:**
> Hi,

Please, I am currently using a windows7 laptop on which I created 3 virtual machines using vmware. Please how do I copy documents and programs from one virtual machine to another.

Cheers,
Zuby.


shared folders or shared clipboards.

create a shared folder on your host to which the VM's can connect to.

or copy and paste between guest and host then back from host to other guest

---

### Post by stefangr1 on 2011-08-10
> **penguintower4245 said:**
> Try using virtualbox its as good as vmware and its free .

VMWare Player and Server are free as well.

Setting everything up again in VirtualBox is probably going to require some work, while the programmes are pretty much equivalant. I doubt whether switching to VirtualBox will be worthwile for the OP.

---

### Post by haqking on 2011-08-10
> **stefangr1 said:**
> VMWare Player and Server are free as well.

Setting everything up again in VirtualBox is probably going to require some work, while the programmes are pretty much equivalant. I doubt whether switching to VirtualBox will be worthwile for the OP.


you can use a Vmware hard disk .vmdk in virtual box, takes a few seconds.

however for the OP then as said you cna use shared folders, depedning on whether you have Vmware workstation or whatever you use then set up shared folders.

You might need Vmware tools installed.

here is an old link but can be adapted [http://www.vmware.com/support/ws5/doc/ws_running_shared_folders.html](http://www.vmware.com/support/ws5/doc/ws_running_shared_folders.html)

---

### Post by zubani05 on 2011-08-10
hey haqking tx, i tried copying manually from the folder of the old vm on my host to the folder of the new vm on my host.Is dt what you meant?

---

### Post by haqking on 2011-08-10
> **zubani05 said:**
> hey haqking tx, i tried copying manually from the folder of the old vm on my host to the folder of the new vm on my host.Is dt what you meant?


no i mean when you have a virtual machine up and running if the machine is setup to have a shared clipboard then you can copy from your host into the virtual machine or back.  Or you cna set up shared folders so that your virtual machines can commonly access files from a folder stored on your host.

---

### Post by scorp123 on 2011-08-10
> **zubani05 said:**
>  Please how do I copy documents and programs from one virtual machine to another. You could use Dropbox for this. URL:
[http://www.dropbox.com](http://www.dropbox.com)

Dropbox works tip top on Linux, Windows and Mac OS X, no matter if 32-bit or 64-bit. You just drag & drop files into the "My Dropbox" folder and they will be automatically copied over to the other PC's and VM's (for Dropbox it's all the same) associated with your account.

---

### Post by haqking on 2011-08-10
> **scorp123 said:**
> You could use Dropbox for this. URL:
[http://www.dropbox.com](http://www.dropbox.com)

Dropbox works tip top on Linux, Windows and Mac OS X, no matter if 32-bit or 64-bit. You just drag & drop files into the "My Dropbox" folder and they will be automatically copied over to the other PC's and VM's (for Dropbox it's all the same) associated with your account.

But doesnt that rely on Internet Connectivity ? I mean i know it works offline but it has to be sent initially right ? not quite the same as just a shared folder on your host ?

---

### Post by scorp123 on 2011-08-10
> **haqking said:**
> But doesnt that rely on Internet Connectivity? Good point.

---

