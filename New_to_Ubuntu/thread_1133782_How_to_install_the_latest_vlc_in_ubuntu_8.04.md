---
title: "How to install the latest vlc in ubuntu 8.04"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by kramer65 on 2009-04-23
Hello,

I want to keep ubuntu 8.04 because of its stability. However, I do want to get the latest vlc player. How am I able to do that?

Thanks in advance!

---

### Post by s.fox on 2009-04-23
Hi

Run this in terminal:

```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

Hope this helps

-Ash R

---

### Post by kramer65 on 2009-04-23
Thanks. I removed vlc (via Programs > add/remove..) and ran your command, but when I open vlc again it still says it is version 0.8.6e (under help > about).

Any other ideas..?

---

### Post by snowpine on 2009-04-23
According to the VLC website itself, Ash's directions are correct, and you are running the appropriate version for Ubuntu Hardy Heron.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by kramer65 on 2009-04-23
Yeah I know. But I want to run the latest version since I am not able to run subtitles in this version and I cannot control the buttons when I am in fullscreen mode. I thought I could just download a deb with the latest version... but it seems to be not so easy...:(

---

### Post by snowpine on 2009-04-23
> **kramer65 said:**
> I want to keep ubuntu 8.04 because of its stability. 

Understand that if you start installing applications not designed for 8.04, you will lose that stability. VLC depends on various audio and video libraries and packages; my guess is that 8.04 cannot satisfy these dependencies, and therefore the developers have chosen not to backport VLC.

---

### Post by LowSky on 2009-04-23
here is the source code, you will need to uninstall VLC from Synaptic first. Beware this method as it will not update itself, and may not creat icons for the menu,
[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

instructions to install
[http://wiki.videolan.org/UnixCompile](http://wiki.videolan.org/UnixCompile)

use the debian notes, as some unix commands will not work
[http://wiki.videolan.org/UnixCompile#Debian](http://wiki.videolan.org/UnixCompile#Debian)

---

