---
title: "Why can I not play youtube videos properly?"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-16
Videos skip
sound in the videos skip
Firefox usually stops being responsive while watching videos

I enabled NVidia graphics card propriety drivers already.. Upgraded to version 180 a week ago. Still can't watch videos properly.

Please advise. Thank you!

---

### Post by juancarlospaco on 2009-04-16
Install all updates, there's updates for Flash Plugin

---

### Post by jbrown96 on 2009-04-16
Are you running the 64-bit version? If so, check out [this page]("http://labs.adobe.com/downloads/flashplayer10.html") for a 64-bit flash from Adobe. It's much faster. It's easy to install; remove flash player from Synaptic, then extract the archive and then move libflashplayer.so into /home/$USER/.mozilla/plugins (create the plugins folder if you don't have it).

You can check to see if you are running 64-bit with the following command ```
uname -a
``` x86_64 is 64-bit

---

### Post by LesterPalooza on 2009-04-16
This is my ouput for uname -a

```
Linux lester-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

```

> juancarlospaco  	
Re: Why can I not play youtube videos properly?
Install all updates, there's updates for Flash Plugin 

means I am not running 64 bit right? Ill try installing all updates that I can find.

---

### Post by jbrown96 on 2009-04-16
Flash is very resource intensive, and it's not off-loaded to your GPU. Run ```
top
``` in a terminal when the video is playing.

---

### Post by juancarlospaco on 2009-04-16
Increase Flash-Cache, right click when playing, Cache tab.

---

### Post by LesterPalooza on 2009-04-17
How will I find the right updates in Synaptics Package Manager? I just want to install the needed packages, but I don't know which ones are needed. :D

---

### Post by jbrown96 on 2009-04-17
The updates will automatically be flagged. You will get a notification in the top right, or if you want to check manually, it's easier to use the update manager (System--->Admin).

---

