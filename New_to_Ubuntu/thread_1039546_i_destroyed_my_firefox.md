---
title: "i destroyed my firefox"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mdewet on 2009-01-14
Hardy x64

I wanted to manually install the latest version on firefox, but everything failed and now my firefox wont start.  

I used the following commands after downloading the .tar.bz2 file -(I did it all from an online tutorial, but I cant remember where it was)..firefox 3 beta 5 was still running when I did the commands..

```

muerte@muerte:~$ cp -R ~/.mozilla ~/.mozilla.backup
muerte@muerte:~$ sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
muerte@muerte:~$ rm firefox-3*.tar.bz2
muerte@muerte:~$ sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
muerte@muerte:~$ sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
muerte@muerte:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
muerte@muerte:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
muerte@muerte:~$ mv ~/.mozilla ~/.mozilla.mozillafirefox
muerte@muerte:~$ mv ~/.mozilla.backup ~/.mozilla


```

so after doing all these commands firefox wouldn't open anymore.  I tried uninstalling it through synaptic and re-installing it through apt-get, but the same problem still occurs.  

Is there anyway how I can restore firefox?

---

### Post by alienexplorers on 2009-01-14
Try reading and following this:
[http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by bumanie on 2009-01-14
Can you go to terminal and put in the following codes and post the output of the second code, please.
> cd ~/ > ls -al

---

### Post by mdewet on 2009-01-14
> **bumanie said:**
> Can you go to terminal and put in the following codes and post the output of the second code, please.

```
drwxr-xr-x 61 muerte muerte    4096 2009-01-15 00:11 .
drwxr-xr-x  3 root   root      4096 2008-12-12 20:15 ..
drwxr-xr-x  5 muerte muerte    4096 2009-01-10 20:44 .audacity1.3-muerte
drwxr-xr-x  4 muerte muerte    4096 2009-01-10 20:35 .audacity-data
-rw-------  1 muerte muerte   10343 2009-01-14 11:49 .bash_history
-rw-r--r--  1 muerte muerte     220 2008-12-12 20:15 .bash_logout
-rw-r--r--  1 muerte muerte    2928 2008-12-12 20:15 .bashrc
-rw-r--r--  1 muerte muerte  119296 2009-01-05 00:16 Besprekingsvorm.doc
drwx------  2 muerte muerte    4096 2008-12-12 19:15 .bogofilter
drwxr-xr-x  4 muerte muerte    4096 2008-12-15 17:58 .cache
drwx------  3 muerte muerte    4096 2008-12-14 09:10 .compiz
drwxr-xr-x 13 muerte muerte    4096 2009-01-04 00:28 .config
-rw-r--r--  1 muerte muerte      94 2009-01-10 16:28 Cool Command scripts
-rw-r--r--  1 muerte muerte      67 2009-01-10 16:06 Cool Command scripts~
drwx------  3 root   root      4096 2008-12-16 13:58 .dbus
drwxr-xr-x  2 muerte muerte    4096 2009-01-07 16:53 Desktop
-rw-------  1 muerte muerte      28 2009-01-14 23:25 .dmrc
drwxr-xr-x  2 muerte muerte    4096 2009-01-02 12:30 Documents
drwxr-xr-x  3 muerte muerte    4096 2009-01-13 11:59 Downloadenhausens
drwxr-xr-x 47 muerte muerte    4096 2009-01-11 21:45 .dvdcss
drwxr-xr-x  3 muerte muerte    4096 2009-01-06 13:13 DVDFab
drwxr-xr-x  4 muerte muerte    4096 2009-01-09 15:38 .emerald
-rw-------  1 muerte muerte      16 2008-12-12 18:24 .esd_auth
drwxr-xr-x  7 muerte muerte    4096 2008-12-13 11:33 .evolution
lrwxrwxrwx  1 muerte muerte      26 2008-12-12 20:15 Examples -> /usr/share/example-content
drwxr-xr-x  2 muerte muerte    4096 2009-01-10 16:22 focAudio
drwxr-xr-x  2 muerte muerte    4096 2008-12-26 21:24 .fontconfig
-rw-r--r--  1 muerte muerte 1293692 2008-02-07 07:06 Fonts.zip
drwxr-xr-x  2 muerte muerte    4096 2008-12-29 13:27 fotos
drwx------  2 muerte muerte    4096 2008-12-17 14:54 .fr-JCeNe4
drwx------  2 muerte muerte    4096 2009-01-12 10:50 .gcjwebplugin
drwx------  6 muerte muerte    4096 2009-01-14 23:25 .gconf
drwx------  2 muerte muerte    4096 2009-01-15 00:11 .gconfd
drwxr-xr-x  2 muerte muerte    4096 2009-01-09 13:54 GDM_Login
drwxr-xr-x 22 muerte muerte    4096 2008-12-29 13:12 .gimp-2.4
-rw-r-----  1 muerte muerte       0 2009-01-15 00:06 .gksu.lock
drwx------ 14 muerte muerte    4096 2009-01-14 23:26 .gnome2
drwx------  2 muerte muerte    4096 2008-12-12 19:15 .gnome2_private
drwx------  2 muerte muerte    4096 2009-01-14 23:25 .gnupg
drwxr-xr-x  2 muerte muerte    4096 2008-12-29 01:22 .gstreamer-0.10
-rw-r--r--  1 muerte muerte     112 2009-01-14 23:27 .gtk-bookmarks
dr-x------  2 muerte muerte       0 2009-01-14 23:25 .gvfs
-rw-------  1 muerte muerte     159 2009-01-14 23:25 .ICEauthority
drwxr-xr-x  5 muerte muerte    4096 2009-01-09 13:59 .icons
drwx------  4 muerte muerte    4096 2009-01-14 16:46 .liferea_1.4
drwxr-xr-x  7 muerte muerte    4096 2009-01-10 23:24 .limewire
drwxr-xr-x  6 muerte muerte    4096 2009-01-06 19:06 LimeWire
drwxr-xr-x  3 muerte muerte    4096 2008-12-12 18:24 .local
drwx------  3 muerte muerte    4096 2008-12-23 23:25 .metacity
drwx------  6 muerte muerte    4096 2009-01-13 12:01 .mozilla
drwx------  5 muerte muerte    4096 2008-12-14 08:57 .mozilla.mozillafirefox
drwx------  3 muerte muerte    4096 2008-12-13 11:31 .mozilla-thunderbird
drwxr-xr-x  2 muerte muerte    4096 2009-01-02 00:55 .mplayer
drwxr-xr-x  4 muerte muerte    4096 2008-12-24 22:50 Music
drwxr-xr-x  3 muerte muerte    4096 2009-01-14 16:46 .nautilus
drwx------  3 muerte muerte    4096 2008-12-29 13:35 .netx
-rw-------  1 muerte muerte      55 2008-12-29 13:35 .netxrc
drwx------  3 muerte muerte    4096 2009-01-14 23:32 .openoffice.org2
drwxr-xr-x  2 muerte muerte    4096 2008-12-21 10:39 PcSetup
drwx------  2 muerte muerte    4096 2008-12-17 12:55 PDF
drwxr-xr-x  2 muerte muerte    4096 2009-01-07 16:51 Pictures
-rw-r--r--  1 muerte muerte     586 2008-12-12 20:15 .profile
drwxr-xr-x  2 muerte muerte    4096 2008-12-12 18:24 Public
drwxr-xr-x  2 muerte muerte    4096 2008-12-15 10:31 .pulse
-rw-------  1 muerte muerte     256 2008-12-12 18:24 .pulse-cookie
-rw-------  1 muerte muerte    2697 2009-01-14 23:32 .recently-used
-rw-r--r--  1 muerte muerte  329318 2009-01-15 00:11 .recently-used.xbel
-rw-r--r--  1 muerte muerte 1160704 2009-01-05 00:16 save the date.doc
drwxr-xr-x  2 muerte muerte    4096 2009-01-04 00:28 .screenlets
drwx------  3 muerte muerte    4096 2009-01-14 23:27 .Skype
drwx------  2 muerte muerte    4096 2008-12-12 18:24 .ssh
-rw-r--r--  1 muerte muerte       0 2008-12-12 18:31 .sudo_as_admin_successful
drwxr-xr-x  2 muerte muerte    4096 2008-12-12 18:24 Templates
drwxr-xr-x 22 muerte muerte    4096 2009-01-09 15:39 .themes
drwx------  4 muerte muerte    4096 2008-12-14 08:20 .thumbnails
drwxr-xr-x  2 muerte muerte    4096 2008-12-28 10:52 .update-manager-core
drwx------  2 muerte muerte    4096 2008-12-12 18:24 .update-notifier
drwxr-xr-x  2 muerte muerte    4096 2008-12-12 18:24 Videos
drwxr-xr-x  3 muerte muerte    4096 2008-12-17 15:41 .vlc
drwxr-xr-x  2 muerte muerte    4096 2008-12-23 10:33 .wapi
drwxr-xr-x  4 muerte muerte    4096 2009-01-08 18:59 .wine
-rw-------  1 muerte muerte     117 2009-01-14 23:25 .Xauthority
-rw-r--r--  1 muerte muerte   20009 2009-01-15 00:11 .xsession-errors
muerte@muerte:~$ 

```

---

### Post by mdewet on 2009-01-14
> **alienexplorers said:**
> Try reading and following this:
[http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")

funny thing, this is actually the tutorial I followed..

Something weird happened now, I followed the instructions from the tutorial to remove firefox : 

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

and all of a sudden my firefox works again..with all my original bookmarks and everything:D

This was a bit twilight zone material, but at least my firefox is back!!

thanks for the help guys!

meiring

---

### Post by bumanie on 2009-01-14
Before removing everything to do with firefox, I suggest first to try and get rid of your attempted update. The standard system file is .mozilla (which you have), but you also have a .mozilla.mozillafirefox that one should not be there. To get rid of that > sudo rm -r .mozilla.mozillafirefoxThen see if firefox works with only the 'standard' system file there.

---

### Post by stchman on 2009-01-14
> **mdewet said:**
> Hardy x64

I wanted to manually install the latest version on firefox, but everything failed and now my firefox wont start.  

I used the following commands after downloading the .tar.bz2 file -(I did it all from an online tutorial, but I cant remember where it was)..firefox 3 beta 5 was still running when I did the commands..

```

muerte@muerte:~$ cp -R ~/.mozilla ~/.mozilla.backup
muerte@muerte:~$ sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
muerte@muerte:~$ rm firefox-3*.tar.bz2
muerte@muerte:~$ sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
muerte@muerte:~$ sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
muerte@muerte:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
muerte@muerte:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
muerte@muerte:~$ mv ~/.mozilla ~/.mozilla.mozillafirefox
muerte@muerte:~$ mv ~/.mozilla.backup ~/.mozilla


```

so after doing all these commands firefox wouldn't open anymore.  I tried uninstalling it through synaptic and re-installing it through apt-get, but the same problem still occurs.  

Is there anyway how I can restore firefox?

You do know that the latest Firefox is in Hardy and later (V 3.0.5)?  If you are using earlier than Hardy then nevermind.

I have wondered why Mozilla uses .tar.bz2 for Firefox and .tar.gz for Thunderbird.

Delete that version of Firefox.  This will also remove the symbolic links you created.

```
sudo rm -rf /opt/fire*

```

Reinstall Firefox 3.0.5.

```
sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
```

Now run Firefox by doing:

```
/opt/firefox/firefox
```

---

### Post by kansasnoob on 2009-01-14
Jump into Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

I'm not kidding! I did extensive testing on 4.6:

[http://ubuntuforums.org/showthread.php?t=467724&page=10](http://ubuntuforums.org/showthread.php?t=467724&page=10)

Since then the developer released a 4.6.1 to correct a teeny, tiny problem.

It's simple, download to desktop from here:

[http://sourceforge.net/project/showfiles.php?group_id=202789](http://sourceforge.net/project/showfiles.php?group_id=202789)

Then double click the file on the desktop!

Then go to terminal and run:

```
ubuntuzilla.py -a install -p firefox
```

You'll be asked a few questions and the installer does it all from there!

---

