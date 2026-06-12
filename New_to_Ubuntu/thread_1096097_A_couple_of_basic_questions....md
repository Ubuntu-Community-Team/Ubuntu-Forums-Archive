---
title: "A couple of basic questions..."
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Common88 on 2009-03-14
These queries are more "what is the best way to do this?"... I couldn't find much advice elsewhere.

So, firstly, I have Vista & Ubuntu dual booted, I have about 20 gigs of music on my Vista installation so how can I access this Ubuntu? Or what is the best way to do it? I dont really wanna have all 20 gigs on each OS because thats a waste of space...

Secondly, I used ubuntu years ago and i remember a program called "wine" where I could run windows programs, i'd like to run the proper windows version of skype so i can send sms etc. - does wine support this well enough or is there a better way to do this these days?

Thanks very much for any help!

---

### Post by ugm6hr on 2009-03-14
Install [ntfs-3g]("apt:ntfs-3g") and [ntfs-config]("apt:ntfs-config") to read & write to your Vista drive, and mount automatically.  That will allow you access to all the files (inc media) there.  You just have to configure it from the menu (it appears somewhere in Applications->System Tools after a reboot).

As for skype with wine - I don't know.

---

### Post by sleepyjon on 2009-03-14
Skype & ubuntu:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

