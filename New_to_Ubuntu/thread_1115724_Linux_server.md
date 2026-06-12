---
title: "Linux server"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by blithen on 2009-04-04
How do I connect to mine in linux? I have a samba share set up that windows can access how do I mount it on linux though?

---

### Post by spiderbatdad on 2009-04-04
The easiest way is to right click a folder you want to share. Go to sharing options. The rest should fall into place.

---

### Post by blithen on 2009-04-04
Maybe it works differently in Gnome, but I'm using XFCE and that option is available when I right click, any other suggestions?

---

### Post by MrWES on 2009-04-04
> **blithen said:**
> How do I connect to mine in linux? I have a samba share set up that windows can access how do I mount it on linux though?

You can mount your samba share at bootup with cifs:

[http://www.swerdna.net.au/linhowtosambacifs.html]("http://www.swerdna.net.au/linhowtosambacifs.html")

I'd definitely use the .creds file to hide your username and more importantly your password.

Bill

---

### Post by Yashiro on 2009-04-04
Use this. [http://www.uvena.de/gigolo/](http://www.uvena.de/gigolo/)
It's included in Xubuntu 9.04. If your version is older just install it yourself. [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by blithen on 2009-04-04
> **MrWES said:**
> You can mount your samba share at bootup with cifs:

[http://www.swerdna.net.au/linhowtosambacifs.html]("http://www.swerdna.net.au/linhowtosambacifs.html")

I'd definitely use the .creds file to hide your username and more importantly your password.

Bill

How do I find out what my samba share server name is?

---

### Post by MrWES on 2009-04-04
> **blithen said:**
> How do I find out what my samba share server name is?


Check the

```
/etc/samba/smb.conf
```

file on the computer that created the samba share; it should look something like this:

```
[MyFiles]
    path = /media/external/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    force user = administrator
    force group = administrator

```

thus, I called my share 'MyFiles'; you can call it whatever you want in the smb.conf

Bill

---

### Post by Yashiro on 2009-04-04
He wants to browse an existing server. Not create a new one.

Use Gigolo on Xubuntu, like I said earlier.

---

### Post by MrWES on 2009-04-04
> **Yashiro said:**
> He want to browse an existing server. Not create a new one.

Use Gigolo on Xubuntu, like I said earlier.

Well he can't mount it if he doesn't know what the share was originally called correct? I wasn't instructing him on how to create one, but where to look for what it was called.

I'm out...

---

### Post by blithen on 2009-04-04
> **Yashiro said:**
> He want to browse an existing server. Not create a new one.

Use Gigolo on Xubuntu, like I said earlier.

I am, I posted that before I read your post. thanks for all the help guys!!

---

### Post by Yashiro on 2009-04-04
It's very flaky though. Just tested it on the latest Xubuntu and it doesn't work. 
It did work on the last build.

PyNeighborhood also might work. Try adding the server IP manually.

You may have to mount the share in your fstab if it fails for you. 
Network browsing with Xubuntu is the pits at the moment. Been trying to get it to recognize a share that every other machine on the network can see and it just fails.

Command line tools like smbclient, smbtree work fine. Every other tool just flat out fails. Really annoying and makes Xubuntu useless on my lan currently.

---

### Post by blithen on 2009-04-04
Yeah it's not working for me, apparently, "A program can't handle smb//192.168.blah blah" :/

---

### Post by blithen on 2009-04-04
SO basically it's mounted, can recognize it, just I can't open it and look at the files, any ideas?

---

### Post by Yashiro on 2009-04-04
Gigolo ,or whatever v3 is renamed to, just doesn't work. It's included specifically to do this  task yet all it can do is spit out the string smb://server/share which is what it needs to mount.
 
I didn't find a browser that actually worked correctly in Xubuntu. 
It needs fixing by someone I guess. I just gave up and did it manually in the end.
 
[I]mkdir /home/blithen/Lan/share1
sudo mount -t smbfs //serverip/share1 /home/blithen/Lan/share1[/I]

A pretty disappointing experience when you compare it to Gnome.
Nautilus worked perfectly from a Debian install on the same machine.

---

### Post by blithen on 2009-04-05
Welp, when I try to do that...
```
blithen@blithen-laptop:~$ sudo mount -t smbfs //serverip/Downloads /home/blithen/Lan/share1/
[sudo] password for blithen: 
mount: wrong fs type, bad option, bad superblock on //serverip/Downloads,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
```

---

### Post by Yashiro on 2009-04-05
Read up on how to mount smb shares manually. It works but I probably didn't post the exact command there.

---

### Post by nandemonai on 2009-04-05
> **blithen said:**
> Welp, when I try to do that...
```
blithen@blithen-laptop:~$ sudo mount -t smbfs //serverip/Downloads /home/blithen/Lan/share1/
[sudo] password for blithen: 
mount: wrong fs type, bad option, bad superblock on //serverip/Downloads,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
```

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473) should be of some help.

---

### Post by inobe on 2009-04-29
PyNeighborhood works fine, running xubuntu 9.04.

---

### Post by cgkx on 2009-05-10
In Xubuntu 9.04, you need install "gvs-fuse'' and "fusesmb" before you can open remote folder/filesystem icon in Gigolo.

When you drag&drop or copy/paste to desktop, it doesn't show you the progress bar;however, it's creating a folder and is doing the copy.

To be more visible of the progress, you need to drag&drop or copy/paste from remote folder (double click to make Thunar open a folder window for this remote system) to one of your folder (double click, say your "home"). This way, you can see the progress.

---

