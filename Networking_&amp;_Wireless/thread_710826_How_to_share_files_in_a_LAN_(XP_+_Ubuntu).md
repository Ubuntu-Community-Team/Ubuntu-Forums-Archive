---
title: "How to share files in a LAN (XP + Ubuntu) ?"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by dberebi on 2008-02-28
I'm sure it's a noob question but I've never became used to linux so.....

I have:
**1.** **my home PC** with [COLOR="Gray"]windows XP sp2[/COLOR], BUT now I can't get windows to work so I'm using a _**Live CD of Ubuntu**_ (7.04 - Feisty Fawn).

**2.** My **laptop with WinXP** sp2.

**I've connected both of them with a cable** (serial? don't know, the port that resembles the usb but wider) **so now they're in a LAN and I know the LAN are working** because I'm using firefox under the Ubuntu but only the LAN connection is available to Ubuntu.

now, I want to backup some files from my home PC and copy them to my laptop, so my question is,

**How can I share files between both of them?**

---

### Post by jvanoort05 on 2008-02-29
You can share the files but if your going to use the live cd then it may be more practical if you get a usb flash drive and save your files on it.

P.S. using the live cd can be slow because you are always using your cd drive. why can't you install ubuntu to your HD with a dual boot?

---

### Post by HermanAB on 2008-02-29
The easiest way to move files between systems is with FTP, for example proftpd or vsftpd, both of which work right out of the box.  People who complain about not being able to get it to work invariable changed something stupid in the default setup and then wonder why it won't work. 

Other methods are:
1. Netcat
2. NFS
3. Samba

Samba is 'Windows Networking'.  This is by far the most difficult and complex way to network computers together.  There is an enormous project in Australia dedicated to this Rube Goldberg machine called [http://samba.org](http://samba.org).

Hope that helps.

Herman

---

### Post by Eiríkr on 2008-02-29
Yes, I was quite amazed at how quickly I was able to get NFS working properly for a Lin->Mac share, even with a number of snags along the way.  Samba is great for Lin->Win, and kudos to the devs.  But *boy* how convoluted.  Leave it to MS to play poorly with others, I guess.  :-|

Cheers,

Eiríkr

---

### Post by superprash2003 on 2008-02-29
if you want more info on setting up samba.. follow this link [http://ubuntuguide.org](http://ubuntuguide.org) there is a great tutorial for samba.. easy to setup just follow instructions!!

---

