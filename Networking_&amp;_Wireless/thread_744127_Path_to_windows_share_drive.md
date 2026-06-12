---
title: "Path to windows share drive?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by engelstein on 2008-04-03
Running ver 7 (Gutsy), desktop version.

Through the desktop GUI I have access to a shared windows drive (//grendel/shared).  Works great, and sets it up at boot (I think), so I can access it right away.

I am now trying to figure out how to access that drive from the command line.  I can't figure out where it's mounted (if it's mounted).  Is there a way I can access it? Or do I need to install Samba and do it that way?

Thx -

---

### Post by Eiríkr on 2008-04-03
The full-on Samba package is only needed if you want to set up a share on your Ubuntu machine.  Otherwise, all you need are the smbclient and smbfs packages (which might come installed by default, can't remember).  The GUI-based access you describe is direct over the wire, and so far as I've read, access that way doesn't actually mount the share anywhere -- so you won't be able to find it via the CLI.  ;)

You *can* however just mount it regularly, and then get at it that way.  Open a terminal and run the following:
```
sudo mount -t cifs -o username=USERNAME,password=PASSWORD,rw,uid=UID,gid=GID //grendel/shared /MOUNTPOINT
```

Replace the caps with the appropriate values.  UID and GID values define who will own the share after it's mounted; if you leave these out, it defaults to root, which can be bothersome.  :)  Use either your username's and group's numeric values, or just your username and primary group names (definitely easier to remember).  Make sure MOUNTPOINT is an empty directory before you mount.  And have a look at [font=courier]man mount[/font] and [font=courier]man mount.cifs[/font] for details on other options you might want or need.

HTH,

Eiríkr

---

### Post by engelstein on 2008-04-03
Excellent -- I'll give this a shot.

Thx -

Geoff

---

### Post by Eiríkr on 2008-04-03
If that works and resolves your issue, please mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  This helps folks looking for solutions.  :)

Cheers,

Eiríkr

---

