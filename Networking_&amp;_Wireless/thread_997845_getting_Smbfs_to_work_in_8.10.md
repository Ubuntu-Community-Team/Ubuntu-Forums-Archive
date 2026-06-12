---
title: "getting Smbfs to work in 8.10"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2008-11-30
Hi;

I am trying to get smbfs working in 8.10.  I have found the following thread but as a fairly new guy to ubuntu i need a little bit more detail to the process / bash commands.

[http://ubuntuforums.org/showthread.php?t=707370](http://ubuntuforums.org/showthread.php?t=707370)

Help well recieved thanks.

---

### Post by geekyhawkes on 2008-12-01
Anyone able to give me a chat through this please?

---

### Post by albandy on 2008-12-01
Exactly what do you want to do with smbfs, share volumes or acces them?

---

### Post by albandy on 2008-12-01
mount a volume from console:

sudo smbmount  //smbserver.yourdomain.extension/user$ /mnt/samba -o username=yourusername,workgroup=YOURWORKGROUPORDOMAIN

if you want do do it automatically when a user logs in I recomend you pam_mount

---

### Post by geekyhawkes on 2008-12-01
Sorry, i should have been more clear.  I have been having lots of problems getting my freecom network drive to work correctly with smb and I was hoping to try smbfs just to rule out any cifs incompatibilty.  The drive worked fine under windows, and always works via ftp.  THe problem i have is that i cannot get it to mount via fstab so i wanted to use smbfs and see if that helped. 

albandy, i was under the impression i had to compile smb from source if i wanted to use smbfs?  The nas netbios name is FND and the share i am after is PUBLIC so should i type

sudo smbmount //FND/PUBLIC/username$ /mnt/samba -o username=username,workgroup=workgroup   ???

Sorry im just a bit confused about the .extension/user$ bit.  

Im guessing pam_mount would remove the need for an entry in fstab?

Thanks for your help.

---

### Post by albandy on 2008-12-01
The $ means hidden in windows shares, in my case the home directory is hidden so I should use a $ at the end.

for example, if you are sharing a folder with share name music you'll mount this way:

sudo smbmount //FND/PUBLIC/music /mnt/samba -o username=username,workgroup=workgroup

---

