---
title: "[SOLVED] Where can I download legal movies?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by greenleaves123 on 2008-12-27
Hmmm...the other thread was closed before this question could be answered.

I find FrostWire sketchy. I've decided I won't want to download movies illegally even if I have bought the DVDs themselves. I can't do a proper search for anything it seems and I am worried about what I might be downloading. There seems to be some porn out there. I definitely do not want to accidently download porn or something.

So, without itunes, how where do I download legal movies? I want to buy legal movies that can be played on Totem. Legal blockbuster, hollywood movies that is, not little known or sketchy movies.

I live in Canada btw. Anyone know of any sites that are Ubuntu friendly? I have Ubuntu 8.04 (Hardy).

---

### Post by nhasian on 2008-12-27
how about Amazon's video on demand service?  does that work in canada?

---

### Post by greenleaves123 on 2008-12-27
I just checked out Amazon's video on demand and unfortunately they are for the U.S. only.

---

### Post by oldos2er on 2008-12-27
[http://beta.legaltorrents.com/movies](http://beta.legaltorrents.com/movies)

---

### Post by ugm6hr on 2008-12-27
> **greenleaves123 said:**
> I've decided I won't want to download movies illegally even if I have bought the DVDs themselves.

In Canada, is it legal to backup DVDs that you own, for your own personal use?

If yes - buy the DVD and use any computer with a DVD drive to "rip" the DVD to a compressed format.  I have never done this, but I understand [VLC]("http://www.wikihow.com/Rip-DVDs-with-VLC") has this facility.

---

### Post by greenleaves123 on 2008-12-27
LegalTorrents looks interesting. I will check it out. 

I tried searching for VLC, but couldn't find it, how to I get it? I'm using Ubuntu 8.04.

OK, this is a really stupid question, but any DVD drive can rip DVDs right? I have a PC with a DVD player, but can't write on DVDs. Also how to I get the file to my netbook without an optical drive? Do I need to buy one of those USB storage devices?

---

### Post by adobrakic on 2008-12-27
```
sudo apt-get install vlc
``` 
in terminal

Also, have you tried something like [this](http://www.cinemanow.com/). 
It looks like you pay for the movie and they send it through a download, rather than hard copy.

---

### Post by ugm6hr on 2008-12-27
VLC: [http://www.videolan.org/](http://www.videolan.org/)

Which PC has the DVD drive (reader), and what OS has it got?

I gather your other thread mentioned you have an Ubuntu netbook.  How are you planning on storing the film on the netbook (e.g. on internal HD, SD card etc?

---

### Post by chris200x9 on 2008-12-27
for ripping movies I recomend handbrake, the recently added a linux gui too :)

---

### Post by Wintervenom on 2008-12-27
> **greenleaves123 said:**
> So, without itunes, how where do I download legal movies?

[quote=oldos2er][http://beta.legaltorrents.com/movies](http://beta.legaltorrents.com/movies)[/quote]

Don't forget [isoHunt](http://isohunt.com), [YouTorrent](http://www.youtorrent.com), and [TorrentCat](http://www.torrentcat.com).

---

### Post by greenleaves123 on 2008-12-27
Thanks.

I got VLC and I have checked out that CinemaNow site. I found some porn there too. I think I remember that they don't have the big Hollywood hits. 

My PC uses Windows XP. I plan on storing the movie on an SD card. I'm just not sure how to do that. My PC doesn't have an SD card slot.

---

### Post by oldos2er on 2008-12-27
"LegalTorrents looks interesting. I will check it out."

 Just remembered this one too: [http://www.archive.org/index.php](http://www.archive.org/index.php)

---

### Post by Wintervenom on 2008-12-27
[Grab an SD reader for four bucks?](http://www.google.com/products?hl=en&rls=en&hs=8Ig&resnum=0&q=sd+to+usb+converter&um=1&ie=UTF-8&sa=X&oi=product_result_group&resnum=1&ct=title)

---

### Post by ugm6hr on 2008-12-27
> **Wintervenom said:**
> [Grab an SD reader for four bucks?](http://www.google.com/products?hl=en&rls=en&hs=8Ig&resnum=0&q=sd+to+usb+converter&um=1&ie=UTF-8&sa=X&oi=product_result_group&resnum=1&ct=title)

I agree.

SD (or even multi-format) card readers are so cheap, you may as well.  They are available in supermarkets in the UK - I'm sure Canada is no different.
If you have a digital camera, it saves time transferring photos too.

If you really don't want to spend any money, you could network your XP PC and your Ubuntu Netbook and transfer files that way too.

---

### Post by greenleaves123 on 2008-12-27
Thanks, I didn't know there were external SD readers out there. I will buy one then. 
 
I don't know how to network the computers.

So here is the plan, buy DVD, rip DVD on computer with xp, buy SD/multimedia reader for computer with xp, put movie file on SD card (does it matter what kind of file it is?) then use card on netbook with Ubuntu.

---

### Post by Wintervenom on 2008-12-27
> **greenleaves123 said:**
> does it matter what kind of file it is?

Nope, it should not matter.

---

### Post by ugm6hr on 2008-12-28
> **Wintervenom said:**
> Nope, it should not matter.

If using SD cards to store, xvid or divx is supposed to be significantly compressed without too much quality loss.

This might be helpful: [http://youtube.jimmyr.com/tutorials/sdQKtxto7C4.php](http://youtube.jimmyr.com/tutorials/sdQKtxto7C4.php)

VLC supports lots of options: [http://wiki.videolan.org/VLC_Features_Formats](http://wiki.videolan.org/VLC_Features_Formats)

---

### Post by soapBAR2 on 2009-01-04
> **greenleaves123 said:**
> I don't know how to network the computers.

It's as easy as pie on Windows-to-Ubuntu (ie. everything will be located on your windows computer), assuming your computers are both connected to one another somehow (and both turned on/logged in). This is not the only method, but this is (in my opinion) the easiest and the best. It works with (as far as I'm aware) nearly every linux-based system, Mac OSX, and Windows 95 and upwards.

In Windows, right-click on the folder you want to share, select the "sharing and security" tab, click "share this folder" and "allow network users to change the files", give the share a name, and click through all the security popups. 

Then, find the IP of your Windows PC (If you don't know it, click start, run, type "cmd", and in the command prompt window type "ipconfig". This will tell you your IP Address - if you have more than one (Vista spits out dozens), use the one that is not 0.0.0.0 or 255.255.255.255).

Then, on your linux machine, open up a console and type
```

apt-get update
sudo apt-get install samba
```

Then, for example;
Your Windows Share Name: share
Your Windows IP Address: 192.168.2.1
The Folder You Want To Mount In*: /home/user/share

the last command would be
```

sudo mount -o noperm -t cifs //192.168.2.1/share /home/user/share
```

Just make sure the folder you want to mount in has proper permissions (in case you don't know, 
```
chmod -R 777 /folder/
``` 
will give you maximum permissions for everything in the folder). If you put the folder within your home directory, it will certainly have permissions.

If you want to unmount, the code is
```
sudo umount /home/user/share
```
If you don't unmount before shutting down, your computer may take a while to shut down (but there won't be any permanent damage). 

*If the folder you mount in is not empty, the files in it will be inaccessible until you unmount.

==================================================
==================================================

Going the other direction (accessing a ubuntu share from windows) is a little harder, but here it is:

Open a terminal, and type
```
ifconfig
```
and record your non-0'd "inet address" (IP Address) on paper/in your head.
Assuming your text editor is nano (it may be nano, gedit, kate, xim, or another one), type
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.default
sudo nano /etc/samba/smb.conf
```
Go to the bottom of the file.

Then, for example;
Your Ubuntu Share Name: share
Your Ubuntu Share Folder: /home/user/sharing
Your Ubuntu IP Address: 192.168.2.2
Who You Want To Give Access To*: Everyone
You would append the following (copying the format)

```
[share]
path = /home/user/sharing
public = yes
read only = no
guest ok = yes
public = yes
browseable = yes
valid users = user guest nobody
write list = user guest nobody
create mask = 0777
```

Exit and save the file
Type
```
sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start
```

Go to your Windows PC, go to My Computer (in '98, "Network Neighbourhood"), click Tools, click "Map Network Drive", put in your Ubuntu PC's IP address (in the example, 192.168.2.2), and put in the share name (in the example, share), and then pick an unallocated drive letter (doesn't particularly matter what). Then, you should be seeing the contents of /home/user/sharing from your Windows computer.

*There are other options, have a look at 
```
man smb.conf
```

---

### Post by MenZa on 2009-01-04
I can't believe noone mentioned [Creative Commons](http://creativecommons.org) yet. Allows you to search for and download freely-licensed images, music, and videos.

> **retskrad said:**
> What's so bad with installing a couple of movies in torrents`? it's not that you get caught, just dont share after you have downloaded. If if you sell or download hunders of them, maybe they will get to you.

It's against the law in most juristictions and we do not condone this behaviour on the Ubuntu Forums. Check out section 3.7 from the [Forum Policy](http://ubuntuforums.org/index.php?page=policy).

---

