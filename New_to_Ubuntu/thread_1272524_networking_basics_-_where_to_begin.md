---
title: "networking basics - where to begin?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by rocka on 2009-09-22
Hi all,

I have two Ubuntu machines [one desktop and one laptop] and also a EEE with the original Xandros on it. The desktop is connected to the router by cat5; the two laptops connect to the same router by WIFI. So far so good, they can all see the internet ok.

I want to be able to get the 3 machines talking to each other - to see files on the other machines and move files to/from etc. Also, I'd like to be able to stream from the desktop to either of the laptops. 

Oh, and there's a printer connected by USB to the desktop; I'd like to be able to print from either of the laptops too...

Fairly simple, yes?

I haven't been able to find anything yet.
I've looked through the menus, there's nothing obvious.
I did some searching here and on Google but all I've found is some stuff on getting Ubuntu to talk to Windoze shares.

Can anyone please point me to a howto or something to get me started?

TIA...

---

### Post by achase79 on 2009-09-22
Follow the information for using the windows shares.  All it does is use samba and the smb/cifs network protocol to connect the two computers.  You will have to have samba installed to serve a share and smbclient installed to view other shares.  Just use the Settings->Administration->Shared Folders program to set up the shared folder.

---

### Post by mikeyphi on 2009-09-22
Read this: [https://help.ubuntu.com/8.04/internet/C/networking.html](https://help.ubuntu.com/8.04/internet/C/networking.html)

Might provide some ideas!

---

### Post by Iowan on 2009-09-22
Though Samba is certainly an option, for a Linux-only network, you have other options for file sharing.  Probably the easiest way to get several links in one place is to have you check [dmizer]("http://ubuntuforums.org/showpost.php?p=7979230&postcount=151")'s signature and mention [SSH(FS)]("https://help.ubuntu.com/community/SSHFS").

---

