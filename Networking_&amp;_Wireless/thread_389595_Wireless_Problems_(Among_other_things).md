---
title: "Wireless Problems (Among other things)"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by UberSoldAt666 on 2007-03-20
First off I am completely new to this. I've used windows my whole like and am definitely an advanced user, but I have always wanted to try out linux so I am.

Anyways, I don't even know where to start. I am simply trying to install my WUSB11v4. 

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

That's the tutorial I'm following, but when I get to the point where you type make whatever it just says command not found? I'm dying here, help would be great!

---

### Post by Floppyjoe on 2007-03-21
> **UberSoldAt666 said:**
> First off I am completely new to this. I've used windows my whole like and am definitely an advanced user, but I have always wanted to try out linux so I am.

Anyways, I don't even know where to start. I am simply trying to install my WUSB11v4. 

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

That's the tutorial I'm following, but when I get to the point where you type make whatever it just says command not found? I'm dying here, help would be great!

You may need to do the following commands first:
```
sudo apt-get install build-essential
```
and
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by pollywog on 2007-03-22
Hey, I had the same problem. I couldn't get it up and running using any of the procedures that I found, but after much trail and error I got working. I listed the entire procedure on:

[http://www.ubuntuforums.org/showthread.php?p=2338149#post2338149](http://www.ubuntuforums.org/showthread.php?p=2338149#post2338149)

Persistance pays-Good Luck- P.W.

---

