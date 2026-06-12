---
title: "what does this line of code in a conky do?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-08-06
```
${execi 15 cp "`conkyBanshee -d CA | sed -e 's/album-art/media-art/'`" /home/jfreak/.album.png}
```

the conky is not working and from what I can figure out it's because nothing is being copied to .album.png.
however the album art is present in /.cache/album-art/media-art

---

### Post by ankspo71 on 2010-08-06
Hi,
It looks like it takes the album art of the currently playing song in Banshee and displays it in conky. 

Here is a link to some instructions to get a conkybanshee script. [http://swiss.ubuntuforums.org/showthread.php?t=1223883](http://swiss.ubuntuforums.org/showthread.php?t=1223883)
I think you will need this to get that conkybanshee line of code in conky to work.

Hope this helps.

---

### Post by jfreak_ on 2010-08-06
> **ankspo71 said:**
> Hi,
It looks like it takes the album art of the currently playing song in Banshee and displays it in conky. 

.

I figured that out, I have the script installed as well. But what does the given code do , from WHERE is it copying the album art?
I don't understand the sed -e 's/.... part

---

