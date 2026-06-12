---
title: "minitube does not play video"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by beew on 2010-11-03
I have minitube (ver 1.2) in Maverick and Lucid. In both cases I can listen to the audio but cannot see any video. In Lucid it used to be able to play video but somehow it can't now, maybe an update has messed it up.

I checked out the faq and it suggests installing phonon-backend-gstreamer, gstreamer-ffmpeg and gstreamer-plugins-bad. But I have checked Synaptic and  all of them are installed already.

The faq also suggest creating the following symbolic link

```
sudo ln -s /usr/lib/kde4/plugins/phonon_backend /usr/lib/qt4/plugins/phonon_backend
```

My understanding of the syntax for making symbolic link is 

```
ln -s real_name_of_place invented_name_of_place
```

But I checked my folders and saw that "/usr/lib/qt4/plugins/phonon_backend"
is the real name of a folder that already exists, and instead of "/usr/lib/kde4/plugins/phonon_backend" there is a folder called "/usr/lib/kde4/plugins/phonon_platform". So this suggestion doesn't seem to make any sense.

However, on further searching I found a solution. minitube would play video if I start it in the terminal with the command

```
export XLIB_SKIP_ARGB_VISUALS=1 && minitube
```

But how can I make this automatic when I start minitube? I tried to edit the launcher by changing the command from "minitube" to the above but when I click the launcher I get the error message > Failed to execute child process "export" (No such file or directory)

I would like to know 1)if there is a way to incorporate that command into a launcher 2) if there is another way to make minitube play videos and 3) if anyone has a theory on what happens. I want to make things work but I am also interested in understanding why they don't. Thanks

---

### Post by P4man on 2010-11-03
I installed it from webup8 ppa with these commands:
```

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install minitube
```

And that worked flawlessly, even on AMD64.

If that doesnt help, to change the default launcher, I think you have to edit minitube.desktop located in /usr/share/app-install/desktop but dont quote me on that.

---

### Post by beew on 2010-11-03
I installed from the webup8 ppa too. It used to work in Lucid but not anymore, it never works in Maverick. But with the command I posted it does work beautifully.

---

### Post by mc4man on 2010-11-03
Works fine here (mav) but if you need to go 

Edit menus ( or r. click on applications - edit menus

Scroll down to Sound & Video - then r. click on r. side screen on minitube -> properties
Use this as the command

```
env XLIB_SKIP_ARGB_VISUALS=1 minitube
```


Edit above will take care of opening from menu - if for some reason you needed to edit the .desktop then 
```
gksudo gedit /usr/share/applications/minitube.desktop
```
and edit the Exec= line as above

---

### Post by P4man on 2010-11-03
Im also on maverick and also no issues here. To the OP: did you upgrade to 10.10 or do  a fresh install? If it was an upgrade, did you create that link or a similar workaround previously? Thing is, I have no KDE folder there (I dont have anything KDE installed, and I suspect that workaround is only for KDE users) but the phonon_backend folder is right there where it should be in qt4.

Then again, the SKIP_ARGB_VISUALS is probably a workaround for the videocard and has little or nothing to do with the above.

---

### Post by beew on 2010-11-03
mc4man 

Will try your suggestion regarding editing desktop file when I go home. Thanks.

P4man,

It is a fresh install, the qt4 and phonon_blackend folders are right there too. That's why I found the symlink work around puzzling and more puzzling is that some people with Ubuntu (not kubuntu) claim that it works for them. I have a KDE4 folder probably because I have installed some KDE apps such as Amarok.

---

### Post by beew on 2010-11-04
Hi mc4man

Editing the launcher command according to your instruction works perfectly. Thanks a lot!

Now I just want to understand why it works, otherwise the problem is solved.

---

### Post by beew on 2010-11-04
Ok, 

Just want to report a problem in case someone encounters it. Minitube and kdenlive somehow have conflicts in Maverick. 

After editing the launcher with mc4man's help I am able to watch videos in both Lucid and Maverick. However in Maverick I just couldn't watch HD video (720P). The picture would freeze while the audio continues.  It just happened that I had an udpate for kdenlive from a PPA and I thought that might be the problem. I downgraded it to the Ubuntu version and I was able to watch maybe a few seconds in the beginning of the clips before they freeze.  So there was some improvement and it confirmed that somehow kdenlive was implicated.  I uninstall kdenlive completely, just as by magic minitude now works flawlessly for 720p in full screen.

---

### Post by studentz on 2010-12-06
Hi there 

I did a fresh Maverick installation 64 bits. I tried to install minitube  from different ppa's, synaptic , and from source  and  I had the same problem as beew. The solution "env XLIB_SKIP_ARGB_VISUALS=1" works for me.

---

### Post by neanderslob on 2012-02-20
Thanks P4man.  Worked like a charm! :guitar:

---

