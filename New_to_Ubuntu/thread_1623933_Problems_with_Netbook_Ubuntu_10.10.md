---
title: "Problems with Netbook Ubuntu 10.10"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by ian19jam on 2010-11-17
I successfully downloaded recently the Netbook Ubuntu 10.10 version onto my Asus Eee E5380 machine.

However I am having difficulty in downloading all my document files from my main computer, which is also Ubuntu 10.10. I connected my external hard drive LACIE to the Netbook, which works when I use the files directly from that source. However I cannot seem to transfer the Document files into the Netbook Document file. I tried dragging and send to but nothing works. Please advise and in simple terms please. Thanks

---

### Post by cariboo on 2010-11-18
Try running nautilus as root, to access your files. Alt-F2 isn't enable in Unity yet, so you have to open a terminal and enter:

```
sudo nautilus
```

Once the file manager has opened you should be able to transfer files from your external drive.

It may be easier to do this from the gnome-desktop, you can select it from the login screen.

---

