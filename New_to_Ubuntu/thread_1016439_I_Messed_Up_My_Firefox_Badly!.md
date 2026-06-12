---
title: "I Messed Up My Firefox Badly!"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by lisar915 on 2008-12-19
Hi everyone,

I'm relatively new to using Ubuntu.  Everything was fine today, until I downloaded and installed a bunch of software upgrades.  After I did that, I was unable to type in and go to other websites using the Firefox browser.  So I foolishly tried removing and reinstalling the browser, which made things worse.  Now I when I click on the icon, Firefox doesn't even open. 

I believe I'm using version 8.04.  So if anyone has suggestions, please let me know.  

Thank you.

Lisa

---

### Post by SuperSonic4 on 2008-12-19
```
sudo rm -r ~/.mozilla
```

this will (after asking for confirmation) delete ~/.mozilla and you'll lose your saved data like bookmarks etc and relaunching firefox should act as default

---

### Post by lisar915 on 2008-12-19
Thank you for your quick response.  I tried doing just that and got the following response:

rm: cannot remove `/home/lisa/.mozilla': No such file or directory

That's very weird considering I just installed Mozilla.

---

### Post by lisar915 on 2008-12-19
Anybody?

---

### Post by Moop on 2008-12-19
What error message do you get if you type firefox into a terminal?

---

### Post by lisar915 on 2008-12-19
I haven't tried typing Firefox into the termina.  I just tried double clicking on the icon.  And nothing happens.

---

### Post by bumanie on 2008-12-19
Before trying a removal, have you tried synaptic package manager to remove and reinstall firefox - might be a safer method to try initially. If you completely remove ~/.mozilla you should be able to get the linux version from the firefox site. If you can't get firefox to work in its present state, you may have to do the download from the live cd and transfer it to a usb stick or else extract the .mozilla file from the installation cd. Post the error (if any) from typing firefox in terminal as suggested above. I would try synaptic package manager, before trying a forced removal. 
The code given by SuperSonic4 should have been > sudo rmdir -r ~/.mozillabecause mozilla is a directory, however this will unlikely work unless the directory is empty in which case you can try a forced removal with > sudo rmdir -rf ~/.mozillaThat should only be done as a **last resort**, in my opinion. By the way in linux to launch most applications, only a single click is needed.

---

### Post by cigtoxdoc on 2008-12-19
I had same thing happen to me.  I ran upgrade as it was marked critical.  I went out to appointment.  When I came back, my FireFox was trashed.  It will not go to home page, unless I manually do URL.  I have lost all my bookmarks.

How do I recover my bookmarks and how do I get back to where I was at noon EST on 19 December?

Who checks out the software BEFORE it is released to general users.  I thought 8.10 was a stable release.

John

---

### Post by lisar915 on 2008-12-19
Hi Bumanie,

I tried installing and uninstalling Firefox through the Synaptic Package Manager, but it didn't help.  I also tried typing the command you suggest and got the following message:

rmdir: invalid option -- r
Try `rmdir --help' for more information.

---

### Post by bumanie on 2008-12-20
Well, if you really want to force remove .mozilla, I'm sorry I got the syntax the wrong way around, apparently it should be > sudo rm -rf ~/.mozillarmdir seems to be only used if the directory is empty. But be sure you want to remove firefox entirely - it's your call. I guess if firefox has no response and synaptic has not helped, you don't have much choice, but that command will totally wipe firefox from your system. I did this once myself, but can't remember exact details  - I think I downloaded the linux version, installed it and then right clicked on the top panel and clicked 'add to panel' and then typed firefox in the box to get the launch icon back. Good luck.

---

### Post by lisar915 on 2008-12-20
I just tried that, and it said "command not found."

---

### Post by bumanie on 2008-12-20
OK we'll try another way. In terminal > cd ~/then > ls -alpost the output of the second command.

---

### Post by lisar915 on 2008-12-20
That second command did something.  Here's what come up after I typed it:

total 628
drwxr-xr-x 72 lisa lisa   4096 2008-12-19 22:51 .
drwxr-xr-x  3 root root   4096 2008-05-07 08:07 ..
drwx------  4 lisa lisa   4096 2008-06-12 18:13 .adobe
-rw-r--r--  1 lisa lisa    102 2008-05-12 19:09 .apport-ignore.xml
-rw-------  1 lisa lisa   3700 2008-12-20 00:02 .bash_history
-rw-r--r--  1 lisa lisa    220 2008-05-07 08:07 .bash_logout
-rw-r--r--  1 lisa lisa   2298 2008-05-07 08:07 .bashrc
drwxr-xr-x  3 lisa lisa   4096 2008-05-17 20:48 .bb
srwxr-xr-x  1 lisa lisa      0 2008-11-26 20:27 .Blam.lisa
drwx------  2 lisa lisa   4096 2008-05-15 23:52 .bogofilter
drwxr-xr-x  3 lisa lisa   4096 2008-05-11 18:10 .cache
drwxrwxrwx  2 lisa lisa   4096 2008-10-18 21:08 Central Park Zoo Pictures
drwxr-xr-x 10 lisa lisa   4096 2008-11-20 23:50 .config
drwxr-xr-x  3 lisa lisa   4096 2008-12-19 18:34 Desktop
-rw-------  1 lisa lisa     27 2008-12-19 17:29 .dmrc
drwxr-xr-x  2 lisa lisa   4096 2008-06-12 18:37 Documents
drwxr-xr-x  9 lisa lisa   4096 2008-10-03 18:10 .dvdcss
-rw-------  1 lisa lisa     16 2008-05-07 12:16 .esd_auth
drwxr-xr-x  8 lisa lisa   4096 2008-12-18 23:30 .evolution
lrwxrwxrwx  1 lisa lisa     26 2008-05-07 08:07 Examples -> /usr/share/example-content
drwx------  2 lisa lisa   4096 2008-12-04 21:53 .filezilla
drwxr-xr-x  2 lisa lisa   4096 2008-07-03 19:34 .fontconfig
drwx------  2 lisa lisa   4096 2008-05-07 19:57 .gaim
drwx------  4 lisa lisa   4096 2008-12-20 00:10 .galeon
drwxr-xr-x  2 lisa lisa   4096 2008-09-25 23:40 .GalleryRemote
drwx------  2 lisa lisa   4096 2008-05-16 23:45 .gcjwebplugin
drwx------  6 lisa lisa   4096 2008-12-19 17:29 .gconf
drwx------  2 lisa lisa   4096 2008-12-20 00:11 .gconfd
drwx------  3 lisa lisa   4096 2008-05-07 20:13 .gftp
drwxr-xr-x 21 lisa lisa   4096 2008-05-07 19:02 .gimp-2.2
drwxr-xr-x 20 lisa lisa   4096 2008-10-22 22:42 .gimp-2.4
-rw-r-----  1 lisa lisa      0 2008-12-19 22:07 .gksu.lock
drwxr-xr-x  4 lisa lisa   4096 2008-05-15 22:41 .gnome
drwx------ 21 lisa lisa   4096 2008-12-18 23:30 .gnome2
drwx------  2 lisa lisa   4096 2008-05-07 12:16 .gnome2_private
drwx------  2 lisa lisa   4096 2008-12-19 17:29 .gnupg
drwxr-xr-x  5 lisa lisa   4096 2008-05-28 22:24 GNUstep
drwxr-xr-x  2 lisa lisa   4096 2008-05-11 22:23 .gpilotd
-rw-r--r--  1 lisa lisa      4 2008-05-11 22:23 .gpilotd.pid
drwxr-xr-x  2 lisa lisa   4096 2008-10-29 19:29 .gstreamer-0.10
-rw-------  1 lisa lisa    124 2008-12-19 22:06 .gtk-bookmarks
-rw-r--r--  1 lisa lisa     86 2008-05-07 12:16 .gtkrc-1.2-gnome2
drwx------  2 lisa lisa   4096 2008-05-12 19:07 .gvfs
drwxr-xr-x  2 lisa lisa   4096 2008-05-15 22:51 .helix
-rw-r--r--  1 lisa lisa     60 2008-06-03 20:13 .htaccess
-rw-------  1 lisa lisa  23142 2008-12-01 15:24 .hxplayerrc
-rw-------  1 lisa lisa   2071 2008-12-19 17:29 .ICEauthority
drwxr-xr-x  2 lisa lisa   4096 2008-05-12 22:25 .icons
drwxr-xr-x  4 lisa lisa   4096 2008-05-17 20:48 .java
drwx------  9 lisa lisa   4096 2008-12-19 18:07 .kazehakase
drwx------  3 lisa lisa   4096 2008-05-07 21:06 .kde
drwx------  3 lisa lisa   4096 2008-09-28 11:27 .kde4
drwx------  4 lisa lisa   4096 2008-11-23 22:32 .liferea_1.4
drwxr-xr-x  3 lisa lisa   4096 2008-05-07 19:10 .local
drwx------  3 lisa lisa   4096 2008-05-07 15:42 .macromedia
-rw-r--r--  1 lisa lisa   4206 2008-05-15 22:51 .mailcap
drwxr-xr-x  3 lisa lisa   4096 2008-05-07 21:06 .mcop
-rw-------  1 lisa lisa     31 2008-11-26 21:08 .mcoprc
drwx------  3 lisa lisa   4096 2008-05-07 12:16 .metacity
drwxr-xr-x  2 lisa lisa   4096 2008-05-15 20:30 .mplayer
drwxr-xr-x  2 lisa lisa   4096 2008-05-11 18:10 Music
drwxr-xr-x  3 lisa lisa  12288 2008-12-18 23:30 .nautilus
drwx------  3 lisa lisa   4096 2008-12-14 23:55 .openoffice.org2
drwx------  9 lisa lisa   4096 2008-05-11 22:50 .opera
drwxr-xr-x  3 lisa lisa   4096 2008-05-11 22:46 .pan2
drwx------  2 lisa lisa   4096 2008-05-31 23:05 PDF
drwxr-xr-x  2 lisa lisa   4096 2008-06-12 18:15 .pdfedit
drwxr-xr-x  2 lisa lisa   4096 2008-09-28 11:27 Pictures
drwx------  3 lisa lisa   4096 2008-05-24 18:29 .prism
-rw-r--r--  1 lisa lisa    566 2008-05-07 08:07 .profile
drwxr-xr-x  2 lisa lisa   4096 2008-05-11 18:10 Public
drwxr-xr-x  2 lisa lisa   4096 2008-05-12 22:55 .pulse
-rw-------  1 lisa lisa    256 2008-05-12 19:07 .pulse-cookie
drwx------  5 lisa lisa   4096 2008-05-12 19:29 .purple
drwxr-xr-x  2 lisa lisa   4096 2008-11-26 21:08 .qt
drwxr-xr-x 10 lisa lisa   4096 2008-02-25 04:10 RealPlayer
-rw-------  1 lisa lisa   4081 2008-12-14 23:55 .recently-used
-rw-r--r--  1 lisa lisa 106200 2008-12-19 22:05 .recently-used.xbel
drwxr-xr-x  4 lisa lisa   4096 2008-11-26 20:38 .rssowl2
drwxrwx---  3 lisa lisa   4096 2008-08-30 10:29 .sane
drwx------  2 lisa lisa   4096 2008-05-12 19:06 .ssh
-rw-r--r--  1 lisa lisa      0 2008-05-07 15:25 .sudo_as_admin_successful
drwxr-xr-x  2 lisa lisa   4096 2008-05-11 18:10 Templates
drwxr-xr-x  2 lisa lisa   4096 2008-05-12 22:25 .themes
drwx------  5 lisa lisa   4096 2008-06-24 22:49 .thumbnails
drwxr-xr-x  4 lisa lisa   4096 2008-12-08 18:45 .tomboy
-rw-r--r--  1 lisa lisa   5026 2008-12-09 00:24 .tomboy.log
drwx------  2 lisa lisa   4096 2008-05-07 21:04 .tsclient
drwxr-xr-x  2 lisa lisa   4096 2008-05-13 17:37 .update-manager-core
drwx------  2 lisa lisa   4096 2008-06-10 23:20 .update-notifier
drwxr-xr-x  2 lisa lisa   4096 2008-05-11 18:10 Videos
drwxr-xr-x  3 lisa lisa   4096 2008-05-15 23:41 .vlc
drwx------  3 lisa lisa   4096 2008-05-18 21:53 .w3m
drwxr-xr-x  3 lisa lisa   4096 2008-12-09 00:24 .wapi
-rw-------  1 lisa lisa    122 2008-12-19 17:29 .Xauthority
drwxr-xr-x  2 lisa lisa   4096 2008-12-01 18:56 .xine
-rw-r--r--  1 lisa lisa 116078 2008-12-19 22:31 .xsession-errors

---

### Post by bumanie on 2008-12-20
You have no .mozilla file there at all, hence the error messages that we are getting re no directory etc. My .mozilla is listed in ~/ (see red highlight)
drwx------  2 ian  ian        4096 2008-11-05 18:24 .lives-dir
drwxr-xr-x  3 ian  ian        4096 2008-03-05 18:41 .local
drwx------  3 ian  ian        4096 2008-03-06 19:45 .macromedia
drwxr-xr-x  3 ian  ian        4096 2008-03-07 00:38 .mcop
-rw-------  1 ian  ian          31 2008-11-14 18:46 .mcoprc
drwx------  3 ian  ian        4096 2008-03-05 18:41 .metacity
-rw-r--r--  1 ian  ian       81244 2008-12-14 21:10 Mimip2.jpeg
[COLOR="Red"]drwx------  4 ian  ian        4096 2008-11-05 15:46 .mozilla[/COLOR]
drwx------  2 ian  ian        4096 2008-11-14 00:34 .mplayer
drwxr-xr-x  2 ian  ian        4096 2008-03-05 18:41 Music
drwxr-xr-x  3 ian  ian        4096 2008-12-19 11:00 .nautilus
drwx------  3 ian  ian        4096 2008-11-07 11:20 .netx
-rw-r--r--  1 ian  ian          54 2008-11-22 18:04 .netxrc
drwxr-xr-x  4 ian  ian        4096 2008-11-17 20:55 .nexuiz

[COLOR="Black"]You seem to have removed .mozilla somehow already. Suggest booting a live ubuntu cd, going to firefox site and downloading the linux firefox version and then transferring to a usb stick and then installing on ubuntu and creating a launch icon as previously described. Good luck and let us know how you go[/COLOR]

---

### Post by lisar915 on 2008-12-20
Thanks.  

Now I don't mean to sound ignorant.  But why can't I just download it like I download other programs?  I don't have a USB stick.

---

### Post by bumanie on 2008-12-20
If firefox is not working, how are you going to connect to the internet? If you have a dual boot with windows, you may have to search a bit to find the linux version of firefox as the firefox site recognizes which OS you are using and offers you the version that matches your OS. Obviously you are connecting somehow now, so, probably no need to use the live cd, just thought it would offer you the linux version and may be easier than searching for one - but I have not tried, the linux version is probably easy to find. Download it however you are able to :D

---

### Post by -kg- on 2008-12-20
> If firefox is not working, how are you going to connect to the internet?

Uh, do you need a browser to use "apt-get" from the terminal?

---

### Post by Zeedok on 2008-12-20
> **-kg- said:**
> Uh, do you need a browser to use "apt-get" from the terminal?
 
No, but "apt-get" will do the same thing as synaptic (which didn't work).  Try installing another browser in synaptic for now (I used midori the other day when I had a problem with firefox) and you can download the package you need.  

Good luck:p

---

### Post by lisar915 on 2008-12-20
Hi, 

The reason I'm able to access the internet is because I installed another browser called Galeon.  It's not bad, but I prefer Firefox.  So if any of you know of the best way to get it back on my system, that would be great.  

Thanks.
Lisa

---

### Post by kansasnoob on 2008-12-20
I had trouble with recent updates to Firefox (in 8.10) and for the first time tried Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/?f=print](http://ubuntuzilla.wiki.sourceforge.net/?f=print)

They also have a 3rd party entry at this forum:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

It went flawlessly in Intrepid!

But if this is 8.04 I've had no problems there. In 8.04 I'd first try going to terminal and:

```
sudo apt-get install --reinstall firefox-3.0
```

```
sudo apt-get update
```

```
sudo apt-get -f install
```

And with each command follow instructions! Just add sudo to the front, like if it says "run apt-get autoremove" you'd add sudo to the front of that command.

---

### Post by lisar915 on 2008-12-20
Thank you Kansasnoob.  I was able to reinstall Firefox after typing this:

sudo apt-get install --reinstall firefox-3.0

You guys are the best!

---

### Post by ukch on 2009-01-07
> **bumanie said:**
> that command will totally wipe firefox from your system.

No, it won't. It only removes your profile, which is then re-generated when you next start Firefox. Please check the truth of your post before you make it!!

---

