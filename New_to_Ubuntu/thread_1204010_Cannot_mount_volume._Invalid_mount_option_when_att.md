---
title: "Cannot mount volume. Invalid mount option when attempting to mount the volume"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by interceptorV8 on 2009-07-04
i've been using ubuntu for over a year now and am still quite a noob when it comes to messing around with the terminal.  

BUT, i've probably found a very simple solution to the problem stated within the title of the thread.

for some reason, one of my external usb hard drives felt like acting weird.  it was working fine for a while and then i safely unmounted it.  when i went back to mount it again, it gave: mount volume. Invalid mount option when attempting to mount the volume."

i tried searching the forums.... switched to windows for the first time in months (it worked fine in windows - and i safely unmounted again), switched back to ubuntu and the drive still would not mount.  

MY SIMPLE SOLUTION:

with the drive ON, i opened up the partition editor, "gparted", selected the drive, right-clicked the the ntfs file system line and i had the option of "mount to sdh1."  (the ntfs configuration tool wouldn't work either)

after i clicked this, the hard drive did it's thing and automounted.  i'd just thought i'd share this since i've read numerous posts and no one has listed anything like this.  gosh i feel like such a noob...

---

### Post by Jose Catre-Vandis on 2009-07-04
What command were you running at the terminal to mount your external usb drive?

Did you try unplugging and plugging back in? (Quicker than loading gparted and fiddling!)

---

### Post by austinpsycho on 2009-07-04
I wonder if people actually read the whole post before responding..  it seems to happen alot that people respond without reading previous posts in their entirety.. :(

---

### Post by niteshifter on 2009-07-04
I wonder about that also. Such as when a poster finds a clever solution to a vexing problem.

But is using a dangerous-as-hell tool to get around the problem. With no mention of if this fixed the problem permanently.

Followed by a another poster - who spotted the danger - who asks for more info from the first poster, looking to save them from themselves. Very community oriented, that one is.

Followed by yet another poster who wonders if anyone reads these things.

Followed by another poster - who can't help but notice the irony so far in this saga - who asks:

@interceptorv8: How were you mounting the drive? Letting the system do it? Or manually via command line?

---

### Post by Jose Catre-Vandis on 2009-07-04
:) @ niteshifter

---

