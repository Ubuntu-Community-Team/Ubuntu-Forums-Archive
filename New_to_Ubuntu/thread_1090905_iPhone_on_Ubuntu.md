---
title: "iPhone on Ubuntu"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-03-08
I was wondering if I could use my iPhone in Ubuntu, putting tunes on it, etc. I have Amarok, can I use that to put music on it? Also when I plug it it with the typical USB cable the only thing that happens is my iPhone charges and I am asked if I want to import photos. How do I configure it to recognize my iPhone if I can?   Thanks

---

### Post by Nxion on 2009-03-10
Currently, if your iPhone is unlocked, then it will sync. From what I understand that is the only way to do at this point and time. Here is some documentation for more information.
[URL="https://help.ubuntu.com/community/PortableDevices/iPhone"]
https://help.ubuntu.com/community/PortableDevices/iPhone[/URL]

---

### Post by stchman on 2009-03-10
Gotta love Apple and their proprietary BS.

Apple folks bash M$ when Apple is no better about it.  They take a free OS (FreeBSD) and hack it to suit their needs to create OS X.

---

### Post by clive littlewood on 2009-03-10
Hi

Currently you will need itunes to sync and transfer files to both the iphone and ipod touch.    :(

Even a "jailbroken" pod still needs itunes for transfer and updates.


Clive

---

### Post by darkvad0r on 2009-03-11
Wow, have any of you tried a google search (or even a forum search for that matter) before replying to the original poster ?

I don't think so, cause if you had, you'd have found out that it is indeed possible to sync your iPhone/iPod touch with ubuntu (wirelessly).

Here's an older thread discussing such possibility:
[http://ubuntuforums.org/showthread.php?p=6876703](http://ubuntuforums.org/showthread.php?p=6876703)

And here's the ubuntu wiki page explaining how to do it:
[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

Cheers

---

### Post by Nxion on 2009-03-11
> **Nxion said:**
> Currently, if your iPhone is unlocked, then it will sync. From what I understand that is the only way to do at this point and time. Here is some documentation for more information.
[URL="https://help.ubuntu.com/community/PortableDevices/iPhone"]
https://help.ubuntu.com/community/PortableDevices/iPhone[/URL]

> **darkvad0r said:**
> Wow, have any of you tried a google search (or even a forum search for that matter) before replying to the original poster ?

I don't think so, cause if you had, you'd have found out that it is indeed possible to sync your iPhone/iPod touch with ubuntu (wirelessly).

Here's an older thread discussing such possibility:
[http://ubuntuforums.org/showthread.php?p=6876703](http://ubuntuforums.org/showthread.php?p=6876703)

And here's the ubuntu wiki page explaining how to do it:
[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

Cheers

Actually I did do some google searches and I found a guide in the Ubuntu Docs. If you look at my post, it is the same guide as you you have suggested.

---

### Post by darkvad0r on 2009-03-12
> Actually I did do some google searches and I found a guide in the Ubuntu Docs. If you look at my post, it is the same guide as you you have suggested.

Yeah, I know, I was talking about the 2 other guys that came after you spreading nonsense because when you search for "iphone" in the forums, this post is one of the first results and from reading it, you could get the impression that it was impossible to sync the iphone with ubuntu.

---

### Post by clive littlewood on 2009-03-12
Hi

As 1 of the "guys spreading nonesense" and an owner of the "latest" ipod touch can i INFORM you that the latest ie. the ipod that the OP would buy will NOT work from the attached howto's and none of the ipods will be able to be updated to the latest apple firmware using this method.

Regards

Clive



PS. It can be an expensive mistake taking advice from so called experts.

---

### Post by darkvad0r on 2009-03-12
> **clive littlewood said:**
> Hi

As 1 of the "guys spreading nonesense" and an owner of the "latest" ipod touch can i INFORM you that the latest ie. the ipod that the OP would buy will NOT work from the attached howto's and none of the ipods will be able to be updated to the latest apple firmware using this method.

Regards

Clive



PS. It can be an expensive mistake taking advice from so called experts.
I'm sorry that you took that personal, I didn't mean to start a flamewar, so let's just stick to the facts and try to help the original poster.

This is what I called "nonsense":
> Currently you will need itunes to sync and transfer files to both the iphone and ipod touch
It's just not true, I own an iPhone 3g and I sync my podcasts on mac with iTunes and my music on ubuntu with gtkpod. You say you own the latest iPod touch but the OP was asking about the iPhone, so why state that **both** the iPhone and iPod touch need iTunes ?
> Even a "jailbroken" pod still needs itunes for transfer and updates.
Ok, this is half-true, but only because of the "updates" part of it. No need for iTunes to sync photos and music.

So now that we have cleared that out, maybe we can help you with your iPod touch, maybe you missed a step in the process ? And notice that I didn't imply anywhere that I am an "expert", I'm just posting here because I know it can be done.

---

### Post by turbo2125 on 2009-03-13
Im still very new to linux, switched because of constant problems with xp on my computer, i have the iphone 3G, and was very worried about iTunes not working in ubuntu. Not being a fan of dual boot, i started to do some research, and found that if you do not want to unlock/jailbreak your iphone, and do not want to dual boot, then a very good option is using VirtualBox v2.1.4 to run a windows or mac guest. I personally use xp in VB, and after a little troubleshooting i found that all it takes once VB is set up with your OS and you have installed itunes (i installed the latest version as of 11 Mar 2009) it was very simple to set up the USB support, and found that my only issue was having to disconnect and reconnect my iphone a few times before my guest os finally recognized it as an iphone, and not as a camera(which is what 8.10 saw it as by default for me) after getting that to work, i can backup, sync, restore, and update my firmware in the guest os, without any issues at all. For me personally, this was my preferred solution, and i just thought i would offer it incase there is anyone else like me that doesnt want the hassel of trying itunes through wine, jailbreaking, or dual booting.

---

### Post by nwadams on 2009-03-13
so you can sync a non-jailbroken iphone or ipod touch(2nd gen) with ubuntu???

I was under the assumption that the only solution was to use itunes. By the way i have a windows xp install in a virtual box that I use to sync my ipod touch. It works great now. I had to patch my kernel to allow for the usb device to get passed to xp through virtual box but it was fairly simple. There's a guide on the internet that I have on my other computer that ill link to if anyone wants.

---

### Post by LowSky on 2009-03-13
As far as I know Ubuntu and the iPhone don't mix well and the iPhone needs iTunes for the most part. prove to me it doesn't if you like but i'm just going off all the info I've seen on this website. VMing Windows to use your iPhone is a decent way for full support if you need it.

Personally I'm not a fan of the iPhone, after owning an iPod and it having more issues than Time Magazine (newest issue is it stoped playing all forms of video, just lovely). I don't support the Apple culture in it planned extinction of its devices or locking me into a phone company. Maybe that why I like Blackberry's. As every major carrier sells them and while it may not be completly compatable with Linux, it works doing most things. Oh and I can change the battery myself...giant plus...lol

---

