---
title: "Configuring a remote server"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by DavidCain on 2008-04-22
Okay, I'm not very good with networking, which is why I'm posting a probably very simple question here.

We have a remote server set up in our basement and I'm trying to gain access to it. Normally, if I were running Windows, I'd open up a command prompt and type, "net use z: //SOFT-FS-01\d$ /user:SOFT-FS-01\ecain [password]" and this would, obviously, set up a drive as D$ that would allow me access to the server. I'm very new to Ubuntu, but pretty techno-savvy. Is there something I can do in the terminal to give me similar results? Thanks.

---

### Post by sammy_pal on 2008-04-22
Do you want to access shared files from the remote server?
In that case you can use nautilus to mount remote samba shares or mount from cli as smbfs
 For that install smbfs and smbclient
```
sudo apt-get install smbfs smbclient
```View available shares using
```
smbclient -L SOFT-FS-01 -U%
```Make a new folder and mount the samba share
```


mkdir share
sudo smbmount //SOFT-FS-01/share ~/share -o username=[username],password=[password],uid=1000,mask=000

```replace //SOFT-FS-01/share with the name of your shared folder

---

### Post by Iowan on 2008-04-22
One of the links in my signature tells how to mount Samba shares - Samba client *should* already be installed on the machine.  Also, **smbfs** is being (or has been) replaced by **cifs**.

---

### Post by DavidCain on 2008-04-25
While I appreciate your help, I'm mostly trying to access the files already on the server, not so much create a shared directory for me to use later. How can I do that?
*edit*
Haha, okay, I got it. I think you guys were just overthinking my question. All I had to do was open Nautilus, navigate to smb://SOFT-FS-01 and input my username and password. I'm a Linux noob, still learning. =) Thanks for the help!

---

### Post by dmizer on 2008-04-25
you have to create a new folder on your ubuntu machine, because your share will need a place to cache the remote server's contents.

second link in my sig outlines how to mount remote windows shares both manually and permanently.

---

### Post by DavidCain on 2008-04-25
I accessed the server's contents through Nautilus, and I'm copying the contents now (~100 GB of music). Do I really need to do anything more? I don't plan on using this for future storage, since I have 320GB hard drive space now.

---

### Post by dmizer on 2008-04-25
with that much data, you may run into problems with dropping packets and server diconnections if you mount via nautilus.  you'll also get much better speeds if you follow my howto, but the important thing is that you accomplish what you need so if nautilus works for you ... fantastic.

---

