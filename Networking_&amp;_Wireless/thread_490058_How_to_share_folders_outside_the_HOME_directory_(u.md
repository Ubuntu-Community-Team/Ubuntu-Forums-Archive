---
title: "How to share folders outside the HOME directory? (using Samba)"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by feistybird on 2007-07-02
Hello,

I have question about Ubuntu "shared folders"

I can share folders in my home directory, and Windows users can browse it without any problems

but if the shared folder is located outside /home/users, for example, "/media/My-USB-HDD", then the Windows users can see this folder name in the Network Neighborhoods, but still unable to access it.

Is there anything I've to edit additionally in my /etc/samba/smb.conf?

Thanks !

---

### Post by dfreer on 2007-07-02
Check out ubuntuguide.org, they have some good how-to's for SMB file sharing. Specifically this Section:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)
Scroll down to the options about sharing a public folder, and tailor the commands as you need them.

---

### Post by feistybird on 2007-07-03
Thanks for your reply.

I did follow that guide and shared my public folders successfully, but am only able to share public folders in my "/home/user/" folders.

Any folders outside "/home" are still not accessable by the Windows Network Neighborhood.

I did set chmod 777 to these folders, 

I have tried both "Seurity = Share" and  "security = user"  + "username map = /etc/samba/smbusers", but still no go...

Below is my shared folder settings:

[public]
  comment = Public Folders
  path = /media/USBHDD/share
  public = yes
  writable = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

any ideas?

Thank you!

---

### Post by feistybird on 2007-07-04
Sorry I was wrong,

File Sharing outside home folder (ie. "/etc" "/bin" ) were actually all OK.

The only exception was in the /media/My USB Hard Disk

The reason was that Ubuntu's USB automount automatically created a folder on '/media/my-usb-hdd-name' with root-only Group permission, and cannot be modified even with" sudo chmod" or "sudo chown", causing the Samba clients failed to access the mounted USB Drive due to folder permissions.

The solution is to have the USB Drive mounted by the /etc/fstab

ex. 

/dev/sdd1 /media/usbdisk auto rw,user 0 0

Then next time when Ubuntu proceeds an automount of the same USB Hard Drive in /media/usbdisk, the  umask will be set to 000 (umask=000), so everyone can access it,  include the Samba users.

---

### Post by dfreer on 2007-07-04
Good catch!

---

