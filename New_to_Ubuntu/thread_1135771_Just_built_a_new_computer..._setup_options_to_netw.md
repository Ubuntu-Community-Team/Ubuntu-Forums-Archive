---
title: "Just built a new computer... setup options to network two Ubuntu computers"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by CRIMPS on 2009-04-24
So, now I have two computers that are up right now.  Both are running Ubuntu (See sig for specifics).  So, I want to network the two computers together.  

This thread should really only cover the setup of the networking of the two computers.  What are my options?  Can I only set up a Server-Client network or can I setup up a simple Workgroup-like environment between the two?  I want to be able to share files between the two.  I will cover my other needs (see wants) in another thread to keep issues simplified ;) .

I continue to see many threads discussing installation and configuration of Samba.  However, it seems like many of these posts detail steps for network Ubuntu AND Windows computers.  This will only be for two Linux computers.  Can anyone direct me to a wiki or site for help? 

Thanks!

---

### Post by Hospadar on 2009-04-24
While it is certainly possible to use samba, and share files on the machines, if you don't have any windows machines in the loop it's probably not the easiest or best solution.

I prefer using ssh, it's very secure and allows remote (command line) control (although you can launch graphical apps from the command line with ssh) it doesn't do vnc or remote-desktop like remote control, it just gives you a command line on the server.  You can also securely transfer files over ssh with nice graphical programs like filezilla, gftp, winscp (on windows), as well as scp from the command line.

Here's a good intro:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
This article goes a lot into public key authorization and whatnot, but
a) if your machines are not exposed to the internet (i.e. you forwarded port 22 to their ip on your router) then it's nothing to worry about, and
b) if you have a strong password that you change somewhat regularly, and your root account is disabled (as it is by default) then you will probably be just fine.

---

### Post by CRIMPS on 2009-04-24
This is exactly what I needed I think.  Thanks!

---

### Post by inobe on 2009-04-24
i would simply follow steps 1 to 11 under **"Sharing folders via the Shared Folders application"**

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

done.


if your fast you should have both computers setup in ten minutes.


if you want secured networking follow steps 1 to 6 under **"Accessing shared folders via Windows"**

that will work with any platform even if it specifies windows.

---

### Post by fenian on 2009-04-24
To setup a LAN (Local Area Network) with Linux only machines I would use NFS (Network File System),in fact I do use it and it works quite well ,much faster than Samba.As far as SSH goes,I feel it is overkill if you only need to share files locally.I use SSH to access my computer remotely from outside the LAN but it requires proper setup and monitoring because even though it is more secure than other methods it still decreases your overall security because it makes the computer accessable via the internet.

Setting up NFS is relatively straight forward a good guide [can be found in this post]("http://ubuntuforums.org/showpost.php?p=1456895&postcount=1"),even though the post is a bit old it is recently updated.

---

### Post by inobe on 2009-04-24
fenian how much faster, have you experienced horrid transfer rates with samba ?

the method i provided limits over bloated smb.conf as we know will cause drag.

---

### Post by MrWES on 2009-04-24
+1 for NFS over Samba --Samba and/or cifs is a pig. If there both Ubuntu boxes use NFS.

Bill

---

### Post by BrightEyesDavid on 2009-04-24
> **inobe said:**
> fenian how much faster, have you experienced horrid transfer rates with samba ?
With NFS between machines on my LAN I get about 8MB/sec as opposed to Samba's 5MB/sec.

---

### Post by inobe on 2009-04-24
fair enough.

---

### Post by theozzlives on 2009-04-24
I recommend NFS even though I use Samba (yes I have a WindowsXP machine) you prolly want either a crossover cable or a router.

---

### Post by inobe on 2009-04-24
it would be interesting to know what hardware CRIMPS is using.

---

### Post by fenian on 2009-04-24
I get about 10% speed improvment using NFS.

---

### Post by CRIMPS on 2009-04-24
I like the idea of NFS for general file sharing over a LAN.  I do plan on setting up SSH in order to connect to one of my boxes remotely from my office.  I think I saw pretty good steps for this on the first Wiki that was posted.  I assume most agree that SSH (and PuTTY) would be the best way to remotely connect from a Windows machine to an Ubuntu machine?

> it would be interesting to know what hardware CRIMPS is using. 

See signature for Hardware specs and current versions of Ubuntu.

Thanks for all of the ideas everyone.  :)

---

