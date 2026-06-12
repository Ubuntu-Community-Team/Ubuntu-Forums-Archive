---
title: "Am I the Only One Who is Lost?"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by MSchenker on 2007-12-09
Hello All,
OK, I love Kubuntu, and I am keeping it.  But I am utterly frustrated with the wireless support.  Now that I am using Kubuntu as my production system on both my laptop and desktop, I really am feeling the pain of wireless issues!

I have a desktop hooked up to a D-Link wireless router, and a laptop with an Intel Wireless Pro 2200 card.

OK, I am able to connect to the Internet from my laptop, which tells me the wireless card works.

But beyond simple Internet connection, I'm completely confused.  Over the past few days, I've spent hours trying to share a folder and a printer between my desktop and laptop.  I've read all about NFS, Samba, FTP, CUPS; I've installed numerous applications and gone in and out of the Konsole issuing reams of commands.  Nothing works.

I know I can't be the only one.

What I want to do seems very simple.  I just want to set a folder on my desktop for sharing, and set a folder on my laptop for sharing.  Other than that, I just want to be able to print from my laptop.

Can someone help out here?

---

### Post by wjp.reg on 2007-12-09
Sorry you're having so much difficulty with SAMBA file/print sharing.

Have you seen [this link]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP") yet?

Good luck!

OOOPPPSS! Wrong Link!! :-(

[http://my.opera.com/albuemil/blog/2007/01/12/server-file-and-printer-sharing-with-w]("http://my.opera.com/albuemil/blog/2007/01/12/server-file-and-printer-sharing-with-w")

---

### Post by MSchenker on 2007-12-09
wjp.reg,
Thanks for the link.  However, I'm not running Windows XP.  I'm running Kubuntu on my desktop and laptop.

Am I mistaken, or is it easier to share a Windows computer with Linux than it is to share two Linux computers?

---

### Post by gigaferz on 2008-01-01
No, unfortunately you are not mistaken, however 

 [http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

I have done this on the past

[http://ubuntuforums.org/showthread.php?t=91887](http://ubuntuforums.org/showthread.php?t=91887)

Also this , wich basically is another version But you are sharing only one folder not your whole home

---

### Post by jbt on 2008-01-02
> **MSchenker said:**
> wjp.reg,
Thanks for the link.  However, I'm not running Windows XP.  I'm running Kubuntu on my desktop and laptop.

Am I mistaken, or is it easier to share a Windows computer with Linux than it is to share two Linux computers?


Hi,

When I had similar problems, I found that I needed to run smbpasswd to set the smb password for the user I was connecting with.

Regards
JohnT

---

### Post by MSchenker on 2008-01-03
For now, I've given up on file sharing in Kubuntu.

It seems that every time this subject comes up, there's a whole new set of methods to try that I never heard of before, but none of them has worked for me.  I've put way too much time into file sharing, and I've decided to wait patiently until the Ubuntu/Kubuntu developers solve the problems.

In the meantime, I'm enjoying Kubuntu very much, and I'm extremely impressed with the work the developers of this operating system have done.

Matt

---

### Post by Maricaibo on 2008-01-03
I am also completely at sea. Using Ubuntu and I've read so many posts, run so many commands, none of which worked, Ubuntu says it sees my wireless card but I have never been able to connect to the router. I don't even knoe how to UNinstall, UNdo everything I've tried.

Reloaded Ubuntu so many times trying to get back to a good starting place that Windows almost seems like a good OS.

Why is it so difficult to get a wireless connection? My card works, my router works (wired) and the router works with a WinXP wireless connection.

This has become really frustrating and I feel like a complete dummy.

---

### Post by jeffus_il on 2008-01-03
Samba is hard to set up.
NFS is easier but not trivial.
I you need to to quick and easy file transfers with a friendly gui, use Filezilla.
It connects using the ftp protocol and/or more recently sftp.
All you need is to enter the remote computer name, username  and password.
And then you use the gui to browse and copy.

---

### Post by jeffus_il on 2008-01-04
If you are interested I will help you set up an nfs share which involves:
On server
1. editing a small file /etc/exports adding a line.
2. run exportfs  

On client:
1. edit /etc/fstab adding a line

That's all

---

### Post by Jman70 on 2008-01-04
This may seem obvious, but it had me up until 3:00 am. Turn of (disable) Firestarter or any other firewall you may have installed at leats temporarily while you get sharing setup.

---

