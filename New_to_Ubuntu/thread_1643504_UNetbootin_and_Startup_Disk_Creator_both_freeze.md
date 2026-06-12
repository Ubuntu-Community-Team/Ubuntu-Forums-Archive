---
title: "UNetbootin and Startup Disk Creator both freeze"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-12-12
Hello Ubuntu Forums Community,

I'm trying to get my live USB to work as it did yesterday. I've been experimenting with OSes and was trying to install mint through startup disk creator. When I select 'Erase Disk', I get an error saying:

"org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

When I try to install it through Unetbootin, It gets stuck at step 2 (I have the ISO so skipped step 1). This also happens when I try to install ubuntu 10.10 and 8.04.

Any help would be appreciated.
Thanks in advance.

---

### Post by wilee-nilee on 2010-12-12
Just right click on the thumb icon-format choose the fat option then install to it.

---

### Post by amjjawad on 2010-12-12
> **kroq-gar78 said:**
> Hello Ubuntu Forums Community,

I'm trying to get my live USB to work as it did yesterday. I've been experimenting with OSes and was trying to install mint through startup disk creator. When I select 'Erase Disk', I get an error saying:

"org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

When I try to install it through Unetbootin, It gets stuck at step 2 (I have the ISO so skipped step 1). This also happens when I try to install ubuntu 10.10 and 8.04.

Any help would be appreciated.
Thanks in advance.

If you want to create a new LiveUSB, then format your USB then try to create a liveUSB again.

---

### Post by kroq-gar78 on 2010-12-12
I've done that and now Startup disk creator freezes. I've restarted my computer, and same result.
Any ideas?

---

### Post by uRock on 2010-12-12
Does your thumb drive have U3 or any other software on it? I had to remove U3 from my Sandisk thumb drive before Startup Disk Creator would work.

---

### Post by kroq-gar78 on 2010-12-12
It's a Lexar with one of those usage meters. and I've erased it many times before (but not formatted through GParted or the other method suggested in this thread). It didn't have any software, ad I can copy file perfectly. Why would the startup disk creator and Unetbootin both not work on this flash drive? I don't have any othre flash drives that I can test on right now, so does anybody think they know why this is happening?

---

### Post by uRock on 2010-12-12
If the usage meter is software based, then it probably has to be removed.

---

### Post by kroq-gar78 on 2010-12-12
sorry, I meant a usage meter on the outside. It works all the time

---

### Post by noonsie on 2011-03-29
I know this is an old thread, but I just wanted to add that the "create startup disk" utility will not work with flash or pen drives that use file compression software, I learned this the hard way...thx :)

---

### Post by GeoffreyBernardo on 2011-08-13
> **noonsie said:**
> I know this is an old thread, but I just wanted to add that the "create startup disk" utility will not work with flash or pen drives that use file compression software, I learned this the hard way...thx :)

How does one get rid of the file compression software?

---

### Post by cadefy on 2012-05-25
BUMP

Mine gets stuck on Step 2 (Extracting) @ 39% - I formatted it with FAT with no luck, then with FAT32 with no luck, what's going on?



UPDATE:
UNetbootin can get stuffed for all I care
I used "Linux Live USB Creator" found at [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download) and worked fine :)

---

### Post by oldos2er on 2012-05-25
Old thread closed.

---

