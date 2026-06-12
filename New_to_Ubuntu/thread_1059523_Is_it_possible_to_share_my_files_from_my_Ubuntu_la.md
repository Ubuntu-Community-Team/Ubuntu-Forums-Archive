---
title: "Is it possible to share my files from my Ubuntu laptop to my Win XP desktop wireless?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by gymophett on 2009-02-03
I want to share my music files I have on my laptop that runs Ubuntu 8.10 to my desktop computer that runs Windows XP. My wireless router is hooked to my desktop computer and I use wireless internet on this laptop. So how may I share it? I really really need to :(.
Thanks for all you guys help :)

---

### Post by emnii on 2009-02-03
You can use [this extremely helpful guide]("http://ubuntuforums.org/showthread.php?t=218630") on using FTP to share files with any OS, including Windows XP.

---

### Post by gymophett on 2009-02-03
> **emnii said:**
> You can use [this extremely helpful guide]("http://ubuntuforums.org/showthread.php?t=218630") on using FTP to share files with any OS, including Windows XP.

Thanks, I'll read up on it :]

---

### Post by raydeen on 2009-02-03
The other option is to use Samba. Here's a tutorial for 8.10 and I believe there's a link for 8.04 as well.

[http://www.jonathanmoeller.com/screed/?p=532](http://www.jonathanmoeller.com/screed/?p=532)

---

### Post by gymophett on 2009-02-03
> **raydeen said:**
> The other option is to use Samba. Here's a tutorial for 8.10 and I believe there's a link for 8.04 as well.

[http://www.jonathanmoeller.com/screed/?p=532](http://www.jonathanmoeller.com/screed/?p=532)

Thanks for this too. If this other guide doesn't work I'll have to use this one :)

---

### Post by theozzlives on 2009-02-03
SAMBA is file and print sharing with Windows.

---

### Post by gymophett on 2009-02-03
I'll give it a try :)

---

### Post by gymophett on 2009-02-03
*bump*
This is too complicated
I'm so new to Ubuntu.

---

### Post by HuaiDan on 2009-02-03
Right click on the directory you want to share, select "sharing options", then give your share a name. If you haven't added Samba yet, this action will add Samba automatically. Wait for it to download and install the Samba and nfs files, this should take a minute.

Then Ubuntu may need to reboot.  After the reboot, repeat the process on the original folder and any others you want shared. Samba FS will be enabled at that point  after which you should see your shares from the windows machine.


Pretty much just like windows file sharing.

Another word on FTP: If you want to set up an FTP server, choose an inetd server if your FTP usage will be only occasional: More overhead on your system resources on each transaction, but less overhead overall if traffic is light. A standalone server is better for heavy traffic.

---

### Post by HuaiDan on 2009-02-03
> **gymophett said:**
> *bump*
This is too complicated
I'm so new to Ubuntu.
Don't let the shell nerds get to you. We have the linux veterans here who like to make everything command-line-complicated :p

It's really simple: just right click and share.

---

### Post by gymophett on 2009-02-03
> **HuaiDan said:**
> Right click on the directory you want to share, select "sharing options", then give your share a name. If you haven't added Samba yet, this action will add Samba automatically. Wait for it to download and install the Samba and nfs files, this should take a minute.

Then Ubuntu may need to reboot.  After the reboot, repeat the process on the original folder and any others you want shared. Samba FS will be enabled at that point  after which you should see your shares from the windows machine.


Pretty much just like windows file sharing.

Another word on FTP: If you want to set up an FTP server, choose an inetd server if your FTP usage will be only occasional: More overhead on your system resources on each transaction, but less overhead overall if traffic is light. A standalone server is better for heavy traffic.


It works it works! Thank you soooo much!!!!! :D :D :D

---

### Post by BDNiner on 2009-02-03
If you share the directories on your windows machine you should be able to browse to the shares by browsing the network option from the places menu. You may have to make sure everyone is added to the groups that can view your windows share or you will have to use the same username that you use on your windows computer.

---

### Post by gymophett on 2009-02-03
Now I can sync my Zune. :)
On my desktop computer I have my files under network places to sync to my Zune. I just never take it to my desktop and sync is wirelessy!
I'm so happy :)

---

