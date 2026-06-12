---
title: "How do I best Place VirtualBox VM's outside of /home Sub-Directories/Partitions?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-04
I have just installed VirtualBox PURL and find that it uses my /home partition for installation of virtual machines and fills my /home with VM's quickly. I only backup my /home partition and use it for clean installs. When I do a fresh install of Lucid 64 bit (from my present Karmic 32 bit OS), can I have a partition that holds VirtualBox machines outside of my /home partition? I am not interested in backing up any VM's. I know the path for VirtualBox is /usr/bin/VirtualBox. So, could I create a /usr Partition and have VirtualBox install in that Partition? If so, would that install the Virtual Machines on that Partition and not in /home; so my /home partition remains manageable for backups. 

Or, is this accomplished a better way?

Thanks.

---

### Post by drzoo2 on 2010-02-04
> **mikodo said:**
> I have just installed VirtualBox PURL and find that it uses my /home partition for installation of virtual machines and fills my /home with VM's quickly. I only backup my /home partition and use it for clean installs. When I do a fresh install of Lucid 64 bit (from my present Karmic 32 bit OS), can I have a partition that holds VirtualBox machines outside of my /home partition? I am not interested in backing up any VM's. I know the path for VirtualBox is /usr/bin/VirtualBox. So, could I create a /usr Partition and have VirtualBox install in that Partition? If so, would that install the Virtual Machines on that Partition and not in /home; so my /home partition remains manageable for backups. 

Or, is this accomplished a better way?

Thanks.

Virtualbox has a preference setting for moving the default location for harddisks and VMs. I moved my VM to the /opt folder for the very reason your asking. So i'm not backing up gigs of vm images.

---

### Post by howefield on 2010-02-04
> **mikodo said:**
> can I have a partition that holds VirtualBox machines outside of my /home partition?

You would install Virtualbox in the normal way, but when it comes to creating the virtual disk for your vm, place it where ever you like.

When you reach the attached screen shot, click on the folder icon to the right of the Location filed, and navigate to where you want your virtual disk to be created, which could be on a separate partition or even separate (for best performance) hard disk .

---

### Post by mikodo on 2010-02-04
> **howefield said:**
> You would install Virtualbox in the normal way, but when it comes to creating the virtual disk for your vm, place it where ever you like.

When you reach the attached screen shot, click on the folder icon to the right of the Location filed, and navigate to where you want your virtual disk to be created, which could be on a separate partition or even separate (for best performance) hard disk .

Thanks guys, I missed the option where to place the VM's

Mike

---

