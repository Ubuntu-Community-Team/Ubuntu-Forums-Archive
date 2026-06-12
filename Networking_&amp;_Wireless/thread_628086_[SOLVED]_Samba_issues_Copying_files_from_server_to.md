---
title: "[SOLVED] Samba issues: Copying files from server to XP folder"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by Alt69 on 2007-11-30
Hi, a few samba issue. :)

I have set up samba on my server and am able to see the share folder on the XP laptop. In order to get access to the publci folder you need to log on. That seems to work. Have tested it out with three differnt ids all from the XP laptop. I am able to create new files and folders within the share. I am able to copy files from XP  to the server. So everything seems to be working except for the following:

1)I am not able to copy some files from my server to a folder on my XP.  I get “Cannot copy <file name> : access denied” message
2) If I create a sub-folder on XP, I am not able to add files from the server into it.

Below is my smb.conf info for the public folder:


[public]

    path = /home/public

    available = yes

    browsable = yes

    public = yes

    writable = yes

    read only = no

    guest ok = no

    create mask = 0644

    directory mask = 0755

Also, the group permissions on the file was the account that was created when I installed the server. As I am wrting the is post I am still testing things out. :)   So I changed the group permission to the public group, and I changed the Access to Read and Write. This fianaly worked.  This file was copied from another non-shared directory on the server.

I am not sure what I need to set to have the permissions to allow anyone to copy files from the public folder to their workstations. I would also like to allow users to create folders that will be shared. I am expecting all sub-folders to inherit the properties of the parent folder, but am I not sure what I am doing wrong, or maybe it doesn't work that way.

Is there a way that when a file is copied into the public share it will inherit the properties of that folder? I'm am use to the Windows environment where that is possible and would like to know how I can get the same functionality in Ubuntu.

I hope this made sense. :)

thanks.

---

