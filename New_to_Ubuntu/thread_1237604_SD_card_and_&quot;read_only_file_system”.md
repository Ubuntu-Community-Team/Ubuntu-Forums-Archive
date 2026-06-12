---
title: "SD card and &quot;read only file system”"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by bob brazie on 2009-08-11
New to Ubuntu 9.04

Hi, I have an SD card that I use in my phone to store and play music.

I am trying to delete songs off of the media but get a message say in is a 'read only file system”

How do I change this so I can remove songs and free up some space on the disk?

Thanks in advance. Bob

---

### Post by gardara on 2009-08-12
You could try to chmod the card and see if that helps, I've had to do it with a mp3 player that appeared as read-only.

```
sudo chmod -R 777 /wherethe/player/is/mounted/
```

chown might also work and even unmounting/mounting, a external HDD I have once appeared as read-only and I couldn't chmod it... plugging it out and back in strangely fixed it.

It might also be a good idea to run fsck on the filesystem of the SD card.

---

### Post by bob brazie on 2009-08-12
Sorry but neither command worked. Mount/unmount doesn't work either.

---

### Post by emeraldgirl08 on 2009-08-12
Try changing permissions in the songs or folders you want to delete to read and write. 

Then delete.

---

### Post by bob brazie on 2009-08-12
Thanks, I tried that but it won't let me.

Is there a way to force a format and what would the command look like?

---

### Post by bob brazie on 2009-08-12
I found there is a little slide switch on the side of the card that prevents altering anything written to it unless it is in the right position.

I guess I should read the packaging instructions before I throw it away. <g>

Thanks to everyone. Bob.

---

