---
title: "Cannot access samba share from Ubuntu"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2008-04-19
OK, I am new to this whole networking thing, so I could be way off here.

My goal is to be able to access the shared folder on my desktop from my laptop within my home network. I set the folder to be shared via samba (I do not know how to configure the unix network thing), and I can access it from a windows laptop, but not from my ubuntu laptop. I go to Network and open the desktop computer "BLACKDIAMOND", and it says in the title bar smb://blackdiamond...it works for a while, then says it is unavailable. Should I not be using samba for this? I would sort of like to because I want to be able to access the shared folder from windows and ubuntu alike. I have assigned a password using smbpasswd from the terminal on the desktop, so that's not the issue. What am I doing wrong? I don't even get a login prompt on the ubuntu laptop.

-Dan

---

### Post by fsmithred on 2008-04-20
There's probably a way to do it, but I've never been able to access samba shares from a linux client. You can use NFS to share files between linux boxes, and it's easier to set up than samba. (If you're planning on sharing files across the internet, NFS is not the most secure choice.)

Here's a guide to setting up NFS. 
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

There's some good information about security in this guide, but I don't use any of that. I'm on a home network with only me, behind a hardware firewall, so my basic setup entails:

install nfs-kernel-server and portmap
edit (create) /etc/exports, which has one line describing the share
edit /etc/fstab on the client so that my user can mount the share
restart the service and mount the share

see man exports, man mount, and man fstab for details on editing these files.


Edit: see this thread, too. I think it has the answer to your question.
[http://ubuntuforums.org/showthread.php?p=1492284](http://ubuntuforums.org/showthread.php?p=1492284)

---

### Post by jonandrews on 2008-04-20
Have a look at my step-by-step Ubuntu / Windows networking guide:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by dbsoundman on 2008-04-20
Thanks fsmithred and jonandrews. However, I have some issues.

First, is it possible to share a folder with samba and NFS at the same time? Currently when I go to the shared folders controls, I can only choose one or the other. I would like to be able to do both.

The other thing is, NFS seems really kind of difficult in relation to working with samba. It just seems silly that networking Ubuntu with Windows is really easy, but the converse is rather involved and inflexible. Am I missing something?

-Dan

---

### Post by dbsoundman on 2008-04-20
I just tried NFS using that website manual link, and no success. I get a message saying the connection times out from RPC or something like that, or I also get a message saying that the directory I want to mount it to on the client does not exist. For example, I put in sudo mount 000.000.0.00:/home/username /home/username/servername, and it tells me that the directory /home/username/servername does not exist, which is true, it does not. Do I need to create the directory first?

-Dan

---

