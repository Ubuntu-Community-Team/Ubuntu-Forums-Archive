---
title: "grsync backups over network."
date: 2011-07-26
forum: New to Ubuntu
---

### Post by sherfie on 2011-07-26
hello, ive been working on setting up a server for the past week now and i always get stuck on the same thing. i want my server to do automatic back ups for my laptop (running windows 7), and every time i try to set up the destination folder it doesnt see my network folder. 
i know i have my network set up right because when i go to find the network outside of any backup program i can find the folder just fine and read/write on the laptop from the server. 
i have been trying relentlessly to find a how to on the internet but nothing seems to work. any help is greatly appreciated!

---

### Post by androssofer on 2011-07-26
could it be ur backup program doesnt hav permissions to view the network folder?

---

### Post by Ghost_Mazal on 2011-07-26
So the share is on the Ubuntu server and your backups run from laptop (with Win 7) to the Ubuntu server share if I understand it correct.

Why don't you simply do a drive mapping in Win 7 to your share and mark "automatically connect when Windows starts"
This way your share will have a drive letter everytime Windows boots up and will make your life much easier.

If you work the other way around then ditto. Create a mount point for your share in fstab. many programs in Ubuntu can't browse to the network , but can browse to a mount point.
This is an example line in /etc/fstab that will mount a share every time your Ubuntu boots

```
//serverip/sharename /mnt/public cifs username=username_of_share,password=password_of_share 0 0
```

Replace all relevant info with your info. However this does pose a security risk as fstab is stored in plain text. But if you are sure you alone have access to your server then it's not an issue

---

