---
title: "Flash Issues w/ Firefox"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Rainman5419 on 2009-11-08
I'm a complete Ubuntu noob here, so I hope I've posted this in the correct forum/sub-forum.

I'm running Ubuntu9.10, 64-bit and am having problems getting flash to work correctly. Specifically, whenever firefox loads flash content(Youtube, Hulu, etc) the browser just crashes.

I've downloaded the latest version of the plug-in from Adobe [here]("http://labs.adobe.com/downloads/flashplayer10.html") and moved it to
/home/<username>/.mozilla/plugins to no avail. The worst part is that I had flash partially functioning previously(objects loaded, but couldn't be interacted with) and after trying to fix that problem I seem to have made it worse.

---

### Post by luvgirl12345 on 2009-11-08
i would advice you to use 32bit system... its way easier and has less glitches.

---

### Post by wojox on 2009-11-08
Try:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Unpack it:

```
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Move it:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by Rainman5419 on 2009-11-08
Following Wojox's advice gets me back to a semi-functioning flash, but I can't interact with anything. I can use spacebar to pause a video, but that's about it.

---

### Post by wojox on 2009-11-08
You may have some conflicts, use this and scroll down to Flash [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Zsola on 2009-11-08
I too had problems with flash, but after some tinkering, and of course made it worse :) what i did removed all the flash from my comp... disabled from in firefox, and removed from synaptic.

After that installed the adobe-flashplugin - also from synaptic,and that did repair all my flash content :)

i would suggest the flash player from macromedia - as did wojox - , but as you said that didnt worked either...

---

### Post by Rainman5419 on 2009-11-08
Following what Wojox said again, I THINK that fixed my problem. Now I'm off, hopefully to stumble my way through my linux noobishness.

Thanks for the quick replies and help.

Edit: Ok, it works but seems temperamental. Youtube is working fine but Hulu for example is not, haven't tested anything else yet.

---

### Post by anewguy on 2009-11-08
Having the same problems - 64bit and flash not even being recognized.  Tried what is suggested here but got this error:

dave@dave-desktop:~$ wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
--2009-11-08 16:22:18--  [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
Resolving download.macromedia.com... 69.192.147.191
Connecting to download.macromedia.com|69.192.147.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3727613 (3.6M) [application/x-gzip]
Saving to: `libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.1'

100%[======================================>] 3,727,613   4.87K/s   in 13m 50s 

2009-11-08 16:36:17 (4.38 KB/s) - `libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.1' saved [3727613/3727613]

dave@dave-desktop:~$ tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
libflashplayer.so

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dave@dave-desktop:~$ 

EDIT:  MY BOO-BOO!!  Had to restart download and didn't notice it had saved with .1 because I didn't delete the original download.

EDIT-EDIT:  Even after getting these procedures to work, I still have no flash.  Youtube comes up and says I either have Java script disabled or need a flash player - the one it links to is only the 32-bit one and will not install on my system.


thanks for any help!

dave :)

---

