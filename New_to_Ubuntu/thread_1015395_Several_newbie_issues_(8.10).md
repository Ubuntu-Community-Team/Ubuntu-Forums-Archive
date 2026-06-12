---
title: "Several newbie issues (8.10)"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Geimhre on 2008-12-18
Neither Flash nor Gnash seem to work. I can't get rid of Flash 9, and it screws up my system. When I enable it, just the presence of a youtube video on a page will devour my memory and force me to close out, and playing them is impossible. Flash 10 doesn't seem to do anything at all.

Thanks in advance

---

### Post by GrantsV on 2008-12-18
Re: the Nvidia.

You need to go over to nvnews.net, visit the linux forum, and download latest driver Beta OPENGL3 180.11.02.

Shutdown your XServer and run the .sh file with:
sudo sh (driver file name).

Reboot, or restart X.

Once you have the latest drivers installed, go into your Appearance menu, visual effects, and turn Compiz on with "Normal" or "Extra" settings.  Your desktop will be like light speed.  But without the latest drivers, forget it good 2d performance.  NVidia 8 series has had major problems up until this driver release.  After a year torture with slow desktop, thanks to the new drivers my PC is super fast like a fresh Windows install.

Good luck!

---

### Post by Geimhre on 2008-12-18
Thanks V

Bump

---

### Post by Kareeser on 2008-12-18
#2: Are you using firefox? Please copy and paste the output to the flash driver in use by Firefox. Open it up, and type ```
about:plugins
``` into the address bar. Find the offending driver, and let's take a look together :)

---

### Post by Geimhre on 2008-12-19
```
Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes
```

---

### Post by hyper_ch on 2008-12-19
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Kareeser on 2008-12-19
Thanks Geimhre...

Do me a favour now:
1. Open firefox
2. Type "about:config", and say that you'll be careful :)
3. Navigate to "plugin.expose_full_path" and set that value to true.
4. Type "about:plugins", and tell me the path of the output again.

I've had this problem before (or a similar one). Downloading a new plugin file should fix the problem.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Download, untar, and copy libswfdecmozilla.so from the extracted folder to the folder that the firefox output declared.

Restart firefox, and the problem should go away.

r999... revision 999. That scares me. I'm on 15.

---

### Post by Geimhre on 2008-12-27
/home/geimhre/.mozilla/plugins/libflashplayer.so

no such folder seems to exist when I go to Home, though

---

