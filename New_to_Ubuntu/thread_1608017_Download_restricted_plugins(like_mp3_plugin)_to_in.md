---
title: "Download restricted plugins(like mp3 plugin) to install them offline"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-10-28
:confused: Ok I know the plugins to play mp3,m4a,mkv etc I need to go online and download required things.Can someone tell me download links for all these(especially for m4a songs I have lots of them!) plugins so these can be installed offline in ubuntu 10.10?

Please tell links for ALL these music and movie plugins,like mkv,avi,aac,m4a etc

---

### Post by amjjawad on 2010-10-28
> **dhiman33 said:**
> :confused: Ok I know the plugins to play mp3,m4a,mkv etc I need to go online and download required things.Can someone tell me download links for all these(especially for m4a songs I have lots of them!) plugins so these can be installed offline in ubuntu 10.10?

Please tell links for ALL these music and movie plugins,like mkv,avi,aac,m4a etc
Why offline? I don't get it!

---

### Post by garuda10 on 2010-10-28
> **dhiman33 said:**
> :confused: Ok I know the plugins to play mp3,m4a,mkv etc I need to go online and download required things.Can someone tell me download links for all these(especially for m4a songs I have lots of them!) plugins so these can be installed offline in ubuntu 10.10?

Please tell links for ALL these music and movie plugins,like mkv,avi,aac,m4a etc

Well, to be frank, I've never faced problems with playing different formats on ubuntu. Just use either Gnome player or VLC player and you should be good to go... Both of them are available via the software manager...

---

### Post by sisco311 on 2010-10-28
> **dhiman33 said:**
> :confused: Ok I know the plugins to play mp3,m4a,mkv etc I need to go online and download required things.Can someone tell me download links for all these(especially for m4a songs I have lots of them!) plugins so these can be installed offline in ubuntu 10.10?

Please tell links for ALL these music and movie plugins,like mkv,avi,aac,m4a etc

You can use keryx to download any package and its dependencies from the Ubuntu repositories, then install them on an offline Ubuntu machine.

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by beew on 2010-10-28
> **amjjawad said:**
> Why offline? I don't get it!

Because OP has no internet access and must use a different machine at a friend's or at work  to get those packages? Otherwise I can't think of a good reason.

---

### Post by amjjawad on 2010-10-28
> **beew said:**
> Because OP has no internet access and must use a different machine at a friend's or at work  to get those packages? Otherwise I can't think of a good reason.

Hmmm, okay, that makes sense if that's the case :)

---

### Post by beew on 2010-10-28
Or maybe it is illegal to download those proprietary stuffs in his/her country.:twisted:

---

### Post by darkhelmetchris on 2010-10-28
> **dhiman33 said:**
> :confused: Ok I know the plugins to play mp3,m4a,mkv etc I need to go online and download required things.Can someone tell me download links for all these(especially for m4a songs I have lots of them!) plugins so these can be installed offline in ubuntu 10.10?

Please tell links for ALL these music and movie plugins,like mkv,avi,aac,m4a etc

I think it would be difficult to research them all and provide individual links, but I can offer you another solution.  Here is how I would implement a work-around solution:

If you install all these updates on a system that is running Ubuntu, you can then save the .deb files that it downloaded- they are kept in the apt archive folder.

If you examine this path:
/var/cache/apt/archives/
you will find (mostly) all of the stuff you have asked the package manager to get for you, and they will be in convenient .deb format.  Just save the ones you want to some removable media, and take them to the new machine that is off-line.  You can just double-click the .deb files and load them on the second machine.  You'll have to be careful to include prerequistes if they are needed - watch what it downloads.

If you want a little more automation, then one of the following:
1.  Use a clean install of Ubuntu, and do what I suggest above, your apt-archive should be quite bare.
2.  If using a clean Ubuntu install is not desirable, sudo-move the existing .deb files from that apt-archive path to some temporary path, do all the installs of the updates, and then you should only be left with what you did since the time you moved the other .debs to your temporary path.  Once you take a copy of what's left, put the old .debs back (if there were some) and your system is cleanly restored.

Then take the results to your offline machine.

---

### Post by darkhelmetchris on 2010-10-28
> **sisco311 said:**
> You can use keryx to download any package and its dependencies from the Ubuntu repositories, then install them on an offline Ubuntu machine.

[http://keryxproject.org/](http://keryxproject.org/)

Oh nice.  I didn't know that existed.  Thanks.

---

### Post by dhiman33 on 2010-10-30
):PHere's what I've done. I've tried to open mp3 without internet. It showed some plugins are to be downloaded to play the format.I listed those download links.Then I tried to play every video and audio format I have and noted down all links for all those items.

The items were gstreamer ffmpeg,plugin bad,ugly and fluendo AND ALL THEIR DEPENDENCIES WHICH WERE SO MANY IN NUMBERS! I manually downloaded everything and it took a lot of time (there were about 30-40 or more different links,though most of them were in kb's.The only big files were a freepats file(28 mb) and a file name libflite(14 mb).Then it took another half an hour to install them one by one.

But atleast the problem is solved now:guitar:

---

### Post by darkhelmetchris on 2010-10-30
> **dhiman33 said:**
> I manually downloaded everything and it took a lot of time (there were about 30-40 or more different links,though most of them were in kb's.The only big files were a freepats file(28 mb) and a file name libflite(14 mb).Then it took another half an hour to install them one by one.

Great that you go it worked out.  If it helps you in future, there is an easier way to get them installed.  Once you have all the .deb files (either by sisco311's cool method, or by copying them from the cache, you can run the following command against the folder of .deb's to install them all at once:
```
sudo dpkg -i *.deb
```
and that will install all of them in one shot.

---

### Post by dhiman33 on 2010-10-31
That idea was so cool!=D>I bet it will save me lots of time in the future.Thank you very much.:KS

---

