---
title: "More than 2 trash locations in Ubuntu 8.10 ?!"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by igor1102828 on 2010-02-12
The trashed files in Ubuntu 8.10 are supposed to have two possible locations: 
***/home/myUSERNAME/.local/share/trash/files*** (and ***/info***) 
and ***/root/local/share/trash/files (and /info)***, or
***/root/.local/share/trash/files*** (and*** /info***).

I cannot find the location of the files, which I'd like to remove from the trash; I do see them in trash, but cannot remove directly because they happened to be under the root priviliges.
I've opened Nautilus (```
gksudo nautilus
```) and went to
the folders ***/home/myUSERNAME/.local/share/trash/files*** (and ***/info***). 
They are empty (**[COLOR="Blue"]ctrl-h[/COLOR]** is pressed in order to make visible all hidden files  and I do see all of them indeed). 
BUT I don't have neither ***/root/local***, 
nor ***/root/.local***, 
so, these files are, certainly, not in the  place,  where they are supposed to be.
[COLOR="DarkRed"]**Where else the trash containers are located in the Ubuntu 8.10 ?**[/COLOR]
Thanks

---

### Post by philinux on 2010-02-12
/home/user/.local/share/Trash

and 

/root/.local/share/Trash

Thats it.

```
sudo locate Trash
```

---

### Post by igor1102828 on 2010-02-12
> **philinux said:**
> /home/user/.local/share/Trash

and 

/root/.local/share/Trash

Thats it.

```
sudo locate Trash
```
Thanks, this is exactly where I was seeking. So, what I get:
```
/root$ sudo locate Trash

/home/myusrname/.evolution/mail/config/et-expanded-mbox:_home_myusrname_.evolution_mail_local_._23evolution_Trash
/home/myusrname/.evolution/mail/local/.#evolution.sbd/Trash.cmeta
/home/myusrname/.local/share/Trash
/home/myusrname/.local/share/Trash/files
/home/myusrname/.local/share/Trash/info
/home/myusrname/.local/share/Trash/files/DFrimen_Photo_djvu.rar
/home/myusrname/.local/share/Trash/info/DFrimen_Photo_djvu.rar.trashinfo
/home/myusrname/.local/share/Trash/info/RealPlayer.trashinfo
/usr/lib/bonobo/servers/GNOME_Panel_TrashApplet.server
/usr/share/gnome-2.0/ui/GNOME_Panel_TrashApplet.xml
/usr/share/sounds/KDE-Sys-Trash-Emptied.ogg

:/root$ ls -a
.          .config    .gconfd          .kde           .recently-used.xbel
..         .dbus      .gnome2          .nautilus      .synaptic
.aptitude  Desktop    .gnome2_private  .profile       .thumbnails
.azureus   .esd_auth  .gstreamer-0.10  .pulse         .wapi
.bashrc    .gconf     .hplip           .pulse-cookie

```
but **[COLOR="DarkRed"]still two big folders are in the Trash![/COLOR]**

---

