---
title: "renaming /home folders to lowercase"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by bvargo on 2011-05-26
as in 
/home/Desktop
/home/Downloads
/home/Documents
/home/Music
/home/Videos

This is annoying to me to have to remember that they're initial caps.  I did ```
mv Videos videos
mv Downloads downloads
``` etc., and I realize I'm going to have to figure out what is using Downloads and correct that (presumably FF and Transmission, but we'll see), but is there any way to get ubuntu to recognize desktop instead of Desktop?

thanks

---

### Post by matt_symes on 2011-05-26
Hi

> **bvargo said:**
> as in 
/home/Desktop
/home/Downloads
/home/Documents
/home/Music
/home/Videos

This is annoying to me to have to remember that they're initial caps.  I did ```
mv Videos videos
mv Downloads downloads
``` etc., and I realize I'm going to have to figure out what is using Downloads and correct that (presumably FF and Transmission, but we'll see), but is there any way to get ubuntu to recognize desktop instead of Desktop?

thanks

In Nautilus file browser, right click on the folder (Desktop, Documents) and select the rename option. Rename as desired.

Make sure you use Nautilus and your ~/.config/user-dirs.dirs should get updated. Don't do it in the terminal unless you want to update that file manually.

Kind regards

---

### Post by gmargo on 2011-05-26
> **bvargo said:**
> is there any way to get ubuntu to recognize desktop instead of Desktop?

You can use symbolic links so that both capitalized and lower case directory names work:
```

ln -s Desktop desktop
ln -s Downloads downloads
ln -s Documents documents
ln -s Music music
ln -s Videos videos

```The advantage of this method is that you won't have to track down any application's usage of these directories.

---

