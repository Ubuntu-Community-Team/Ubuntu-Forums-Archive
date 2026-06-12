---
title: "Boot Screen"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by sdlynx on 2009-07-06
I moved around some partitions on my HDD (including Ubuntu's partition) and now Ubuntu shows text during boot up instead of the screen with the bar and the Ubuntu logo.  I figured the first time it was just because it was running diagnostics after being moved but it happens everytime.  I tried to change the settings using Startup-Manager but it was already set to show the splash and not the boot text during bootup.  I tried unchecking them, applying that, and then checking them, but it didn't work... any ideas?

---

### Post by sdlynx on 2009-07-06
I tried dpkg-reconfigure usplash and now the splash screen shows up shifted to the right of the screen during shutdown and startup.  The startup screen shows the splash when the bar is moving to the right and left but once it should start making the bar bigger it goes into the text mode.

---

### Post by Elfy on 2009-07-06
Run this to find your UUIDs, find the swap partitions number.

```
ls -al /dev/disk/by-uuid
```

Chek the UUID for your swap in fstab

```
cat /etc/fstab |grep swap
```

Check the UUID for your swap in the initramfs tools file

```
cat /etc/initramfs-tools/conf.d/resume
```

They should match, if you need to change the initramfs number you must run this to allow it to work

```
sudo update-initramfs -u
```

---

### Post by Gone fishing on 2009-07-06
I had this problem and this fixed it.

1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart 

Just a question what is the advantyage of UUIDs over /dev/sda1 for example?

---

### Post by Mulenmar on 2009-07-06
[QUOTE=Gone fishing;7568642Just a question what is the advantage of UUIDs over /dev/sda1 for example?[/quote]

If memory serves me correctly, something in the kernel was changed some versions back, and the change made it possible for the same partition to get assigned different device names (ie, /dev/sdf1 instead of /dev/sdb1) at different times, and UUID (Universally Unique IDentifers) make this statistically impossible.

I've only encountered this problem with USB-based flashdrives, and only on one computer which happens to have memory card-type adapters working on the same USB bus.

*Note: I am nowhere near an expert on this*

---

### Post by sdlynx on 2009-07-06
@forest pixie
Thanks very much it worked!!!

@Gone Fishing
Sorry I couldn't try out your way lol

Can anyone explain to me why it is the swap that controls whether the boot screen looks like that?

---

### Post by Elfy on 2009-07-06
It doesn't as far as I know - what was happening (I think) was that it was attempting to show you where the error was.

Why it does it I will leave to someone else more knowledgeable than I ;)

---

### Post by sdlynx on 2009-07-06
> **forestpixie said:**
> It doesn't as far as I know - what was happening (I think) was that it was attempting to show you where the error was.

Why it does it I will leave to someone else more knowledgeable than I ;)

Oh I see... well good enough XD

I don't think the developers figured that a split second wouldn't be enough to read and recognize the error...

---

