---
title: "sharing files on a dual boot system?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by psy-moon on 2009-05-16
Greetings all, can anyone answer this ?
I have a dual boot system with multiple hard drives. 
Windows XP and ubuntu studio . I have files on a slave nfts hard drive that I share across my local network. Can I configure  these files so they continue to be shared when ubuntu is running. I understand I have to set ownership and permissions for the files in ubuntu, but will this affect how they work when windows is running?

---

### Post by psy-moon on 2009-05-16
great I get to answer my own thread. So here's how one enables files that are shared in your windows file system to be shared in ubuntu.
Check synaptic package manager, under networking and see if you have "samba" installed.
open a terminal and type

 ```
   sudo gedit /etc/samba/smb.conf 
```this opens the samba config in a text editor.

look at the [global] section at the top it says
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```change the domain name to match your windows LAN workgroup name.
At the end of the [global] section add

```
# To enable sharing on windows directories
    usershare owner only = False
```now you can add ubuntu shares to windows folders and they will be available on your windows network.
Navigate to the folder you wish to share, right click it choose sharing options and check " Share this folder" _and_ "Guest access".

After a reboot my shared folders are now available to my spouse weather I'm running windows or ubuntu;
 cool
now, I am an absolute beginner, so please correct me if I did it wrong.

---

### Post by Joeb454 on 2009-05-16
If you have the Windows install on another internal hard drive or partition, you can use ntfs-config to auto mount the drive on startup, and then just copy files from Ubuntu - Windows.

This way, you can save files TO the windows partition, and windows wouldn't know the difference.

There's a guide on how to do it in my sig :)

---

