---
title: "Home Server"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by metro0308 on 2010-01-21
Hello.... 

I'm looking to set my old Dell desktop as a home server. I want to use it for file (pictures, word, etc) storage and as a itunes server all of which can be accessed remotely. I think I have decide on ubuntu server. 

Can anyone give me any tip, comments, advice? This would be my absolute first time doing this. While I'm never used a Linux based OS I'm pretty good with figuring things out on my own. 

Thanks.

---

### Post by tom.swartz07 on 2010-01-21
> **metro0308 said:**
> Hello.... 

I'm looking to set my old Dell desktop as a home server. I want to use it for file (pictures, word, etc) storage and as a itunes server all of which can be accessed remotely. I think I have decide on ubuntu server. 

Can anyone give me any tip, comments, advice? This would be my absolute first time doing this. While I'm never used a Linux based OS I'm pretty good with figuring things out on my own. 

Thanks.

While you should have no problems setting up the file storage, you will definitely run into trouble with iTunes.

Currently there is no iTunes support for the most up-to-date version of the program. A few people have had success with way old versions of iTunes, but thats about it.
You could look into trying another program for music, such as songbird or rhythmbox?

---

### Post by metro0308 on 2010-01-21
That sucks... I still have DRM on about quater of my music b/c I refuse to pay again to have it removed just b/c I am stubborn.

---

### Post by wojox on 2010-01-21
You can look at the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") . FYI Ubuntu server is all command line, but you could install a lite weight Desktop if you need. If you really want to learn it and have fun just use the command line.

---

### Post by lisati on 2010-01-21
Setting up a basic FTP arrangement is fairly straightforward with vsftpd but you might want to consider limiting users' access to their home folders or some such arrangement. Documentation on vsftpd can be found on the previously mentioned server guide.

---

### Post by tom.swartz07 on 2010-01-21
> **metro0308 said:**
> That sucks... I still have DRM on about quater of my music b/c I refuse to pay again to have it removed just b/c I am stubborn.

You could just burn it to CDs and re-rip it in .mp3
That'll remove the DRM on it, but its a time consuming method.


Ive been thinking about doing the same to my collection. I have about 1,000 or so songs that need to be converted. haha

---

### Post by metro0308 on 2010-01-22
How would you compare this vs Openfiler? It seems they over, or have offered itunes server support but from a user standpoint seems more intense then this.

---

### Post by chrisinspace on 2010-01-22
> **lisati said:**
> Setting up a basic FTP arrangement is fairly straightforward with vsftpd but you might want to consider limiting users' access to their home folders or some such arrangement. Documentation on vsftpd can be found on the previously mentioned server guide.

Even easier is sftp over ssh.  Just install OpenSSH on your server, make a few [configuration changes]("http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html"), set up the appropriate rules on your router, and then use Filezilla go access it from anywhere.

---

### Post by metro0308 on 2010-01-23
Instaled the server software and I'm trying to setup stuff up but for some reason I can't enter my password, it takes every other character when I type it in and when I try to set up the LDAP server I get the options screen and I have a fatal error that bascially shuts me down. Any ideas why?

---

### Post by Bridgette on 2010-01-23
> **wojox said:**
> You can look at the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") . FYI Ubuntu server is all command line, but you could install a lite weight Desktop if you need. If you really want to learn it and have fun just use the command line.
 
 
When u say lightweight desktop on the server edition, which ones work and which dont?, which are the best?
 
Thanks
Bree

---

### Post by scratman on 2010-01-23
WinFF would probably be the best way to convert the audio files without losing too much quality.  Just convert to WAV and then back to MP3.

---

### Post by rbscairns on 2010-01-23
Metro, from what you have posted here, it looks like what you are really trying to do is set up your Dell desktop as a network attached storage (NAS). Have you given serious consideration to using FreeNAS that also supports iTunes and has a GUI (via http)?

I have been using FreeNAS for about a year now and find it rock-solid.

---

### Post by lisati on 2010-01-23
> **Bridgette said:**
> When u say lightweight desktop on the server edition, which ones work and which dont?, which are the best?
 
Thanks
Bree

My $0.02, drawn in part from personal experience:
It can depend on your system and what you need. My old backup machine can't handle any of the Ubuntu-friendly GUIs I've tried (not enough RAM or processing power), but my newer desktop that I've set up as a server has the regular GNOME-based GUI. 

This *might* be "overkill", but will provide a GUI:
```
sudo apt-get install ubuntu-desktop
```

You might also want to look here: [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by Bridgette on 2010-01-23
Hi
So u have Gnome loaded ontop of the Server edition or are u saying just load the desktop version, I have been slowely and steadily learning and having fun but i need to get the LAN working and the server edition wont recognise my onboard LAN chipset and loading the driver for this hardware is the main issue I have thats driving me nuts, get over one hurdle and then theres another
So does Gnome or similar programs make it easier to load drivers etc
 
Thanks
Bree

---

