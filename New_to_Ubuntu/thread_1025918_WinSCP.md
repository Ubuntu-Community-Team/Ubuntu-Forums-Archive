---
title: "WinSCP"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by perito on 2008-12-30
I need an _easy to use_ and _user friendly_ replacement for WinSCP.. any suggestions ?

---

### Post by tech9 on 2008-12-30
see link

[http://linux-blog.org/Going-Fishing-for-a-WinSCP-Replacement/](http://linux-blog.org/Going-Fishing-for-a-WinSCP-Replacement/)

---

### Post by teddks on 2008-12-30
Though I've never used WinSCP, [FileZilla](apt://filezilla) handles SSH file transfers quite nicely. Also, if you put the information for the server into Places>Connect To Server, you can browse the server like a folder.

I always just use the 'scp' program, which is command-line only. It's typically nice to use, and is very similar in most respects to the standard 'cp' program, so if you know cp, you know scp.

---

### Post by Nostalos on 2008-12-30
Not sure about KDE, but if you are using Gnome why not just Alt-F2 and enter the URL 

sftp://username@hostname/some/folder

---

### Post by FakeOutdoorsman on 2008-12-30
> **Nostalos said:**
> Not sure about KDE, but if you are using Gnome why not just Alt-F2 and enter the URL 

sftp://username@hostname/some/folder
Or, if I remember correctly since I'm not a Gnome user, "Places -> Connect to Server".  This will let you use Nautilus (the Gnome file manager) as a SFTP/SCP client.  Nautilus will also allow you to create bookmarks to the remote server so you won't have to retype the info each time you want to reconnect.

Another alternative is gFTP.

---

### Post by perito on 2008-12-31
Nautilus is nice but how to put a private key file (*.ppk) ?

---

### Post by teddks on 2008-12-31
> **perito said:**
> Nautilus is nice but how to put a private key file (*.ppk) ?

Key handling should all be done by ssh itself. Read the ssh manual for more about that. If you want to do key-based authentication, the easiest way to set it up is with Seahorse (installed by default and located in Applications>Accessories>Passwords and Encryption Keys).

---

