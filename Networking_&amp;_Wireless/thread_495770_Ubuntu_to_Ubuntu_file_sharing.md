---
title: "Ubuntu to Ubuntu file sharing"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by foxmuldr on 2007-07-08
I have a desktop machine and a laptop.  They're connected via a simple hub.  I've shared files between them with Win XP & Vista previously.  Yesterday and today I've installed Ubuntu on both of them, yet I can't figure out how to share files.

I've found Places -> Network, but it only shows ""Windows Network" and no folders or machines.

I'm a total newbie to Linux and would appreciate any help.

- Rick

---

### Post by masterd on 2007-07-08
Hi,

On one of you computers you need to install either a samba or a nfs server. I personally prefer samba because you can later easily access the shared files from a windows pc.

KDE:
First you need to install the some pkgs. You can use either Adept Manager or Synaptic - they are under the System menu. Find and install the "samba" and "smbfs" packages. Then from System Settings under Network & Connectivity choose Share. When you select File Sharing and enable Administrator Mode at the botton of the window you can add manage all shared folders.

or you can try this HOWTO
[http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)

Hope this helps you

---

### Post by remmosf on 2007-07-08
Well i could not get the samba solution to work. But you can use "ssh" as described elsewhere. I am using it right now with "Midnight Commander".

---

### Post by masterd on 2007-07-08
yeah, i know what u mean :-)

btw you can also do this with konqueror using one kioslave to open files on a remote computer using ssh. Look here: [http://docs.kde.org/stable/en/kdebase/kioslave/fish.html]("http://docs.kde.org/stable/en/kdebase/kioslave/fish.html")
I use this quite ofter - it's a really nice option :-)

---

