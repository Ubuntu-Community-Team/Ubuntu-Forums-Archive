---
title: "[SOLVED] How do I get server folders to auto mount on client?"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by Hayesio on 2008-07-02
Hi Guys,

I've just set up a network between my two desktop pc's - both Ubuntu boxes. One pc acts as the server and connects to the internet, then routes the internet to the other pc (client).

When on the clint PC, i can open nautilus and go to File>Connect to server, enter the details and it will allow me to access all files on the server.  The problem is, everytime i reboot the client i must do this! How can i make it do it automatically when the client boots up?

Thanks

---

### Post by ilrudie on 2008-07-03
> **Hayesio said:**
> Hi Guys,

I've just set up a network between my two desktop pc's - both Ubuntu boxes. One pc acts as the server and connects to the internet, then routes the internet to the other pc (client).

When on the clint PC, i can open nautilus and go to File>Connect to server, enter the details and it will allow me to access all files on the server.  The problem is, everytime i reboot the client i must do this! How can i make it do it automatically when the client boots up?

Thanks

What kind of file server is it?  NFS (recommended)?  SMB (Samba/windows)?  The answer for NFS is to place it in the /etc/fstab.  The caveat is that if that file server goes down you may not be able to boot from your client either without editing the fstab file and commenting out the NFS shares.  I have not done this in Ubuntu but in Solaris the boot will hang if the NFS share is not accessable and can't be mounted.  It will retry the mount indefinitly until it succeeds. [COLOR=Red] In order to overcome this you should always specify 'soft' as one of the nfs mount options in fstab.[/COLOR]

---

### Post by Hayesio on 2008-07-03
Ok, so how would i do this?

If I create a directory to mount to on the client, say: 
/home/jim/Music

Then add to fstab:
```
sftp://hayesio@192.168.0.1/home/hayesio/Music /home/jim/Music ext3 ro 0 0 

```

Then remount fstab;
```
sudo mount -a
```

Would that do it?  
What about the "soft" command option? And what about the permission to enter the servers file directory?

---

### Post by ilrudie on 2008-07-03
You probably can't mount sftp in fstab.  sftp isnt really for that kind of use.  I would suggest looking into using NFS if you want it to automount.  soft is just an NFS option in fstab that allows the mount to time out instead of retrying indefinitly until the share becomes available.  if you want to stick with sftp you will probably need to mount it once you get your graphical x session open since nautilus (an application) is handling this and not the underlying OS.  Maybe someone else can help you with this but my knowlege lies more with the underlying unix/linux rather than the gnome front end.  I'll let you know if I think of anything though.

---

### Post by Hayesio on 2008-07-04
Excellent! i setup a NFS server on the pc with internet and added the files i want to mount to fstab on the client.  Its now working perfectly.

Thanks ilrudie

---

### Post by ilrudie on 2008-07-05
Glad to help.

---

