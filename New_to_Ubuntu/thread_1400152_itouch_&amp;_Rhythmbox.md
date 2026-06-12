---
title: "itouch &amp; Rhythmbox"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by celticbhoy on 2010-02-06
I was asked by my nephew to get his new itouch to work on his Karmic install. Everything shows up fine by mounting the device using ifuse, and it shows up fine in Rhythmbox. The problem is when I try to copy any tracks to it. The progress meter runs and shows it transfering, but the song doesn't show on the itouch. I think that this is a format problem (the tracks are mp3's). What format should they be, and how do I convert them?

---

### Post by ubudog on 2010-02-06
MP3's should work. Open the Music folder or wherever the music that you want to put on the itouch is located.  Highlight them all, right click, select copy.  Go to the itouch's music folder.  Right click, select paste.  It should work.

---

### Post by celticbhoy on 2010-02-06
> **ubudog said:**
> MP3's should work. Open the Music folder or wherever the music that you want to put on the itouch is located.  Highlight them all, right click, select copy.  Go to the itouch's music folder.  Right click, select paste.  It should work.

Do I ignore all the 'F' folders located in the itouches music directory?

---

### Post by ubudog on 2010-02-06
I guess.  Try ignoring it.

---

### Post by baddog144 on 2010-02-06
The problem lies in how Apple does the iTunesDB. As far as I know, there is no way to get iPod Touches to sync on Linux, after iPhone OS 2.0 (or thereabouts). You'll have to resort to Windows for this one, I think :(

---

### Post by Linux000 on 2010-02-06
I just got my iPod touch to work using 9.10, you have to use "gtk iPod manager" I couldn't make rythmbox work.

---

### Post by s.fox on 2010-02-06
Hello,

From [this]("https://help.ubuntu.com/community/PortableDevices/iPod") page on the community docs wiki:

> Ubuntu works very well with iPods, except the iPod Touch, iPhone, and any other future generation Apple portable devices that do not show up as a generic storage device. To sync with these new-generation devices, you must perform an unsupported [Jailbreak]("https://help.ubuntu.com/community/PortableDevices/iPhone") operation to gain SSH access to the device (the iPhone) over wifi. 


-Silver Fox

---

### Post by Linux000 on 2010-02-06
Yep, thats it.

---

