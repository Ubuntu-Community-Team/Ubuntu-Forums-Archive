---
title: "online videos on Firefox"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by ash2525 on 2009-02-23
Hi i just installed ubuntu and i can not watch videos from vh1 on Firefox it just loads and does not do anything. But i can watch videos from youtube how can i fix this problem? I have the latest flash and stuff i think and it does not ask me to install a plugin. Does this have to do with ubuntu and can anyone help me?

Also try to watch some videos just to see if it works.

---

### Post by gandaran on 2009-02-23
post the link so we can try it!

---

### Post by ash2525 on 2009-02-23
here is a link to a video =. 

[http://www.vh1.com/video/play.jhtml?id=1604307&vid=56979](http://www.vh1.com/video/play.jhtml?id=1604307&vid=56979)

---

### Post by simeon87 on 2009-02-23
For me, it says they're not allowed to play the video outside the United States due to copyrights. Are you outside the U.S. but you're simply not seeing this message?

---

### Post by ash2525 on 2009-02-23
i am in the us

---

### Post by gandaran on 2009-02-23
> **ash2525 said:**
> here is a link to a video =. 

[http://www.vh1.com/video/play.jhtml?id=1604307&vid=56979](http://www.vh1.com/video/play.jhtml?id=1604307&vid=56979)
this is flash video but it only works for USA residents, if you are in USA and youtube works then this should also work for you.
which flash plugin have you installed? adobe, swfdec or gnash?

---

### Post by redseventyseven on 2009-02-23
I got the message too (obvs!) but it appears that that message is a "video" itself, so it would indicate that the video is working fine.

Open a terminal and run firefox from the terminal (the command is simply "firefox") - leave the terminal window open and try to play the video.

Paste any messages that appear in the terminal *from the time that you open the page with the video on it onwards*.

---

### Post by gandaran on 2009-02-23
right click that flash video window, does it say adobe flash player 10 or something else?

---

### Post by ash2525 on 2009-02-23
I just installed the latest flash. I did not know i had 9 installed! And i wouldent of known if it was not for  you gandaran. So Thank you!

Sorry to take up forum space.

---

### Post by Bölvaður on 2009-02-23
we are here all to learn to be more aware of our own actions ^^

---

### Post by QCompson on 2009-03-05
I have the same problem... but it is even more frustrating.  Sometimes it will work fine, sometimes not at all (just the grey box of doom).  I can often play one video, and then half an hour later, nothing on the VH1 site will play.  Really annoying.  

Flash 10 here.  64 bit intrepid.  Youtube and hulu both work flawlessly.

---

### Post by CRIMPS on 2009-03-05
Wow, Firefox closes without error, warning when I open that link.  This is probably related to my other post [here]("http://ubuntuforums.org/showthread.php?t=1088141")

Again, I opened firefox from the terminal hoping I would receive some type of error messages.  No luck unfortunately. :(  

I went to [http://www.javatester.org/version.html]("http://www.javatester.org/version.html") to find the exact version of Java I have installed.  
```
Java Version 1.6.0_07 from Sun Microsystems Inc.
```

Maybe I need to upgrade?

---

### Post by QCompson on 2009-03-15
Just to let anyone know who is having a similar problem on x64 systems.  I discovered my problem was that not only did I have the x64 flash 10 plugin in my plugin folder (~/.mozilla/plugins), but at some point I had installed the flashplugin-nonfree package as well.

Uninstalling the flashplugin-nonfree package has allowed me to continue watching "Rock of Love Bus" episodes without difficulty.  Whether that is a good or bad thing I'm not sure.

:D

---

