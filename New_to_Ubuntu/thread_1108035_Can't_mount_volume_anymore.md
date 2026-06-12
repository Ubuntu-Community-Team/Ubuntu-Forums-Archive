---
title: "Can't mount volume anymore"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Presi on 2009-03-27
I specified /media/disk/ as mounting point for one of my hard disk (through 'properties', 'volume' tab, I believe)

Now I can't mount it anymore, It says "mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

How can I modify the volume mounting point now?

Thanks,

-Presi

---

### Post by kanikilu on 2009-03-27
First of all, I believe "/media/disk" is a built-in mountpoint that Gnome tries to use, so I would change that to something else to leave that available to the system.

When setting it, I believe I ran into the same issue as you - I want to say that in the properties it's actually just wanting the last part of the mountpoint. For instance if you want to mount to /media/harddrive, you would enter just "harddrive". It's not very obvious/intuitive :rolleyes:

What kind of device is this? If it's an internal hard drive or (semi-)permanent external hard drive, I would probably add it to /etc/fstab (using the UUID) rather than letting HAL try to manage it.

If it's a removable drive like flash memory, then, there should be a way to fix it, but I honestly can't remember what I did when I ran into that problem :oops: Hopefully someone else can answer that...

// Edit - I just did a quick search and found this blog post...see if that helps...

[http://howtoxyz.blogspot.com/2008/07/how-to-mountpoint-cannot-contain.html](http://howtoxyz.blogspot.com/2008/07/how-to-mountpoint-cannot-contain.html)

---

### Post by Presi on 2009-03-29
Thanks Kanikilu,

I followed the instructions from the link and it solved the problem!

Thanks again,

-prsi

---

