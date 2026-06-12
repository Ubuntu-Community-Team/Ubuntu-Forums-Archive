---
title: "File Sharing with Multimedia Devices"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by revhead347 on 2014-01-20
I did a search, but I really didn't find any of the information I was looking for.  I was kind of hoping to use my Ubuntu computer as a multimedia hub, and I wanted to know if that was realistically possible.  I have several WD Live boxes in the house, and i have had luck accessing files using samba.  However, I can only access files on the computer hard drive, and I would really like to access the files on the external drive.  Not sure if that's possible or not.  I also recently blew a lot of money on a super cool Samsung 5500 series Smart TV.  That has not worked at all.  Samsung directs you to download proprietary software to your computer in order to access files.  Is there an open source alternative to the proprietary software?  Can I use this computer to act as a hub, or do I need to continue to lug hard drives around the house?

Kurt

---

### Post by tfrue on 2014-01-21
I have an older desktop that was given to me and I know it's a dual core  intel processor, 512MB RAM, and came with a single 320GB drive. I have  installed another HDD along with my external drive and use Samba to  share files to all three drives. 

I use Ubuntu Server 13.10 with  no GUI, just terminal, and it works wonders! You don't have to use a  server just to use Samba, but I'm also using apache, torrent, trying to  get a PXE boot server, and a few other things but Samba will work with  the desktop versions of Ubuntu.

I will walk you through the set up if you are interested...

Chris

---

### Post by madverb on 2014-01-21
Use DLNA.

---

### Post by revhead347 on 2014-01-21
Thank you for your replies.

Kurt

---

### Post by revhead347 on 2014-01-21
I found something on the software center by Rytek called "dlna"?  Is that what you are talking about?  If not, what is the package info for dlna.  I assume it's something like "sudo apt-get install XXXXX"   Something like that.

When I go to my Windows Network share, I am unable to mount my external hard drive.  Not sure why.  I'm getting closer, but it's just not working.  It just gives me an error code "Failed to Mount."  What do I need to do to fix this?

Kurt

---

### Post by revhead347 on 2014-01-21
Chris, sorry for not responding to your post.  I would prefer to not switch to 13.10.  I also use this computer as a computer, not just a server, so the GUI is a necessity.  I think I really need to just figure out how to get this External Drive to Samba share.  If I can do that then the WD Live box will work.  That's half of it right there.  I'm trying to see if this DLNA is a reasonable substitute for Samsucks proprietary software.

Kurt

---

### Post by SeijiSensei on 2014-01-21
Many devices support the [DLNA]("http://www.techradar.com/us/news/digital-home/home-networking/dlna-what-it-is-and-what-you-need-to-know-1079015") protocol including the PS3 and smart TVs.  You can install [ps3mediaserver]("http://www.ps3mediaserver.org/") on your PC to interconnect with DLNA-enabled devices.  It re-encodes files on-the-fly into a format compatible with the media device.

---

### Post by tfrue on 2014-01-21
You don't have to use the server to use Samba, nor 13.10, but I configure Samba through the terminal so I don't know how to set it up in the GUI but it's super easy to get it up and running through the terminal.

---

### Post by tfrue on 2014-01-21
Do you have a DLNA server though? If you have devices that are DLNA compatibly, but not the server, then I don't believe that you can use DLNA.

---

### Post by revhead347 on 2014-01-21
It's back to the very steep learning curve for me here.  Let's start  with something basic.  Can anyone walk me through setting up Samba using  the terminal so that it will Windows Share files on my external hard  drive?

I do not have a DLNA server.  I do have xmbc on the computer.

Kurt

---

### Post by Morbius1 on 2014-01-21
You are using Ubuntu with a desktop environment on it - right?

Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by tfrue on 2014-01-21
I like using samba because it's simple, so here we go.

Type:
```
sudo apt-get install samba
```

Let it install, then we can edit the configuration file. Type:
```
 sudo vim /etc/samba/smb.conf
```
Scroll all the way to the bottom and type 'o', the add:
```

[NewShare] (Can be anything you want)
comment= A New Share
path= /media/mynewshare (The path to the directory you're sharing)
browseable= yes
guest ok= yes
writeable= yes
(Then hold *Shift* and press *zz* to save and exit)
```
This will be an open share that anyone on your LAN can access, we can lock it down if you want it's a small step but takes a little bit to write it so I will show you how to if you want.

---

### Post by Morbius1 on 2014-01-21
> However, I can only access files on the computer hard drive, and I would really like to access the files on the external drive.
> When I go to my Windows Network share, I am unable to mount my external hard drive. Not sure why. I'm getting closer, but it's just not working. It just gives me an error code "Failed to Mount."

A "Failed to Mount" is not a samba caused error. It's a Linux permissions caused error. 

For example. If this is the share you have already created, you simply plug in the external drive, and the device is formatted to NTFS then it will generate a "Failed to Mount" error:
> [NewShare]
comment= A New Share
path= /media/mynewshare
browseable= yes
guest ok= yes
writeable= yes
If you are using a later version of Ubuntu and the share looks something like this:
> [NewShare]
comment= A New Share
path= /media/revhead/mynewshare
browseable= yes
guest ok= yes
writeable= yes
It will also generate a "Failed to Mount" error regardless of how it's formatted.

Of course it's possible you have no share definitions at all in smb.conf since you used Nautilus to share your folders. The output of the usershare command will tell us how that is set up.

There's an easy fix if all of my assumptions are correct depending on how this is all set up but we don't know what version of Ubuntu you are using nor do we know how this  external device is formated so it would be great if you could post the output of those commands I asked for.

---

### Post by madverb on 2014-01-21
Install MiniDLNA (now known as ReadyMedia) on your computer and set it up. [https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA) [http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

---

### Post by revhead347 on 2014-01-22
So sorry for not checking this earlier.  I kept reloading the page, and didn't realize that it had gone into 2 pages.  I am using Ubuntu 12.04 with a Desktop environment.  The drive is formatted to NTFS.  There is no need to lock anything down on my network.  It's just my wife and I in here.

Kurt

---

### Post by revhead347 on 2014-01-22
> **tfrue said:**
> I like using samba because it's simple, so here we go.

```
 sudo vim /etc/samba/smb.conf
```
Scroll all the way to the bottom and type 'o', the add:
[code]


I have samba installed, and updated.  I tried this and got a "command not found"

Kurt

---

### Post by tfrue on 2014-01-23
If you know how to use nano, then you can use nano. 
```

sudo nano /etc/samba/smb.conf
```
Should work, but the save and exit commands are different.

---

### Post by Morbius1 on 2014-01-23
Good Golly Miss Molly.
> **revhead347 said:**
>  and i have had luck accessing files using samba. However, I can only access files on the computer hard drive, and I would really like to access the files on the external drive. Not sure if that's possible or not. 
[COLOR=#0000cd]*If you can access shares you created on "the computer hard drive" then you already had samba installed so I don't know what you just installed.*[/COLOR]

> **revhead347 said:**
> When I go to my Windows Network share, I am unable to mount my external hard drive. Not sure why. I'm getting closer, but it's just not working. It just gives me an error code "Failed to Mount." What do I need to do to fix this?
[COLOR=#0000cd]*Maybe it's just me but my interpretation of that post is as follows: I created a share of my external hard drive and I can see the share in Windows Network but when I access it I get a "Failed to Mount" error. *[/COLOR][COLOR=#000000]So samba is installed, the share has already been created, but you get an error when accessing it.[/COLOR]

[QUOTE=revhead347]I am using Ubuntu 12.04 with a Desktop environment. The drive is formatted to NTFS.[/QUOTE]
This would all be a lot cleaner and far more accurate if you had posted the output of the two commands I asked for but you refuse so in an attempt to resolve this issue ( [COLOR=#0000cd]at least the samba part of this topic[/COLOR] ) I'm going to shoot from the hip:

Edit smb.conf:
```
gksu gedit /etc/samba/smb.conf
```
Towards the top of the file - right under the "workgroup = workgroup" line add the following line:
```
force user = morbius
```
*[COLOR=#0000cd]**Change morbius to your own local login user name - the name you log in with.**[/COLOR]*

Save the file, open a terminal, and restart samba:
```
sudo service smbd restart
```
Can you access the samba share of your external hard drives now?

If you cannot then I need the output of those 2 commands that I have asked for 4 times now:
```
testparm -s
```
```
net userhsare info --long
```

---

### Post by revhead347 on 2014-01-23
To Morbius.  I have completed the task.  Here is the output from "testparm -s"

smbd stop/waiting
smbd start/running, process 18776
kurt@kurt-HP-Compaq-dc7600-Convertible-Minitower:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    force user = morbius

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


The following is the output from "net usershare info --long"

[Video]
path=/media/New Volume/Video
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

[Link to Video]
path=/home/kurt/Link to Video
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

[New Volume]
path=/media/New Volume
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

Kurt

---

### Post by revhead347 on 2014-01-23
Now everything on the network is failing to mount.

KUrt

---

### Post by Morbius1 on 2014-01-23
You know if I was a betting man ............
> [global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    [COLOR=#0000cd]**force user = morbius**[/COLOR]

You know what would have worked much better? For you to use the name kurt instead of morbius.

Try it again. Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Find the line:
> force user = morbius
And change it to:
> force user = kurt
Then restart smbd:
```
sudo service smbd restart
```
Wait 5 minutes for the network to settle down and see if you can access your shares again.

---

### Post by revhead347 on 2014-01-23
Wow.  I have no idea how that works, but it works.  I can access my external hard drive from my WD Live box upstairs.  Thank you so much for your help.

Sorry about being a little slow on the language.  To be honest, virtually none of this stuff makes sense, and if it weren't for this forum I would probably still be stuck screaming at a Windows 8 computer.  There are so many nickname terms in Linux, like "ice cream," etc, I didn't know if "morbius" was some code word for a general user.

Now that I have that resolved, let me see if I can get this dlna thingy configured so I can use my Smart TV.

Kurt

---

### Post by revhead347 on 2014-01-23
Ok, I installed minidlna, and my Samsung tv is detecting my computer now.  However, it does not have any folders or videos to play.  I assume that all I need to do is configure minidlna to share that external hard drive over the network.  I have read the instructions, but I am a little unsure of how to configure it.  I copied the minidlna conf.  Can anyone steer me in the right direction.

# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200

# network interfaces to serve, comma delimited
#network_interface=eth0

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
media_dir=/opt

# set this if you want to customize the name that shows up on your clients
#friendly_name=My DLNA Server

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
#db_dir=/var/cache/minidlna

# set this if you would like to specify the directory where you want MiniDLNA to store its log file
#log_dir=/var/log

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

# set this to strictly adhere to DLNA standards.
# * This will allow server-side downscaling of very large JPEG images,
#   which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no

# default presentation url is http address on port 80
#presentation_url=http://www.mylan/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=900

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678

Kurt

---

### Post by SeijiSensei on 2014-01-24
I'd guess replacing "/opt" with the path to the files you want to share is a good first step.

```

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
# can prepend the type, followed by a comma, to the directory:
# + "A" for audio (eg. media_dir=A,/home/jmaggard/Music)
# + "V" for video (eg. media_dir=V,/home/jmaggard/Videos)
# + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
media_dir=/opt

```

Maybe "media_dir=/media/New Volume" for starters?

Making the jump from Windows to running Linux servers that are configured by text files is often difficult the first time around.  Here, though, the configuration file seems to have pretty decent comments.  I know looking at a file like this for the first time can seem overwhelming, but trying reading through the comments so you can see what each directive in the file does.

---

### Post by revhead347 on 2014-01-25
Thank you for your reply.  I'm at work right now.  When I get home on Wednesday, I will give it a try.  The code logic is starting to make more sense to me.  I'm guessing that the # tag is in there to add notes to the configuration.  The programming logic ignores anything that starts with a # tag, and you add in what you want and remove the # tag so that the program follows your instructions.  Am I correct or totally off?

Kurt

---

### Post by SeijiSensei on 2014-01-26
Yes lines beginning with "#," the "hash mark," are treated as comments in nearly all configuration files.  There are a few that use semicolons or double slashes ("//") for this purpose, but they are less common.  Comments with hash marks are commonly ignored in scripting languages like the bash shell or PHP as well.

Often overrides to default settings are presented as a comment, for instance
```
# network interfaces to serve, comma delimited
#network_interface=eth0

```
I'd guess that minidlna listens on all network interfaces by default.  This line shows you how to "bind" the program to one or more specific interfaces.

---

