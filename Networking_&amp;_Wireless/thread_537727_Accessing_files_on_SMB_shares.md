---
title: "Accessing files on SMB shares"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by Matakoo on 2007-08-29
Okay, I'm not sure if I should post this in this section but...

I have samba set up correctly. That is, I can access the shares properly. Write to files, create directories, delete stuff. You name it. So far so good.

However, some of the programs I use refuse to open files straight from there. In other words, if I want to use the files I first have to copy them over from the share, do whatever I want to do with the files, and finally copy them back. This problem is so far only showing itself when it comes to GTK/Gnome applications. I.e. Gimp complains that only local files are supported. The same with Firefox. I'm not sure if OpenOffice uses GTK, but the same problem is sort-of there (at least it automatically creates a local working copy).

The KDE-based apps do it correctly. 

Now, is there a way to fool the offending programs to think smb-stored files are local??? The shares in question are located on a Windows 2003 server, and I'm using Kubuntu Feisty if that makes a difference.

---

### Post by Leonopolis on 2007-08-30
First post here so go easy on me.

I've got the same problem, anyone got any ideas?

Thanks in advance for any help.

Leon

---

### Post by callan79 on 2007-08-30
> **Matakoo said:**
> I have samba set up correctly. That is, I can access the shares properly. Write to files, create directories, delete stuff. You name it. So far so good.
Now, is there a way to fool the offending programs to think smb-stored files are local??? The shares in question are located on a Windows 2003 server, and I'm using Kubuntu Feisty if that makes a difference.

Hi There,

Can you tell me, are you accessing the files via :

1. Going to Places >> Computer and typing smb://computername in the address bar?
or
2. Going to Places and browsing the network
or
3. Mounting the share to a local directory, so it exists as part of your local filesystem - [like this](http://ubuntuforums.org/showthread.php?t=536787)


Let me know how you go!

Cheers
Callan

---

### Post by Matakoo on 2007-08-31
> **callan79 said:**
> Hi There,

Can you tell me, are you accessing the files via :

1. Going to Places >> Computer and typing smb://computername in the address bar?
or
2. Going to Places and browsing the network
or
3. Mounting the share to a local directory, so it exists as part of your local filesystem - [like this]("http://ubuntuforums.org/showthread.php?t=536787")


Sort of a combination of 1 and 2...using the built-in KDE remote:/ protocol in the file-selector. Easy to do even in Gtk-based apps.

But for some reason I forgot to try to mount-variety...and that one worked as I wanted it to. Well, once I installed the smbfs package that is. Thanks!

---

