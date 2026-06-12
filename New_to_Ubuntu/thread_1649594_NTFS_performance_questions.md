---
title: "NTFS performance questions"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-12-20
How is the performance with using NTFS? I don't mean using it as the main file system for an ubuntu install. And perhaps 'performance' is not the correct word.

Here is the situation.

I have a machine that Windows Vista failed horrible on me the other day. Everything in the %windows\system32\drivers\ folder has become corrupted. I installed a second HDD and installed windows on that just to have a working OS on it from which to work on the first. 

Actually, it isn't my machine, it is a friends.

While booted in the working OS, I try to access the first HDD and it says that access is not allowed, that I don't have privileges to do so. I have changed the drives ownership to my admin group and also given my admin group full rights and privileges. Yet it still wont open for me. It doesn't retain the privileges settings and ownership settings after a reboot.

Any windows virus scanner has access to it and can scan all the directories and files just fine.

So anyway, after many attempt to have it work, I decided to pull out my trusty live linux usb flash drive. I plugged it in, booted up, and voila!! I could see both drives, her old vista with the corrupt sys files, and the new vista that I recently installed.

I could open all files and view all content on both drives no problem.

I need to copy over the contents (docs, music, pics, vids, etc) from her old drive (the corrupt one) to the new one for backup purposes.

This is where my concern comes in.

In the past, like maybe 1-2 years ago, I tried to transfer over some files from one NTFS to another NTFS drive while logged into ubuntu. I think it was 9.04 or maybe it was 8.10. The files transferred over but were then unreadable while logged into the windows system. It had something to do with the NTFS driver that ubuntu used in that time period and it wasn't 100% stable yet.

How are things now? Should I be able to transfer her files over without any concerns?

any ideas, hints, tips, advise would be greatly appreciated. Thanks!!

-Spydey

---

### Post by cariboo on 2010-12-20
You can run nautilus as root to transfer the files, as Linux permissions don't work on a NTFS system. Press Alt-F2 and type:

```
gksu nautilus
```

The NTFS-3G drivers have gotten much better since the last time you tried to transfer files.

---

### Post by spydeyrch on 2010-12-27
Thanks for the reply, I was able to transfer the files over and they work just fine. I appreciate your assistance. :)

-Spydey

---

