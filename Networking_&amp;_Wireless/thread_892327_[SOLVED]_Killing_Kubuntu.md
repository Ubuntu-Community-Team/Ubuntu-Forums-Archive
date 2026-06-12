---
title: "[SOLVED] Killing Kubuntu"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by mandrill on 2008-08-17
I have a 3 pc home LAN, mixed with xp, vista, ubuntu, and as of yesterday kubuntu upgraded to kde 4.1. Everybody played nice together, until....

It (Kubuntu) sees mshome, can access and write to files on the other boxes, but it (itself) is stuck in WORKGROUP. For the life of me I can't figure it out. I have fooled around with this all day with various and mixed but not successful results. KDE is like a new language to me. I'm cool with Gnome, but...

If anyone can give me a way to do this I'd be very grateful. (I'm thinking text file mod somewhere)

ps  MSHOME and WORKGROUP folders are sitting right next to each other in the samba directory, which just pisses me off!  ](*,)

---

### Post by dmizer on 2008-08-17
Install samba server:
```
sudo aptitude install samba
```

Make a backup of the configuration:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-backup
```

Edit the samaba configuration file with your favorite text editor (I like nano):
```
sudo nano /etc/samba/smb.conf
```

Delete everything in this file, and replace it with the following lines:
```
[global]
    ; General server settings
    netbios name = [COLOR="Blue"]KUBUNTU_COMPUTER_NAME[/COLOR]
    workgroup = MSHOME
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    name resolve order = hosts wins bcast
```
(note: be sure to replace [COLOR="Blue"]KUBUNTU_COMPUTER_NAME[/COLOR] with the Kubuntu computer's actual name)

Restart samba:
```
sudo /etc/init.d/samba restart
```

Kubuntu will now be a member of the MSHOME workgroup.

---

### Post by mandrill on 2008-08-18
> **dmizer said:**
> Install samba server:
```
sudo aptitude install samba
```

Make a backup of the configuration:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-backup
```

Edit the samaba configuration file with your favorite text editor (I like nano):
```
sudo nano /etc/samba/smb.conf
```

Delete everything in this file, and replace it with the following lines:
```
[global]
    ; General server settings
    netbios name = [COLOR="Blue"]KUBUNTU_COMPUTER_NAME[/COLOR]
    workgroup = MSHOME
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    name resolve order = hosts wins bcast
```
(note: be sure to replace [COLOR="Blue"]KUBUNTU_COMPUTER_NAME[/COLOR] with the Kubuntu computer's actual name)

Restart samba:
```
sudo /etc/init.d/samba restart
```

Kubuntu will now be a member of the MSHOME workgroup.

Appreciate the shortcut. Thank you. Now, perhaps you could tell me how to get the right permissions to share folders - right now, I'm spent, and have to just walk away from the keyboard. I use both machines as music servers (to each other, or rest of network) and like I said, if this was Ubuntu I wouldn't need to ask.....thanks in advance.

---

### Post by dmizer on 2008-08-18
> **mandrill said:**
> Appreciate the shortcut. Thank you. Now, perhaps you could tell me how to get the right permissions to share folders - right now, I'm spent, and have to just walk away from the keyboard. I use both machines as music servers (to each other, or rest of network) and like I said, if this was Ubuntu I wouldn't need to ask.....thanks in advance.

No problem.

The best way I know of for configuring samba shares is to follow the "best samba server howto" linked in my sig.  A server configured according to that howto will provide for correct permissions in the share.

---

