---
title: "Setting up a shared folder"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-05
I am trying to set up a shared folder in jaunty, but its proving quite challenging. I've ticked the box to 'allow other people to write in this folder', but whenever i restart the box will become unticked :/
Could someone help?

---

### Post by mikeyphi on 2009-10-05
Could be that you need to install samba (file sharing package), available through synaptic

---

### Post by Falc7 on 2009-10-05
I installed it through add/remove programs

---

### Post by mikeyphi on 2009-10-05
> **Falc7 said:**
> I installed it through add/remove programs

In that case you only installed a GUI for samba. Go back to Synaptic and install 'samba'

---

### Post by Falc7 on 2009-10-08
I've installed it through synaptic, but the same problem happens, i click 'allow other people to write to this folder', click okay and everything, then restart, and the option is not selected

---

### Post by Sarmacid on 2009-10-08
You need to be root for that. Open up a terminal and type ```
gksu nautilus
```Navigate to the folder you want to share and tick the share option, this time it will stick. But be careful what you do while you are running nautilus with root privileges!

---

### Post by Falc7 on 2009-10-08
I get this message:
```
josh@josh-laptop:~$ gksu nautilus

(gksu:4265): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Nautilus-Share-Message: unknown format for key 'shared/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
** (nautilus:4266): WARNING **: Unable to add monitor: Operation not supported
ains 'Everyone:F,'.  Assuming that the share is read-onlyNautilus-Share-Message: unknown format for key 'shared/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'shared/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

--- Hash table keys for warning below:
--> file:///root
--> file:///home
--> file:///home/josh
--> file:///

(nautilus:4266): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 4 elements at quit time (keys above)

(nautilus:4266): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time
josh@josh-laptop:~$ 

```

---

### Post by alphaniner on 2009-10-08
From my own poking about, I noticed that creating and setting up shares through Nautilus (right click -> Sharing Options) doesn't modify the samba configuration file.  I have never used any of the GUI tools, but is it possible that something you did there is conflicting with what you are trying to do through Nautilus 'Sharing Options'?

You only need to be root to set 'allow other people to write in this folder' if you do not own the folder.  At least, that's my experience with 8.04 and 9.04.

And warnings like that are not uncommon when you launch a GUI app from the terminal.  Don't worry about it.

---

### Post by Falc7 on 2009-10-08
I thought perhaps this message might be important```
Nautilus-Share-Message: unknown format for key 'shared/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

```

> **alphaniner said:**
> is it possible that something you did there is conflicting with what you are trying to do through Nautilus 'Sharing Options'?


I don't know, is there someway to reset everything to do with samba?


Now, i get this error message when trying to add a share without being root , 'net usershare' returned error 255: net usershare add: failed to add share shared. Error was Operation not permitted

---

### Post by Falc7 on 2009-10-08
edit: oops double post

---

### Post by 3rdalbum on 2009-10-08
I have not managed to get the Nautilus shared folders thing to work; why not try the System-Config-Samba program? It's available in the repositories and it definitely works. Just be aware that your Samba users have to also exist as Linux users too, and you'll be fine.

---

### Post by alphaniner on 2009-10-08
Yeah, you've got a point there.  I missed that.  Stupid question of the year, is 'shared' the folder you are trying to share?

Ok, I just learned something.  There is a folder **/var/lib/samba/usershares**.  In that folder are what I think are the configuration files for samba shares made through Nautilus.  Could you post the output of```
cat /var/lib/samba/usershares/shared
```

---

### Post by Falc7 on 2009-10-08
> **3rdalbum said:**
> I have not managed to get the Nautilus shared folders thing to work; why not try the System-Config-Samba program? It's available in the repositories and it definitely works. Just be aware that your Samba users have to also exist as Linux users too, and you'll be fine.

It looks promising, thanks for the tip, i'll try it out

> **alphaniner said:**
> Yeah, you've got a point there.  I missed that.  Stupid question of the year, is 'shared' the folder you are trying to share?

Ok, I just learned something.  There is a folder **/var/lib/samba/usershares**.  In that folder are what I think are the configuration files for samba shares made through Nautilus.  Could you post the output of```
cat /var/lib/samba/usershares/shared
```

```
josh@josh-laptop:~$ cat /var/lib/samba/usershares/shared
#VERSION 2
path=/home/josh/Shared
comment=
usershare_acl=S-1-1-0:F
guest_ok=y
josh@josh-laptop:~$ 


```

This is the result after i have added that folder to be a shared folder list through system-> administration-> samba as recommended by 3rdalbum

Yep 'shared' is the folder i am trying to share :)


Edit: Yep its working now, installing system-config-samba worked, thanks guys :D

---

### Post by alphaniner on 2009-10-08
I just checked the 'Allow Everyone...' box and restarted and sure enough, it is no longer checked.  However, I was still able to write to the folder from a Windows NT box.

Edit: It seems to be a bug in Nautilus.  A folder with 'Allow Everyone...' will have **usershare_acl=S-1-1-0:F** in the config file, whereas a folder without that setting will have **usershare_acl=S-1-1-0:R** in the config file.  IOW, the setting is working even though the check disappears.  That is what I am seeing anyway.

---

### Post by stew2222 on 2010-05-21
Ahh, handy, I was was trying to find where nautilus dumped the config for shares made through the gui ... cheers

---

