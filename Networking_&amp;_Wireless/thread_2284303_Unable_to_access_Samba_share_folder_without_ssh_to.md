---
title: "Unable to access Samba share folder without ssh to the server"
date: 2015-06-28
forum: Networking &amp; Wireless
---

### Post by Xiaochuan on 2015-06-28
I have two machines (Ubuntu server 14.04 and Mac OS 10.9.5). I intend to install Samba server on a dedicated Ubuntu server and access the shared folder from Mac OS. 

The issue I am encountering is that I am unable to access the shared folder unless I ssh the Server and keep the tunnel open. Once the share folder is open, I can close the ssh terminal and read/write works fine on the shared folder. So it looks like that ssh connection is compulsory in my case,  I assume that ssh is not needed for Samba. Has anyone had the same issue before? or any ideas for troubleshooting? 

I have also tried to access the share folder from a Windows 7, and the same issue exists. So I guess the issue is on Ubuntu side. 

My smb.conf is:

[<folder_name>]
path = /home/<user_name>/<folder_name>
available = yes
valid users = <user_name>
read only = no
browseable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777

Furthermore, I have tried to share the same folder via sshfs and it works fine. Many thanks in advance.

---

### Post by Lars Noodén on 2015-06-28
Just a guess, but do you have home directory encryption turned on for any of the affected users?

---

### Post by Xiaochuan on 2015-06-28
Hi Lars, 

Thanks for your reply. I found a file named .encryptfs in my home folder, does it indicate what you said?

This could be generated from sshfs that I installed, so it explains everything now. Thanks a lot!

---

