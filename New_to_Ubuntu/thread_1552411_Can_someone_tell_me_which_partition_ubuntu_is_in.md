---
title: "Can someone tell me which partition ubuntu is in?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-08-13
I had a bit of a problem which meant that I needed to reinstall ubuntu (I deleted a partition in Windows).  I have 2 HDDs on my laptop and was wondering if anyone could tell me which partition Ubuntu is in.

I've attached the Gparted screenshots for each drive

---

### Post by RiceMonster on 2010-08-13
/dev/sdb6

/dev/sdb7 is also an important partition, as this is your swap space.

---

### Post by GaryTheCat on 2010-08-13
thanks for that :) does that partition need to be that big? I keep my 'data' in the one mounted at /media/Data/ (so I can share mp3s and the like between ubuntu and vista.

Also, how can I tell which of the swap partitions relate to my current installation?

---

### Post by Elfy on 2010-08-13
I'd say not as big as that would be more than sufficient :)

The swap which is locked is  the one being used - sdb7

---

### Post by GaryTheCat on 2010-08-14
Thank you all :D

---

