---
title: "Persistent option for USB Creator"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Arla on 2010-02-07
Can anyone tell me what this really means, 

For example, if I create a USB startup key, that is 1GB in size, using the Ubuntu install, I have about 270MB of "space" after the CD,

I can setup either none, or between 128 and the full 270 for persistence, I assume if I choose none, then it works just like the actual Live CD (Nothing is persisted) however what is the difference between choosing 128 vs 270? What happens to the "extra" space if I choose 128?

What I'm TRYING to do, is create a bootable USB that has GNUCash on it, but just confused by this option.

---

### Post by The Cog on 2010-02-07
I believe that the space you allocate for persistence is a partition (or rather, a file I think) that is mounted using as a special filesystem, and it stores the changes to the original CD image. This allows you to save personal settings or install software packages and retain the changes.

---

### Post by tea for one on 2010-02-07
> **Arla said:**
> Can anyone tell me what this really means, 

For example, if I create a USB startup key, that is 1GB in size, using the Ubuntu install, I have about 270MB of "space" after the CD,

I can setup either none, or between 128 and the full 270 for persistence, I assume if I choose none, then it works just like the actual Live CD (Nothing is persisted) however what is the difference between choosing 128 vs 270? What happens to the "extra" space if I choose 128?

What I'm TRYING to do, is create a bootable USB that has GNUCash on it, but just confused by this option.

Good evening

As I understand the process, when you create a USB installation of Ubuntu, you are creating the equivalent of a "live" CD i.e. approx 700 MB.

The remaining space on your USB device can be used for "persistent" storage i.e. any software that you download after the installation or any data that you wish to keep will remain in the "persistent" area.

Therefore, if you use a 2GB device, you must allocate approx 700 MB for the Ubuntu OS and then you can have approx 1.3GB for additional software and data.

I hope this helps you to decide the size of device you may need.

Best wishes

---

### Post by tea for one on 2010-02-07
Whoops, 

I forgot to add that any unused space on a USB device can still be used in Windows or Linux as a storage device for data, subject to the file system that is on the device.

I use Fat 32 on my USB sticks so that I can use the spare space on Windows at work and Ubuntu at home.

---

