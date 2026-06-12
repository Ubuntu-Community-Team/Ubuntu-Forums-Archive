---
title: "Any help getting my wireless adapter to work?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by kr0me on 2007-03-20
Hey guys,

I have always wanted to try out Linux, after hearing so many good reports for it, and last night I finally got around to burning myself an Ubuntu disk and booting from it.

All went well, but I was unable to connect to the internet. Using windows, I was always able to do this by connecting to my home's wireless network, using a USB adapter. The make/model of this adapter is "US Robotics 802.11g Wireless USB Adapter".

Windows always let me use this straight out of the box, however Ubuntu did not. When I went onto the options for it, it failed to even recognize that it was plugged in . . . I think.

This is my question - is there anywhere I should look, or anything I should do, that will help me get onto the internet using Ubuntu? Or is it a lost cause?

Thanks in advance for your help,

kr0me

---

### Post by kr0me on 2007-03-21
Update/Bump:

Btw I forgot to mention, I do have the original disk that came with the adapter. Is there a way I can use this to help me get it to work?

Thanks,

kr0me

---

### Post by kr0me on 2007-03-23
I'll try one more bump, then I'll just forget it - I promise :p

Sorry to be a bother, I just really had great expectations from Ubuntu - and as an OS it is great, but I **need** to be able to access the internet in order for it to be an acceptable solution for me.

Thanks,

kr0me

---

### Post by spd106 on 2007-03-23
According to this [list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")  that's pointed to in one of the networking forum stickies, you will probably need ndiswrapper.
Try a forum search for ndiswrapper there are many threads on it already, maybe also try this wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You will need the windows driver.

---

### Post by Jouke74 on 2007-03-23
And you can use this post as a general framework to get it working. Note that you need to change the Asus windows driver into the one of your your own wireless card (INF and SYS files). For 32 bits Ubuntu, use a windows 32 bits driver, for 64 bits Ubuntu use a windows 64bits driver.

The install of software etc remains the same.

[http://www.ubuntuforums.org/showthread.php?t=391416]("http://www.ubuntuforums.org/showthread.php?t=391416")

---

### Post by tomiu on 2007-05-16
> **kr0me said:**
> I'll try one more bump, then I'll just forget it - I promise :p

Sorry to be a bother, I just really had great expectations from Ubuntu - and as an OS it is great, but I **need** to be able to access the internet in order for it to be an acceptable solution for me.

Thanks,

kr0me

what happened??? can u access the internet in ubuntu??

---

