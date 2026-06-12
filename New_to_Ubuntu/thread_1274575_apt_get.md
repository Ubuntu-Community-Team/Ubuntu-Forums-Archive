---
title: "apt get"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by spiky001 on 2009-09-24
hi how do i use apt get  in terminal, & can i use it to get Nautilus. I use ubuntu 9.04

---

### Post by scorp123 on 2009-09-24
> **spiky001 said:**
>  i how do i use apt get  in terminal Read the manual please: ```
man apt-get
``` (Use the cursor keys to navigate; press Q to quit).

But please: If you're too new to this then I'd recommend you stick to the GUI stuff for now, e.g. Synaptic which is very easy to use (and is a graphical front-end to "apt").

> **spiky001 said:**
>  & can i use it to get Nautilus. I use ubuntu 9.04 If you use Ubuntu 9.04 then you already have Nautilus ... Nautilus is the file manager. The thing that opens when you go ***Places > Home Folder***

... your question makes little sense I'm afraid.

---

### Post by QIII on 2009-09-24
You should already have Nautilus.  It's your generic "file browser" that comes with Ubuntu, similar to Explorer in Windows.

As for apt-get, give this a read through...

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

The pdf is free to download.

---

### Post by spiky001 on 2009-09-24
i did find that the file manager woz called nautilus just after i posted sorry my mistake

---

### Post by scorp123 on 2009-09-24
> **spiky001 said:**
> i did find that the file manager woz called nautilus just after i posted sorry my mistake There are a few extra pacakages that you might be interested in ...

[LIST]
[*]nautilus-wallpaper
[*]nautilus-open-terminal
[*]nautilus-image-converter
[*]nautilus-filename-repairer
[/LIST]

If you want to find out what these extra packages are good for you could either use the terminal (apt-cache show nameOfpackage) or Synaptic :D

You have to logout + login again to make any of those packages active after installation (if you stay logged in you won't notice any change).

---

