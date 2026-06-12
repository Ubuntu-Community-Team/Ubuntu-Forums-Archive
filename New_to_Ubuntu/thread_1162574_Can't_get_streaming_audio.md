---
title: "Can't get streaming audio"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by gshockxc on 2009-05-17
I have a favorite radio station that I like to listen to online, but I can't get streaming audio.  Or, at least, I don't know how.  I go to the website, it loads fine, click on the link, the player window opens, click Play, but nothing happens.  Any suggestions?  I'm Jaunty, Firefox 3.01.

Thanks.

---

### Post by Terry of Astoria on 2009-05-17
Is it a html page, the player window?
try media player connectivity - a plugin for Firefox. Look in the Tools-Addons menu and search for it. I like the way it "subverts" various players and is able to get me a link I can use to play with vlc or mplayer.
Let me say vlc is a great streaming media player. 
   More information like what stream are you trying to decode, perhaps? . . . In other words, the web address?
Have you installed the ubuntu-restricted-extras package (intrepid)?

---

### Post by gshockxc on 2009-05-17
Turns out I'm just a knucklehead and didn't read far enough.  I have to install a special player, which I found and followed the link, but I don't quite understand all the instructions.

Here's the link to the download and install instructs.  
[http://www.linux-sxs.org/multimedia/mplayermozplug.html](http://www.linux-sxs.org/multimedia/mplayermozplug.html)

If you can help, thanks.

---

### Post by Terry of Astoria on 2009-05-18
OK, what I would do is install that mplayer plugin from the repositories. Just a sec . . Look here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
And here is the command to install the mplayer plugin:
```
sudo apt-get install mplayer mozilla-mplayer
```
This is assuming that you have enabled the repository where the mplayer package is located.
Read the link I sent above for how to enable the repository, otherwise known as a software source.

---

