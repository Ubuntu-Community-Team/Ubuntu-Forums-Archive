---
title: "Linux can't read directly from a Samba share"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by alimovz on 2006-11-22
Hello,

Here is my problem. I have two boxes at home one is running Linux and the other is dual boot Linux and Windows. I have all my music on the first one and share the folder with that music though samba. 
So if I boot into Windows XP on the other machine I access this share and can easily play all my music directly from the samba share on my Linux box. Now if I boot into Linux on on the same machine, I can still access the samba share with music but cannot play those files unless I download them onto my file system, which completely defeats the purpose of me having another server for my files. 
Does anyone know how to enable my Linux box to play those files directly off of the remote server? I just wanna be able to open the share in a different window and double click the file and play it. 

Thanks for any help.

---

### Post by andrewc6l on 2006-11-22
It sounds as if you haven't mounted the Samba share. Try (from a terminal):

[FONT="Fixedsys"]sudo mount -tcifs -ouser=[FONT="Arial"]<same username you use to mount the share on Windows>[/FONT],pass=[FONT="Arial"]<same password you use to mount the share on Windows>[/FONT] //your-linux-fileserver-name/your-share-name /mnt[/FONT]

If that works, you should be able to see the share with:
[FONT="Fixedsys"] ls /mnt[/FONT]

Assuming that's the problem, you can edit /etc/fstab to mount the file system automatically. I'm doing exactly what you're doing, and my fstab has:

[FONT="Fixedsys"]//myserver/music        /music  cifs    credentials=/etc/samba/credentials/myserver     0       0[/FONT]

Then I created an /etc/samba/credentials/myserver file which contains:
[FONT="Fixedsys"]username=myuser
password=mypass[/FONT]

Make sure you have a /music directory, then
[FONT="Fixedsys"] sudo umount /mnt
 sudo mount -a[/FONT]
... and ls /music should show you what you want. (And more to the point, will also do that next time you boot.)

If ls /mnt doesn't show your files (the file system fails to mount) then you should look into /etc/samba/smb.conf on the server (make sure your client has access) and make sure you don't have a firewall blocking the Samba ports.

  - Andrew

---

### Post by marx2k on 2006-11-27
Im sorry, what is CIFS? I always use smbfs to mount samba shares. Should I be using cifs?

---

### Post by andrewc6l on 2006-11-27
cifs is a more modern version of sambafs. It's a little better at handling large files (>2G).
[http://de.samba.org/samba/Linux_CIFS_client.html]("http://de.samba.org/samba/Linux_CIFS_client.html")

 - Andrew

---

