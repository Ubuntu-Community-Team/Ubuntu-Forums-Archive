---
title: "file sharing"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by stevepoppers on 2009-10-09
I've been searching, and finding it hard to understand. My situation:

I have a desktop running Jaunty Server. I want to share files and folders on that computer over my network, so I don't have to drag my damn external drive around the apartment. The other computers on the network also run Jaunty (Desktop).

Is there not a fairly quick/easy way to do this?

It's quite possible I'm mistaken, but I get the impression that Samba is just for Windows, as that's all I ever see it in reference to. I actually have our other computers sharing, but can't figure it out on the server, because of the terminal. I can't find a guide for it. With the GUI, it just *goes.* (Which I guess is how that goes, but you'd think that someone might bother telling you how to terminal as well.)

---

### Post by Sarmacid on 2009-10-09
Samba is not unique to windows machines, ubuntu comes with the samba client and you can set up a server. More info on the subject [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

An alternative to this would be to install ssh on your computers, then you can just access the other computers clicking the location bar on nautilus and typing```
sft://username@computerip
```

---

### Post by kanikilu on 2009-10-09
If all your computers are running Ubuntu, I'd personally look into NFS:

[https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html)

I haven't set it up myself, so can't really give you much help beyond that, but if you have more specific questions about it, I'm sure someone here can help you out.

---

### Post by lykwydchykyn on 2009-10-09
Samba will work for Linux clients, but it's far easier to just use ssh.

Just install openssh on the server and give everyone an account on the server.

Then from GNOME you can browse the server with ssh://user@server.

Or you can mount directories on the server with sshfs.

The only thing ssh won't do (to my knowledge) is allow anonymous (unauthenticated) shares.

---

### Post by kanikilu on 2009-10-09
> **Sarmacid said:**
> An alternative to this would be to install ssh on your computers, then you can just access the other computers clicking the location bar on nautilus and typing```
sft://username@computerip
```

Good point, and along those same lines, you could use SSHFS and mount remote directories locally:

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by wojox on 2009-10-09
From one of you Jaunty Desktops go to Places > Connect to Server

Service type: ssh

Server: internal ip of jaunty server

Port: 22

User Name: Username on Server

Try that .

---

### Post by LinuxRules1 on 2009-10-09
If you want to share files on the Jaunty server then you have to edit the /etc/samba/smb.conf file.

For example, say the folder you want to share is /media/disk and the user to access it is user, you would do the following,

Step 1: type
```

sudo pico /etc/samba/smb.conf

```

Step 2: Scroll down to bottom of the page and type the following,
```

[share_name]
     path = /media/disk
     writeable = yes
     browseable = yes
     valid users = user

```

Now your done with configuring.

if you don't have a password set for samba you would type the following command.
```

sudo smbpasswd -a user

```

then restart samba.
```

sudo /etc/init.d/samba restart

```

---

