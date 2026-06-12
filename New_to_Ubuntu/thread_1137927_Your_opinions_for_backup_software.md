---
title: "Your opinions for backup software"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by eddski on 2009-04-26
I have a setup consisting of /boot (primary), /, home tmp, var, swap, usr, all in an extended partition. I want to back my system and tried some of the software and it wasn't pretty. I'm new and want to start with something relatively easy. I want to update to jaunty sometime, but everything works very well now and I need some backups. Thanks in advance...

---

### Post by glotz on 2009-04-26
[http://www.partimage.org/](http://www.partimage.org/)

---

### Post by jayanramesh on 2009-04-26
Dear Glotz,
Is there any  back up solution for jaunty 64 bit?
Thank you

---

### Post by glotz on 2009-04-26
I think partimage will work just fine if you want to backup the whole thing. If you wish only to backup some parts, then it's not an ideal tool for the job. Maybe somebody else knows.

---

### Post by inobe on 2009-04-26
heres a list

[http://www.junauza.com/2009/01/7-best-freeopen-source-backup-software.html](http://www.junauza.com/2009/01/7-best-freeopen-source-backup-software.html)

---

### Post by jayanramesh on 2009-04-26
Thank you both Inobe and Glotz

---

### Post by presence1960 on 2009-04-26
> **eddski said:**
> I have a setup consisting of /boot (primary), /, home tmp, var, swap, usr, all in an extended partition. I want to back my system and tried some of the software and it wasn't pretty. I'm new and want to start with something relatively easy. I want to update to jaunty sometime, but everything works very well now and I need some backups. Thanks in advance...

I would recommend rsync or it's GUI version grsync. Simple and fast. The first backup may take a little but after that it is very quick.

---

### Post by shel-hall on 2009-04-26
> **eddski said:**
> I have a setup consisting of /boot (primary), /, home tmp, var, swap, usr, all in an extended partition. I want to back my system and tried some of the software and it wasn't pretty. I'm new and want to start with something relatively easy. I want to update to jaunty sometime, but everything works very well now and I need some backups. Thanks in advance...
It's not so much a question of what you want to back up, but, rather, where you want the backup copies to be.  CDs?  DVDs?  Tapes?  Remote server?  Internet service?

For many years, I've used a multi-stage backup scheme:  copy critical files from workstations/desktops/laptops/whatever to a local server, then from there to long-term storage.  This gives you quick restoration of recent files (from the local server's hard disk) and long-term storage of data on some other medium.  For many years, I used tape as the long-term storage, but I'm working now on a system using a remote server with high-redundancy disk systems, with the transfers from the local backup server traversing the internet.

In any case, I use something that merely copies individual files, so I don't have to worry about special backup software's becoming unavailable, not supporting some particular hardware, etc.  This generally means xcopy on Windows machines, and rsync on Linux/Unix machines.

So ... what are you going to back up to?

-Shel

---

### Post by eddski on 2009-04-26
To shel-hall, I want to backup to an external hard drive(for recent backups) and then to a dvd(as you stated for long-term storage). I don't like leaving backups on a hard drive for very long, as I have seen first hand what can happen when your external drive goes out.

---

### Post by gotee12 on 2009-04-26
I use Remastersys to back up my entire Ubuntu install to a single "Live" DVD. I can then either reinstall the entire OS/Apps/Documents in one fell swoop or take it to another PC and boot up from the Live DVD. It works great for me. 

You can add the software repository and then install it from the command line. The install creates shortcuts for the app under System -> Administration.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by inobe on 2009-04-26
> **gotee12 said:**
> I use Remastersys to back up my entire Ubuntu install to a single "Live" DVD. I can then either reinstall the entire OS/Apps/Documents in one fell swoop or take it to another PC and boot up from the Live DVD. It works great for me. 

You can add the software repository and then install it from the command line. The install creates shortcuts for the app under System -> Administration.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

got a howto for that, i didn't have much luck setting it up.

thanks :)

---

### Post by steve101101 on 2009-04-26
what command would i run to do the same thing as this command which backs up EVERYTHING on my computer

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

---

### Post by steve101101 on 2009-04-26
bump

---

### Post by jayanramesh on 2009-04-27
Dear presence et al,
Thank you so much.For me it is very easy to use Grsync GUI version of rsync.

---

### Post by jayanramesh on 2009-04-27
Dear inobe,
After seeing 1 time vault 2.clonezilla 3.duplicity 4.bacula 5.amanda 6. rsync 7.flyback .I couldn't find any 64 bit version and moreover it seems all command line versions

Thank you

---

### Post by jayanramesh on 2009-04-27
Dear gotee12, 
Thanks a lot .I installed remastersys and it is good.

---

