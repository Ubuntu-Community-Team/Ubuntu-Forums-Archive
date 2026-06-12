---
title: "Problems connecting to FTP server."
date: 2009-07-29
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2009-07-29
I am trying to get gFTP to transfer files to my PS2's ExecFTP server. I have been able to connect to the server using FlashFXP on Windows 7 but haven't been able to get gFTP to connect to the server at all. Whenever I try to connect to the server I get this in my log:

```

Looking up 192.168.0.10
Trying 192.168.0.10:21
Connected to 192.168.0.10:21
220 ps2ftpd ready.
USER anonymous

220 modified by SlicStik__
SYST

230 Login ok.
TYPE I

215 UNIX Type: L8
PWD

200 Type set to I.
Invalid response '2' received from server.
Disconnecting from site 192.168.0.10

```

I have "Passive file transfers", "Resolve Remote Symlinks" and "Transfer files in ASCII mode" enabled in the FTP>Ftp settings tab.

fyi: the settings on FlashFXP are the same as gFTP and FlashFXP connects just fine to the server.

If anyone could help me out here I would really, really appreciate it. I am pulling out my hair here. I don't see why it would connect on Windows and not on Ubuntu...

---

### Post by asmoore82 on 2009-07-29
I would try filezilla

---

### Post by skaldicpoet9 on 2009-07-29
> **asmoore82 said:**
> I would try filezilla

I can't apparently:

> 
FileZilla FTP client cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

:(


I wish I could figure this out....

...and while I am here, just to save from creating another thread, but does anyone know what the default server name for Samba is? Or how I can change it/view it?

---

### Post by winemaker9 on 2009-07-29
'stealing the answer' from 

[http://ubuntuforums.org/showthread.php?t=1167759]("http://ubuntuforums.org/showthread.php?t=1167759")

It appears that filezilla loads just fine from command line..

> 
[INDENT][FONT="Arial Black"]sudo apt-get install filezilla[/FONT][/INDENT]

---

### Post by skaldicpoet9 on 2009-07-29
Awesome, thanks for the reply. That worked just great! However, I am still curious about why gFTP (or FTP, KFTPGrabber and others) would not connect. Does anyone know why?

---

### Post by MockY on 2009-07-29
I would use bareFTP. By far the neatest client for Linux, imo.
[http://www.bareftp.org/download.php](http://www.bareftp.org/download.php)

---

