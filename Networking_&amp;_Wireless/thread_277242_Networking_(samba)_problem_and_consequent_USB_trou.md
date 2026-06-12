---
title: "Networking (samba) problem and consequent USB trouble"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by Mallgur on 2006-10-14
Hi;

I post this question here because it is primarily related to networking. The secondary problem I'll mention derives from this inabillity to network properly.
I'm just getting started with Linux but have a long history in dealing with computers on several different OSes though.

First things first, the setup:

2 machines wired using a cross cable, both with fixed IP addresses.
One is a XP box that is connected to the Internet.
The other is an old laptop that is running Xubuntu and accesses the internet fine using the shared connection from the XP machine. This machine has an external USB hard disk connected and working properly.

The objective:

To be able to copy files from the external USB hard disk to the XP box over the network.

The problem:

Since the Xubuntu box accesses the internet using the shared connection of the XP box, the networking hardware and basic configuration is clearly ok.
The problem is that when I try to share a folder on the external USB hard disk using System->Shared Folders I mange to get the XP box to see the Laptop, but I can't access it. When asked for a username and password I put them in, but the authentication fails. I tried both SMB and NFS on the Shared Folders but the problem is the same.

A different attempt:

I tried using SMB4K and Kwallet to try and use the network in the opposite direction, i.e., accessing shares on the XP from Xubuntu, but even though I did manage to browse the shares, I can't write to them. In spite of setting up Read&Write on SMB4K the writing always fails.

The spinoff problem:

The only way I manage, at present, to copy files from one machine to the other is disconnecting the external USB drive from the Xubuntu box and connecting it to the XP.
The problem is that when I reconnect it to the Xubuntu box, it gets a different 'name'... It usually is /media/sda1 and that is where aMule is placing all the files. But when I reconnect it it becomes /media/sdb1 and so aMule doesn't find the correct dirctories.
I do go to System->Disks and Disable the partition before unplugging the External USB disk, but it happens just the same. I checked mount after this and /media/sda1 is not present so I figure it should take the same mount point when replugged, no?

Sorry for the lengthy post but I think it is preferable to provide as much information as possible when asking for help in order to make it easier for those who are kind enough to reply.

Thanks for any help.

---

### Post by kidders on 2006-10-14
Hi there,

The best (most reliable) way to handle sharing with samba is to do it yourself, by manually editing your smb.conf, and manually setting your access passwords with smbpasswd. That way, you always know exactly what's happening :-) Don't forget to restart the samba service every time you make a change.

Your other issue is well-known, and has good solutions :-) It would take far too much space to explain it all here, but the idea is:

[LIST=1]
[*]Teach your PC how to distinguish your external hard drive from every other USB device you might plug in.
[*]Have Ubuntu create a /dev entry called, say, /dev/usbhd, and associated entries for each partition on the disk (/dev/usbhd1, /dev/usbhd2...)
[*]Use the new /dev entry to in your /etc/fstab rule, to ensure your disk always uses the same mount point(s).
[/LIST]

Give [this Google search]("http://www.google.ie/search?rls=en&q=udev+rules&ie=UTF-8&oe=UTF-8") a try. What you're interested in is creating things called "udev rules". Udev is the system that controls the names & permissions of the stuff in /dev.

Hope that helps.

---

### Post by Mallgur on 2006-10-14
:) 

Ok. I now manage to get access to the laptop but only if I authenticate as root.
When I try to use smbpasswd using my login I get a Logon_Failure error to 127.0.0.1 ... Maybe my old password is wrong? I don't remember setting one for myself so I don't know if that could be the problem.

Thanks a lot for your reply. Editing the smb.conf file at least let me access the shares now.

I'm going to check out the google search you gave to see about the other issue.

---

### Post by kidders on 2006-10-14
> **Mallgur said:**
> I'm going to check out the google search you gave to see about the other issue.

Kewl :-) Knowing that your external devices will always turn up in the same places in /dev is tremedously convenient.

With regard to your password, I'm not clear on whether you're referring to your Linux password, your Samba password, or your Windoze password. :???: Sorry.

To access local samba shares remotely, you need to set yourself a password first, usually with smbpasswd.

---

