---
title: "Easy Server OS"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by ErusGuleilmus on 2007-08-15
I have a P3 box with the processor at 733 mhz and 512 ram. All I want to use it as is a basic file server over a lan. What would be a good distro for this? I fear that the aforementioned machine might not have the muscle to run Ubuntu Server, but I want something with a GUI and is not overly complicated, you know, something relatively easy to get going.

Thanks!

---

### Post by tgm4883 on 2007-08-15
I had a fileserver that ran on a P3 733mhz with 384MB ram.  The trick is to use no GUI.  I installed a command line system using the alternate cd, then installed webmin so i could manage it via firefox.  Works great.

---

### Post by ErusGuleilmus on 2007-08-15
Sweet. I have never heard of "webmin", are there any tutorials floating around out there?

---

### Post by chriscando on 2007-08-15
I think Ubuntu would be perfect for this.
If you want to run a gui I would look at the Ubuntu Xfce version called Xubuntu as it is suppose to be lighter on system requirements.

But if you can go without the gui, ubuntu server edition is perfect. It is actually pretty light on system requirements IMO since it does not have a gui by default.

Did you want to use this as a file server for other linux machines or windows machines too?

Either one will be really easy to get going with. I would recommend setting up a ssh server its great for sharing files.

---

### Post by ErusGuleilmus on 2007-08-15
Yeah, i know about xfce, i used it for awhile. If I installed xfce onto the server edition, would I still be able to do all the set up I need through the console?

---

### Post by chriscando on 2007-08-15
I don't think there is anything you can't do through the console that you can do through a gui. But it depends what you want to do.

If you just want to share files then yes you can do it all from the command line. I would setup a ssh server
Install it by..
```
sudo apt-get install sshd
```

Then if you need to add more users for their own file sharing accounts
```
sudo adduser username
```

If you want to connect from a windows computer download the free program winscp. You will be able to login to your server using the same login as on the command line. Winscp allows you to drag and drop files, its very easy.

And if your sharing files from another linux machine its even easier.

---

### Post by tgm4883 on 2007-08-15
If you want to share with linux computers, just set NFS up from the command line.  If you want to share with windows computers, IMO SAMBA sucks to setup from the command line and I would install webmin (or at least SWAT)

A good little guide for settting up NFS can be found here.
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu_Feisty#NFS_Server)


webmin can be found here
[http://www.webmin.com](http://www.webmin.com)

you will have to download the deb (wget it on the machine) and attempt to install.  It will complain about uninstallable things.  apt-get these things (dont forget to add the universe and multiverse to your sources.list then apt-get update) and your set.  Then just access webmin from a web browser by going to [http://*serverip](http://*serverip)*:10000

---

### Post by notwen on 2007-08-15
I second NFS, it's very easy, simply edit a file specifying the folders you're wanting to share then you mount them via lan on the other computers.  I have a headless PC running ftp, web, nfs services.  I keep all my media on said PC and play my music from where ever I currently am.  Helps keep my HDDs empty on my laptop and daily usage desktop.  I know NFS can support Unix, Linux, Mac OS, and Windows, but as far as a Linux to Linux setup goes it's easy as the steps given in guide linked above by tgm4883.  As far as OS goes, I'd recommend XFCE if you insist on using an Ubuntu blend w/ GUI or the Ubuntu server, or just go w/ plain old Debian Etch w/ or w/o a GUI.  Good luck. =]

---

### Post by ErusGuleilmus on 2007-08-15
Thank you for the replies. Im not a very Linux Savy person yet, so this might be a challenge. I know that Samba detect all the Winodws boxes floating around my home network, and I can read/right on there shared directories. Might it be easier if all I want is a file server, to use XP. You can go ahead and slap me if you feel the need.

---

### Post by clblanchard on 2007-08-16
/me Slaps ErusGuleilmus.  You would be best off using ubuntu server edition.  It uses almost no resources and NFS is awesome.  Not to mention it's all free.  SLAP!!!!! one more time for good measure!!

---

### Post by chriscando on 2007-08-16
I could not agree more with clblanchard, ubuntu server is perfect for this and FREE!
There is no point in buying a copy of XP for this (because you wouldn't be pirating this right??).

I really think it will be worth the time you put into this to setup ubuntu. Besides, you have a bunch of people willing to help you :)

---

