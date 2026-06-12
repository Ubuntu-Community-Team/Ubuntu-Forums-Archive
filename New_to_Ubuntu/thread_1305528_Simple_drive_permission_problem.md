---
title: "Simple drive permission problem"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-29
**EDIT: Don't worry, I worked it out. Instead of having "default" in my fstab as the options to mount, I should have user,rw,exec,auto **

Hi guys,

I have two hard drives in my computer, one dedicated to my filesystem, and one dedicated to "media" - ie, music, videos, photos etc...

Anyway, I re-installed 9.10 a few days ago on my first drive, /dev/sda and I re-formatted it to be ext4. I left my other drive, Media, on /dev/sdb as ext3. 

Today I backed up my Media drive and re-formatted it to ext4, and I was just about to start copying stuff across to it and it gave me a permission error.

It's mounted at /media/Media, and the permissions say root owns it. So I changed the owner to me, with read/write access, but I still couldn't create folders or anything on the disk.

I tried rebooting, to see if it would mount it under my username at boot, but instead it got re-mounted automatically... but with root ownership.

My fstab entry for it looks like this:

```

/dev/sdb1	/media/Media	ext4	defaults 0 0

```

How can I change it so it's mounted on boot with read/write access for me?

Thanks

---

### Post by mgranet on 2009-10-29
```
sudo chown username:username /media/Media
```

EDIT: you may also want to add 'user' after 'defaults' in your fstab line you posted. (With a comma between them)

---

