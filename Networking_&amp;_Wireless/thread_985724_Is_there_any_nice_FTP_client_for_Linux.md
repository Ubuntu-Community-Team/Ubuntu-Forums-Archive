---
title: "Is there any nice FTP client for Linux?"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by MockY on 2008-11-17
Ever since I completely left Windows 4 years ago, I have been missing a good, nice looking FTP client. The FTP of my choice is FlashFXP, and there is seriously not a single client that is even remotely as good. Granted, this is however not the nicest of them all, but the functionality is perfect.

Though Sir_Yaro has done a fantastic job making FlashFXP working (the thread is located [here]("http://ubuntuforums.org/showthread.php?t=351841")) it still does not fully function. Hats off for his work by the way.

This leaves me using a ftp client native to Linux, and the issue most have is that they are so ugly that it hurts to look at the GUI. A prime example would be gFTP. An uglier client is probably not possible to make. FireFTP works kind of good, though drag-n-drop is not fully supported, transfers are not listed, and there is an extremely annoying 4GB per file limit (issue with Firefox they say). Filezilla is almost as ugly as gFTP and has a very busy GUI. And working with huge amount of directories is slow as well as it jumps to the top directory when going up. So using it is not a pleasant experience.

JFTP, KFTPGrabber, Kasablanca, IglooFTP, are all very ugly (most KDE applications have an extremely ugly interface by default) and have small issues here and there that I don't like. One feature that I really miss is saved local directories upon connect. None of these clients do this, though some of them stay at the last used directory which is somewhat acceptable. Some does not save column width on remote server which get very annoying (FileZilla being one example). Another thing that is very bizarre that most of the Linux clients don't support different icons for different types of files. This makes it hard to easily browse through the directories. FireFTP does, but the choice of icons still makes it hard to easily see.

So far functionality wise, gFTP seems to be the best of the bunch but dues to it's horrible interface, I simply don't want to use it. "Weird" is probably the thought some of you get, but what is wrong with wanting a very slick looking interface?

Is there ANY client that actually works to satisfactory and at the same time look nice? There are plenty of them on Windows (and I can only assume ALL looks nice on OSX) and I have a hard time understanding the lack of the need for a nice looking, fully functional FTP client for Linux.

If the answer is no, then I just have to hang in there and wait 4 more years and see if things have changed then.

---

### Post by lifestream on 2008-11-17
Oh! How about Nautilus "File-> Connect to Server.."?

I find it to be wonderful, even though I use thunar for local files.

---

### Post by MockY on 2008-11-17
While Nautilus is a good choice, having all ftp sites listed as mount points or bookmarks is not very preferable. I don't want the sites on the desktop nor in places. I have over 30 sites that I go to regularly and that would take up my entire desktop. Besides, I can't seem to get 2 panes nor change the charset. ÅÄÖ is not displayed. I bet if I look around, I will be able to fix the last 2 issues, but it's not specifically intuitive not having something containing all the sites. I might actually use Natutilus for the site I visit every hour, but for the rest of them I am currently using FireFTP and FileZilla for larger files than 4GB.

---

### Post by bab1 on 2008-11-18
Try [Glub Tech]("http://www.glub.com/").  This is a very nice Java based secure ftp client.

---

### Post by pvella on 2008-11-18
I like FileZilla.  And it has sftp, which a lot of my people prefer to use for security reasons.

---

### Post by MockY on 2008-11-18
> **pvella said:**
> I like FileZilla.  And it has sftp, which a lot of my people prefer to use for security reasons.

Like earlier stated, FileZilla is not optimal. Besides, it is ugly.

> **bab1 said:**
> Try Glub Tech. This is a very nice Java based secure ftp client. 

I tried to install it, but it refuses to run. I get this when trying to run after successful install
```

$ ./secureftp.sh 
./secureftp.sh: 6: /usr/lib/jvm/java-6-openjdk: Permission denied

```

---

### Post by bab1 on 2008-11-18
Did you install it as root?  Use sudo.  I installed using all defaults and it worked fine.  I'm using Gutsy.

---

### Post by Sorivenul on 2008-11-18
> **MockY said:**
> So far functionality wise, gFTP seems to be the best of the bunch but dues to it's horrible interface, I simply don't want to use it. "Weird" is probably the thought some of you get, but what is wrong with wanting a very slick looking interface?

If gFTP has the best functionality for what you do, then use it and learn to cope with the poor aesthetics.  There is no logical reason to sacrifice functionality for the sake of appearance.  That's just my two cents, though.

Good luck!

---

### Post by binbash on 2008-11-18
filezilla is perfect

---

### Post by MockY on 2008-11-18
> **binbash said:**
> filezilla is perfect

Not even close though I wish this was the case
This is what bugs me with FileZilla:

[LIST]
[*] Cluttered interface with 6 panes.
[*] When working with large quantities of directories, going inside a directory and then going up again, it takes you to the top of the hierarchy. Extremely annoying. It should go back to the last directory I entered.
[*] When drag-n-drop a directory or file to your local machine, it drops it into the folder that you hover over. If you have a large quantity of directories, there will be no white space and you are therefore forced to either right-click and select download or manually create a directory. Furthermore, if a folder is renamed on the local site, the old name sticks around (as in, it displays 2 folders) until I enter another directory and back again. Having to do this and on top of that being forced to start on top of the hierarchy when going back is a pain in the butt and slows me down significantly. The last behavior does not happen every time though, but still occurs
[*] SLOW. Entering a directory with 8000 picture (just as an example) takes a significant amount of time. And more often than not, it disconnects because it can't handle the load. I tested this via LAN as well as WAN (both between 2 computers on 50mbit fiber, as well as 2 computers using regular cable). This occurs every single time. How on earth am I gonna work with such a client? I have to reconnect to the server and then try again in order to see the content.
[*] It does not use system icons for files so it makes it harder than it should be to quickly identify files.
[*] It does not have ANY move capabilities. If I want to move a file to another directory, 
[*] In order to log in to a site that you have stored in the site manager, you actually have to open the site manager and click the site you want to connect to. There should definitely be a button you click on to show saved sites. Pretty much like the Quickconnect button has.
[/LIST]

> **Sorivenul said:**
> If gFTP has the best functionality for what you do, then use it and learn to cope with the poor aesthetics. There is no logical reason to sacrifice functionality for the sake of appearance.

Why do I have to choose one of the other? Is it really that horrible to ask for both? I don't want my computer to be ONLY functional, I want working with it to be fun and pleasing to the eye as well. I spend most of my days in front of a computer, so a little eye candy makes it more fun. Is that really to much to ask for? I'm I really alone wanting both?

gFTP can't display ÅÄÖ, which makes it even less visually attractive. 
Furthermore, gFTP does not save the last directory you were in on the local site. Since gFTP for what ever weird reason shows hidden folders by default, I have to scroll like a maniac in order to get back on track again.
It has the same behavior as all the other clients when browsing large quantities of directories. Once you go up a level, you are forced to start from top, and not from the last entered directory.
However, though ugly, the interface has a logical structure with no clutter and another bonus for bookmarks.

> **bab1 said:**
> 
Did you install it as root? Use sudo.

I sure did. It would not even install if I wasn't since it creates folders outside /home ( I tried  :) ). 
The error message occurs regardles if I run it as root or not. Bizarre that it complains about permissions even if I run it with sudo.

---

### Post by Sorivenul on 2008-11-18
> **MockY said:**
> gFTP can't display ÅÄÖ, which makes it even less visually attractive.
This is strange, because it supports it for me in the directory structure, unless you are talking about localization issues...  See my attached screenshot.
The rest of the issues with gFTP don't bother me much, but I don't do nearly as much FTP work as you obviously do.

---

### Post by MockY on 2008-11-18
> **Sorivenul said:**
> This is strange, because it supports it for me in the directory structure, unless you are talking about localization issues...  See my attached screenshot.

The same works here, on local site. But it does not work on a remote site. Attached an example.

---

### Post by morningboat on 2008-11-18
Have you tried a new solid FTP client engine CrossFTP ([http://www.crossftp.com/](http://www.crossftp.com/))? It has quite good international and unicode character support,  multi-tabs support. Its Pro version can further handle SFTP/FTPS/WebDav/S3 and synchronization. Hence I think it is even better than FlashFXP. The good thing is that it is quite stable, and I recommend you have a try of this. Here is a screenshot. 

Other good ones you may be interested in is the kftpgrabber.

---

### Post by MockY on 2008-11-19
Looks like Java... :)
Actually, I think I tested this out long time ago on SuSe. Crashes were common, and I never continued using it. What I do remember (if this is the same application we are talking about) is that you could select what icon you wanted to use for specific files. I will certainly try it out.

I'll let you know how it works out.

---

### Post by bab1 on 2008-11-19
> I tried to install it, but it refuses to run. I get this when trying to run after successful install
```

$ ./secureftp.sh 
./secureftp.sh: 6: /usr/lib/jvm/java-6-openjdk: Permission denied


We can see the process with:
[CODE]
bruce@malibu:/usr/local/secureftp2_5>ps -ef |grep secureftp
bruce     [COLOR="Red"]**5223**[/COLOR]  5168  0 23:44 pts/2    00:00:00 /bin/sh ./secureftp.sh
bruce     5224  5223  8 23:44 pts/2    00:00:15 /usr/bin/java -Dfile.encoding=UTF8 -Dglub.user.dir=/home/bruce -Duser.dir=/usr/local/secureftp2_5 -jar /usr/local/secureftp2_5/secureftp2.jar


```

[/CODE]

If you used the defaults and the install was indeed successful, then the client should be installed at ```
/usr/local/secureftp2_5
```

The directory listing should look like this:
```
bruce@malibu:/usr/local/secureftp2_5>ls -l
total 1300
-rwxr-xr-x 1 root root    219 2008-11-18 07:31 ftps.sh
-r--r--r-- 1 root root 192230 2008-07-30 23:12 images.jar
drwxr-xr-x 2 root root   4096 2007-04-11 21:48 lib
-rwxr-xr-x 1 root root    204 2008-11-18 07:31 register.sh
-r--r--r-- 1 root root 569202 2008-07-30 23:12 resources.jar
-r--r--r-- 1 root root 531348 2008-07-30 23:12 secureftp2.jar
-r--r--r-- 1 root root   1829 2008-07-30 23:12 SECUREFTP.LICENSE
-r--r--r-- 1 root root   1387 2008-07-30 23:12 SECUREFTP.README
-rwxr-xr-x 1 root root    180 2008-11-18 07:31 secureftp.sh

```

This command successfully launches secureftp for me:
```
bruce@malibu:/usr/local/secureftp2_5>./secureftp.sh &
[1] [COLOR="Red"]**5223**[/COLOR]
```

Note: although secureftp.sh is owned by root, all users are able to execute it.  I notice that you are using the Java JDK instead of the JRE.  I wonder if you have the permissions set so that the JDK is what is failing rather than the secureftp.

Attached is a snapshot.

---

### Post by xen-uno on 2008-11-19
FireFTP ... an FF extension. 30 sites might be a bit heavy as you access them through a combo box but it does have a nice clean interface. I always liked AceFTP on the Windows side.

---

### Post by MockY on 2008-11-19
> **xen-uno said:**
> FireFTP ... an FF extension. 30 sites might be a bit heavy as you access them through a combo box but it does have a nice clean interface. I always liked AceFTP on the Windows side.

Like I stated in the first post, there are some show stoppers with FireFTP. It is generally very slow with large quantities of directories and its 4GB cap will sometimes make me pull my hair.

[QUOTE=morningboat]Have you tried a new solid FTP client engine CrossFTP[/QUOTE]

This client works almost perfectly in terms of functionality. There were alot of tweaking required however, but fortunately that is something you just have to do once. I have seen better looking clients but it works overall really well. 
There are some minor issues but no show stoppers: 
All icons are the same for all files. This makes it slow to quickly see what kind of files a directory has. It's not attractive either.
It does not respond to double clicks with touchpad (Java issue maybe?)
The font is randomly displayed weird (like there are multiple words on top of each other). Folders appears to be highlighted once in a while. This goes away when I scroll or enter a directory. It is however back when going back to the main directory. 
When GTK+ skin is selected, the GUI appears to be slow. The default Java Metal theme seems to work the best.

None of these things are really important since it overall works very well. It is really fast, and is capable of listing directories that have 10k+ folders in it within a second.

I'll be using this client from now on (unless something better comes along) and hope that they work a bit with the GUI over time. Thanks for the tip.

---

### Post by MockY on 2009-11-22
I finally found good candidate in [bareFTP]("http://www.bareftp.org/")
It's still a young project and it's lacking in the performance department, but is imo by far the best client on Linux.

---

