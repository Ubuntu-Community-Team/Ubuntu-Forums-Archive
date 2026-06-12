---
title: "Cant watch iPlayer/flash videos"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by typos1 on 2009-06-30
Recently set up ubuntu jaunty (64 bit) on my machine and everythings now pretty much sorted, but I cant view ot listen to iplayer or the vast majority of flash movies. I can see them occassionally but not with sound. I ve got realplayer (but theres no 64 bit version) and messed about for hours making sure I ve got flash for 64 bit (think I have) but nothing works. I ve read several threads about it but nothing works for me. Help all I want to do is view/listen to videos, I dont want to have to reboot in windows just to watch a clip!!

(Acer Aspire T-180 AMD x64, 1gb RAM )

---

### Post by philinux on 2009-06-30
First this.

Use synaptic and uninstall all flash.

Then
```
sudo updatedb

and

locate libflashplayer.so

```
Make sure all instances gone.
Get the 64 bit flash from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Unpack the tar file and move the libflashplayer.so file to:-

/home/user/.mozilla/plugins

create the above directory if not already.
__________________

---

### Post by typos1 on 2009-06-30
That is one of the things I tried to do, but I cant get to work. I ve got 64 bit Flash and created the folder, but nothing. ll try uninstalling everything and starting again

---

### Post by typos1 on 2009-06-30
jason@jason-desktop:~$ locate libflashplayer.sosudo updatedb
/etc/updatedb.conf/alternatives/updatedb
/usr/bin/updatedb
/usr/bin/updatedb.mlocate
/usr/share/man/man5/updatedb.conf.5.gz
/usr/share/man/man8/updatedb.8.gz
jason@jason-desktop:~$ sudo updatedb
jason@jason-desktop:~$ locate libflashplayer.so
/home/jason/.local/share/Trash/files/libflashplayer.so
/home/jason/.local/share/Trash/info/libflashplayer.so.trashinfo
/home/jason/.mozilla/plugins/libflashplayer.so 
/usr/lib/mozilla/plugins/libflashplayer.so

All installed as far as I can see, but makes no difference...

And why doesnt trash empty? I "emptied" it loads and it says its done it but its still got stuff in it!

---

### Post by typos1 on 2009-06-30
Some flash stuff still plays (with no sound) when flash uninstalled! But nNOT iplayer. Hope someone can help-dont wanna have to use windows!

---

### Post by hyperdude111 on 2009-06-30
Iplayer works and always has for me. Try this it is for all codecs not just flash.


sudo apt-get install ubuntu-restricted-extras

---

### Post by typos1 on 2009-06-30
Yep, already tried that. 

Back to windows then :cry:

---

### Post by Anonymousable on 2009-06-30
If you enable medibuntu there is a package for the commercial version of flash. See [http://www.medibuntu.org/](http://www.medibuntu.org/) for what it is and instructions for enabling the repository. Then simply do
$ sudo apt-get install flashplugin-nonfree
This worked for me perfectly. Good luck with that!

---

### Post by typos1 on 2009-06-30
Done that already

(I ve enabled medibuntu, I ve installed and uninstalled flash and flash plugin, I ve made sure multiverse is selected in software sources, I even registered as am experimental user with iPlayer...nothing)

---

### Post by typos1 on 2009-07-01
ANYONE? I ve spent hours and hours on this, done so much cant remember half of it-would take a couple of hours to type what I ve done. 

I wont work, banging my head against a brick wall here.

Where can I get some support??

---

### Post by hyperdude111 on 2009-07-01
Try a re-install of ubuntu then re-do the ubnutu restricted extras command. Windows should not be required for iplayer.

You could also try a virtual machine or run the windows version of firefox in wine and install the windows flash that could also work.

---

### Post by typos1 on 2009-07-01
Thought about using wine but shouldnt have to. Shouldnt have to do a whole re-install either

---

### Post by ainsworth_t on 2009-07-01
Have you tried uninstalling firefox and flash then re-installing it?

---

