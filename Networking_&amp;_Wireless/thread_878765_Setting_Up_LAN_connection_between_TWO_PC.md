---
title: "Setting Up LAN connection between TWO PC"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by scliem on 2008-08-03
Hi all, I would like to know is there anyway for me to setting up a LAN for file sharing propose in Ubuntu? Any references any helps is very appreciated, thanks!

---

### Post by geraldvillorente on 2008-08-03
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

---

### Post by scliem on 2008-08-03
Thanks for the help... But I would like to ask, is it no need set up something like IP Address? Forgot to tell you all that I wish to use cross cable to LAN two PC up...

---

### Post by scliem on 2008-08-03
Anybody help?

---

### Post by geraldvillorente on 2008-08-03
you should use crossover cable if your connection is pc-to-pc. Static IP addressing is advisable since your are using peer to peer connection

---

### Post by scliem on 2008-08-03
Thanks for the advise. But the problem is, how to set it up? I am new to Ubuntu...

---

### Post by ernz on 2008-08-03
Hey scliem! I know it's a bit of a cheeky solution, but I have found it to work quite well (if not a little slow). If you are wanting to connect the to networked devices together purely for file transfers, you can use something called LANShark.

You can find it here:
[http://www.getdeb.net/app/lanshark]("http://www.getdeb.net/app/lanshark")

Hope this helps! :)

---

### Post by dhughes on 2008-08-08
> **scliem said:**
> Hi all, I would like to know is there anyway for me to setting up a LAN for file sharing propose in Ubuntu? Any references any helps is very appreciated, thanks!

 Actually the quickest, if not the best way, I was trying to use NFS, SSH, SCP messing with exports etc. then I just ended up making a new folder, right clicking it chose "Sharing options" and "Share this folder" then put stuff in there I wanted to share making sure to right-click the files and folders to make sure Permissions were OK so the files could be shared.

 This is over my home LAN using a Linksys router. It's easy but I'm not getting very fast transfers, using 100Mbit NICs and a 100MB switch I can't get over 5MB/s, that's something I have to work on.

 > Forgot to tell you all that I wish to use cross cable to LAN two PC up...

 Oops, I just read that part about the crossover cable, I'm not sure if it will work using that method but it's a pretty easy way to try using the shared folder method.

---

### Post by Iowan on 2008-08-09
Another [Samba]("https://help.ubuntu.com/community/SettingUpSamba") link.

---

