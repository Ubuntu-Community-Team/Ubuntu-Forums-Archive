---
title: "Suddenly booting in text mode"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by gackt on 2009-05-31
Hi, I'm not sure what i did but my ubuntu wont start straight to loading screen anymore, instead it give me much texts like, 

loading driver.......[ok]
checking this        [ok]
checking that        [ok]

and after this, the loading screen with progress bar appear. Usually my ubuntu goes straight to loading screen. What happen? Thanks and sorry for my English

---

### Post by Elfy on 2009-05-31
Have you cahnged anything recently - I had same issue after a swap change - run this

```
ls -al /dev/disk/by-uuid
```

Find the UUID which relates to your swap partition, now run this and check that the swap mount match the above UUID

```
cat /etc/fstab |grep swap
cat /etc/initramfs-tools/conf.d/resume
```

Edit - and check that your menu list shows quiet at the end of the line

```
cat /boot/grub/menu.lst
```

Look for 

```
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bd3eb939-a847-4b87-b1b8-3d39b7a51382 ro **_quiet_** splash
```

---

### Post by The Mad Mule on 2009-05-31
For me, that started after I installed the "restricted codecs" package to play the media things.

So I reformatted, and from now on I'm sticking to my old method of just installing them manually whenever Ubuntu tells me that the file can't be played because of missing codecs.

---

### Post by gackt on 2009-05-31
yes you are right i play abit with the swap partition, but all my grub has ro quiet parameter but still the booting is in verbose mode. Thanks anyway

---

### Post by Elfy on 2009-06-01
Did you check the swpa partition UUID's - I would suspect that is the reaason.

---

### Post by gackt on 2009-06-01
Sorry dont quite understand, can i post something to make you understand this issue better? Thanks

---

### Post by QIII on 2009-06-01
Here's a thread I was in several days ago.

[http://ubuntuforums.org/showthread.php?t=1167553](http://ubuntuforums.org/showthread.php?t=1167553)

Read how the OP solved the issue in the first item.

---

### Post by Elfy on 2009-06-02
> **gackt said:**
> Sorry dont quite understand, can i post something to make you understand this issue better? Thanks

Run the first 3 commands I gave in post #2 - paste the outputs here. I have had the same thing in the past.

---

