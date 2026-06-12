---
title: "Home Network Setup Help Needed"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by weiqiang on 2007-05-25
Hi all,

I am planning to purchase a new computer to install Ubuntu for my home usage. Here is what I want to do with it.
I currently have 2 computers at home, one XP and one Ubuntu. They go up to internet by a Linksys Router, the 802.11g I think. I need the third computer to download some huge files, probably through bittorrent and emule. I want to be able to control the third computer through the other two, and these two computers can easily access the content downloaded by the third computer. Basically I want to remotely browse bittorrent and emule sources and do the downloading job on the third computer, the other two can share the content.

I am not sure how I  can achieve this, Can anyone please give me some idea?

---

### Post by tact on 2007-05-25
This is such an open ended question you have asked.   So many ways to do it.

Ok..  so you have already one WinXP and one ubuntu machine on your home LAN now.  And adding one more ubuntu machine.

The WinXP box means the easiest way to peer share will be using windows networking (samba).  Good news is that with ubuntu (edgy or fiesty to my knowledge) you don't have to follow all the "how do I make my ubuntu box part of a windows domain" type instructions.  Forget all that.  Samba is set up "enough" in the standard out-of-the-box fiesty or edgy to do what you want to do.

All you need to decide is  whether you are happy with the extra protection that you have with ubuntu/samba the default way it is set up...  ie having to use username/password to access shares on the new  ubuntu machine.     If you really cannot stand having to give username/password whenever you access the shares on the new ubuntu machine from either the old ubuntu machine or the WinBox...  then its a simple matter to change it.  (Ask later if u dont know).

Also out-of-the-box you can remote desktop into the new ubuntu box fairly simply.  From ubuntu to ubuntu (or ubuntu to WinXP) you just click Applications>Internet>Terminal Server client and point it to the IP address of the target machine. 

 (On both ubuntu (or a WinXP box) target box - you need to permit remote login.  System>Preferences>remote desktop - in ubuntu)

---

### Post by weiqiang on 2007-05-26
Well, the current Ubuntu and XP used to be able to share certain folders, but I found that the speed is not satisfactory. I am not sure it's because of the router or something else. I am using WRT54G router. Is there a faster way to implement this? Besides, do I need a Ubuntu or Ubuntu Server?

---

### Post by weiqiang on 2007-05-26
What if I make it as a ftp server?

---

### Post by tact on 2007-05-27
If by "sharing files" you are ok with the windows box and your existing ubuntu machine copying files from the new ubuntu box to their own HDD - then for sure you can use a variety of methods including ftp.

(I originally thought you wanted to "share files" meaning...  access files on the remote machine, not copying them to the local machine before using).

If you are ok with adding software and configuring it on the windows machine you might consider using SSH to log into and connect to the new ubuntu machine.   

Another "outside the square" thinking idea - what about using remote desktop?   You can "remote desktop" connect from a windows machine or ubuntu machine to the new ubuntu machine.

No you don't need ubuntu server edition.  It adds nothing.  Actually its pretty much just  the desktop version MINUS the graphical desktop and graphical installation packages.

---

### Post by weiqiang on 2007-05-28
I am confused about my expression too, actually:)

Remote Desktop is definitely a good idea. By this way, I can add new download task in server machine through the local ones. I just need to copy files downloaded from server to local. I guess ftp would do it? I don't know if this is fast enough.

Thanks a lot for your reply ,tact.

---

### Post by bsmith1051 on 2007-06-01
FYI
Here's the how-to on setting-up an FTP server,
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

I don't think it's complete, though.  There's also another one specific to the PureFTP server (which has a GUI),
[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

---

### Post by weiqiang on 2007-06-02
What is the fastest way to transfer file in a gui way, ftp or other ways? Can I even map a network drive that is part of my server on my windows machine?

---

