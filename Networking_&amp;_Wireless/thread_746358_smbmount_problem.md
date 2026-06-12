---
title: "smbmount problem"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by mr.loco on 2008-04-05
Hey guys. I'm having a problem with smbmount.

I can see the shares via smb://path/to/share but when I try to mount it to /home/mrloco/Music it just won't let me. First it asks me for a password which I don't need since ive set the permissions in Windows so that everyone can read, and then it says:

```
8694: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

This really doesn't make sense cos i've triple checked that that's the right path i'm putting in.

Thx.

---

### Post by Eiríkr on 2008-04-05
How are you trying to mount?  What is the specific command line you are using?

Also, note that the smbmount command has been deprecated for some time, and is officially abandoned.  From the man page:
> WARNING: smbmount is deprecated and not maintained any longer.  mount.cifs (mount -t cifs) should be used instead of smbmount.

Have a look at [font=courier]man mount[/font] and [font=courier]man mount.cifs[/font] to familiarize yourself with the options available.

Cheers,

Eiríkr

---

### Post by mr.loco on 2008-04-06
I've tried doing

```
sudo mount -t cifs //laptop2/etc /home/mrlocoMusic

```

and it spits out basically the same thing.

Where are the man pages? [edit: nevermind, got it]

---

### Post by mr.loco on 2008-04-06
Ok the problem was that there was a space in the share name.

I tried putting in %20 instead of the space but that didnt work so I just renamed the share.

---

### Post by Eiríkr on 2008-04-07
I trust it worked after renaming?  :)

Spaces in paths can be handled any of numerous different ways.  Some apps use the %20 approach, others require backslash escaping like **//SERVER/This\ is\ a\ share/Fred**.  Oftentimes renaming is the easiest approach, as you discovered.  :D

Cheers,

Eiríkr

---

### Post by mr.loco on 2008-04-08
Yeah it works like a charm :)

---

### Post by Eiríkr on 2008-04-08
Experimenting some after posting here last time, I found that double quotes around the offending part of the path will work in a manual mount command, but in the /etc/fstab file, you need to replace the spaces with \040, as indicated in the fstab man page.  

And if that does it for you for this thread, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

