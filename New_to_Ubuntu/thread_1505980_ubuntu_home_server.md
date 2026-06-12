---
title: "ubuntu home server"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by p7willm on 2010-06-09
I am just starting to look at solving my home storage and backup environment and was wondering if ubuntu will do it.

Right now I do not details on how. I just need to know if it what I want to do is impossible, possible but a pain in the ***, just what ubuntu was built to do, or why would you want to do that this would be much easier.

I have a Mac Book Pro and a time capsule to backup my system drive. I am happy with that and don't think I need/want to change that.

I also have about 1Tb of pictures on USB drives and that gets backedup when I get around to running a copy of one drive to another. (I am pretty good at doing this every Monday night). 

I am also starting to rip my DVDs so I can put some on my iPad when I travel. Since I am ripping the DVDs anyway I figure I could leave them on the computer and watch the from there.

I have a new TiVo that I would use to watch the DVDs. I might get into saving TV from the TiVo in the future.

I know that I can setup a RAID and protect against a drive failure but I really don't want to do that. I had a raid a couple of years ago and screwed part of the directory structure. So, my data was protected against hardware failure, but that data was useless. I really like doing a file by file backup so I know that i can read it all.

So, what I would really like to do is have a drive, two if it keeps growing, to store my pictures. On a regular automated basis I would like to copy all these files over to a backup volume. 

Now that my data is on the server I might also like to get to it when I travel. It might be nice to stream a movie or two to the iPad. Maybe something else.

So, should I look at ubuntu for this?

I am fairly computer literate, I found your site didn't I. I have worked with IBM mainframes since the 70's as an operator, sysprog, and OS developer since the 1970s. I also know C and can build a computer.

---

### Post by ubunterooster on 2010-06-09
**[http://www.linuxmint.com/](http://www.linuxmint.com/)**
Mint has less problems with this and is based on Ubuntu

---

### Post by jediborger on 2010-06-09
If you like your time capsule I would recommend this.
[http://backintime.le-web.org/]("http://backintime.le-web.org/")

Although this is just a client application. Your server would be the backup location and for that you should look into either NFS or Samba. You don't have to use the server edition of Ubuntu, the main difference is that the server edition does not come with the Gnome desktop so you will be at the command line only. Hope this helps you in going the right direction.

---

### Post by ubunterooster on 2010-06-09
Mint does samba out-of-box quite simply; and has good backup programs, to boot.

---

### Post by Miljet on 2010-06-09
You might want to also have a look at rsync over SSH.

[http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh](http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh)

---

### Post by expatCM on 2010-06-10
What about FreeNAS?

[http://freenas.org/doku.php](http://freenas.org/doku.php)

---

### Post by ubunterooster on 2010-06-10
My initial assumption was that the backup-to pc would be used for more than _just_ a file server/backup. If that is all it will be used for FreeNAS would be preferred over the Ubuntus/Mints

---

