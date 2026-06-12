---
title: "Wireless Help"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Hasmarth on 2008-07-24
Ok here's my story, i got ubuntu running on a laptop that was given to me by a friend. I always wanted to try linux, but didn't want to sacrifice my gaming rig for it. My problem is, ubuntu on the laptop won't recognize my wireless network.

The laptop is a Dell Inspiron 5100, with (i believe) a Broadcom BCM4306. I know how to run terminal and can supply copy paste/screenshot info from it. Any info would be awesome. I've been trying to troubleshoot through all of this but all the ubuntu info seems like an alien language to me. thanks for the help.

P.S. I think it might be a driver issue, but i have *no idea* how that works. Again, any help would be awesome.

---

### Post by eeeumpc on 2008-07-24
you will probably need to install ndiswrapper since ubuntu doesnt have native drivers for broadcom cards. ndiswrapper allows you to load windows drivers to make the card work under  linux. next you will need to obtain the .inf and .sys files of the windows drivers.

---

### Post by Hasmarth on 2008-07-24
where can i find ndiswrapper and the drivers?

---

### Post by superprash2003 on 2008-07-25
Hope this helps [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Kevbert on 2008-07-25
You need to check what version of BCM4306 you're using by going to Accessories terminal and typing in 
```
lspci
```  the card will be listed towards the end.
Please check out this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560").
If you have any questions please ask.

---

### Post by Hasmarth on 2008-07-25
ok well i read through the Fiesty no Fluff thing, and it looks like i didn't have ndiswrapper set as the module. So i followed [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix) that and this was the result:
[IMG]http://i47.photobucket.com/albums/f174/sockkid123/screenshotndiswrapper.png[/IMG]

Again, any help would be great. I don't think this is supposed to happen, and in lshw -C network, it still appears as "module=ssb"

---

### Post by Kevbert on 2008-07-25
b43 is a firmware driver that resides in /lib/firmware and possibly in its' own directory.  In this directory you will find a number of files ending in .fw   If you follow the guide in my previous post it will install and configure these.

---

### Post by Hasmarth on 2008-07-25
but what about the whole "ndiswrapper" thing? i don't think i even have that. I follow the guide to step three, and it says "sudo: ndiswrapper: command not found." Whats the deal with that?

---

### Post by Kevbert on 2008-07-25
You should have got ndiswrapper-utils in step 1.

---

### Post by Hasmarth on 2008-07-25
o geez, i feel like an idiot >.< i must have overlooked that. Really sorry about that
Hmmm, i doubt this is supposed to happen:
[IMG]http://i47.photobucket.com/albums/f174/sockkid123/Screenshot-taylortaylor-laptop.png[/IMG]

Also, thanks alot Kevbert, you've been a really great help.

---

### Post by Kevbert on 2008-07-26
You may need to edit your software sources.  Go to System-Admin-Software Sources.  Maker sure the 4 boxes are ticked under the Ubuntu Software tab and  Important, Recommended and Unsupported boxes are ticked under the Updates tab.  This should resolve the first error.
The second error is that you've left out the space between make directory and the home symbol so the line should read
```
mkdir ~/bcm43xx
```

---

