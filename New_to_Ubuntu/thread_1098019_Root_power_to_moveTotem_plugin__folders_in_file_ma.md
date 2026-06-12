---
title: "Root power to moveTotem plugin  folders in file manager system"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Martynwills on 2009-03-16
I am trying to install a youtube H264 plug-in for Totem

source here:
 [http://www.soccio.it/michelinux/2008/03/29/h264-youtube-video-in-totem/en/](http://www.soccio.it/michelinux/2008/03/29/h264-youtube-video-in-totem/en/)

Following the path

/usr/lib/totem/plugins 

I have reached the place to put the new plug-in but when I try to drag and drop it into Totem plugin folder it says I do not have permission as i&#7743; not the root user.

I know I can use sudo in the terminal to give myself root powers at the command line but how do I borrow root powers if I want to drag and drop in the nautilus file manager system?

---

### Post by taurus on 2009-03-16
You use gksudo nautilus.

```
gksudo nautilus
```

---

### Post by Martynwills on 2009-03-16
sorry but where when then what????

---

### Post by Martynwills on 2009-03-16
Apologies Taurus. I actually got off my **** and just tried what you said and discovered it gave me root powers and opened up nautilus. 

Many thanks. 

Newbie out.;)

---

### Post by philinux on 2009-03-16
> **Martynwills said:**
> I am trying to install a youtube H264 plug-in for Totem


I know I can use sudo in the terminal to give myself root powers at the command line but how do I borrow root powers if I want to drag and drop in the nautilus file manager system?

Use the terminal.

I'm not sure you need this though.

---

### Post by Martynwills on 2009-03-16
Cheers for the reply Phil. I may not need it, but I needed the lesson on gksudo anyway. So I got something out of it :)

---

