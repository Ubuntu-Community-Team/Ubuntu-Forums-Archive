---
title: "Sharing folders between Ubuntu and Windows XP"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by GreenLantern33 on 2006-11-28
I have two machines, a windows xp laptop and a ubuntu desktop.

On the ubuntu desktop I can see files that are on the windows machine just fine.

However when I go to the windows machine and try to access files on the ubuntu machine I get a prompt for a username and password.

Is there a quick fix for this?

I found this how-to (below), but I thought there might be something easier that I could do since I can already share one way, just not both.
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer+to+peer+connection](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer+to+peer+connection)

Thanks in advance,
GL

---

### Post by guest5 on 2006-11-28
I have the same issue, just today I attempted to share files.  Can see all the shares on 4 pc's using simple file sharing.  I am assuming we need to somehow tell ubuntu (add user?) someone, somewhere, is going to connect to the samba/ubuntu share.

How do we do it?

Hoping to see some experts on this soon.

---

### Post by Iowan on 2006-11-28
> **GreenLantern33 said:**
> 
Is there a quick fix for this?
Besides **security = share** in [global], you might try **guest ok = yes** inside the shares.
Keep in mind that this blows away security.

If that response is too vague, I can offer more details...
(Edit **/etc/samba/smb.conf**)

---

### Post by GreenLantern33 on 2006-11-28
And I would do this in /etc/samba/smb.conf

Right?

---

### Post by guest5 on 2006-11-28
way waaayyy to vague for me.

---

### Post by guest5 on 2006-11-28
surely if it is asking for a password and login name, there must be a correct username and password somewhere?

where do we create one if there isn't one?  or find the one it is already looking for? or change it?  it does not seem to be in my /etc/samba/smb.conf that I can see.

---

### Post by Iowan on 2006-11-29
[QUOTE=GreenLantern33]And I would do this in /etc/samba/smb.conf

Right?[/QUOTE]Correct.
[QUOTE=guest5]way waaayyy to vague for me.[/QUOTE]
The referenced [HowTo]("http://www.ubuntuforums.org/showthread.php?t=202605") goes into detail about adding users.  In brief, for **security = user**, the user must exist for the Linux box(in the **passwd **file) AND on Samba ( the **smbpasswd **file).  IIRC, **security = share** is (supposed to be) a quick/dirty way around the registration/password issue, but I seem to remember reading that **share** still required some authentication.  The **guest ok = yes** *should* remove the requirement for the share. (Not absolutely sure about this - I haven't tried it... I prefer a bit more security.)

---

### Post by nadp on 2006-11-29
wat i did was make a FAT32 partition and put all the files i want to use in win/linux, since both OS's read fat32, it shouldnt be a problem

---

### Post by guest5 on 2006-11-30
thanks you.

security = share

and restarting samba works well enough for me.

again.  
Thank You.

---

