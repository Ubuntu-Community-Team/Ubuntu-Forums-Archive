---
title: "gnome-video-thumbnailer is using 100% CPU"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-08-07
When I download a video file (through Transmission or Firefox) and nautilus is open on the folder where the file is downloading I notice a process called "gnome-video-thumbnailer" that is using up 100% of my CPU.

It appears that it keeps refreshing the thumbnail of the currently downloading file. REALLY irritating as you can imagine.

Is there a fix for this?

---

### Post by philinux on 2009-08-07
Yes through nautilus. Edit Prefs.

---

### Post by abhiroopb on 2009-08-07
I found the options, but there is only something to enable or disable the thumbnails. I want the thumbnails to remain but without it making my PC unusable.

---

### Post by lovinglinux on 2009-08-07
> **abhiroopb said:**
> I found the options, but there is only something to enable or disable the thumbnails. I want the thumbnails to remain but without it making my PC unusable.

Don't open the folder where files are being downloaded. It will keep refreshing and nautilus will constantly generate the thumbnail. IMO, the thumbnailer eats too much CPU for a feature that is not really essential. This is one of the features I always disable, no matter if I'm using Windows or Linux.

You could set the thumbnailer to generate the thumbnails only if they meet a particular size limit. Since videos are usually larger than pictures, it won't cripple your Nautilus functionality that much.

---

### Post by abhiroopb on 2009-08-07
Not opening the folder is a patch, not really a solution. 

But thanks for suggesting. I guess until this is solved thats what I will have to do.

---

