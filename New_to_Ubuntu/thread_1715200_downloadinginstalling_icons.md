---
title: "downloading/installing icons"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by noob.bot76 on 2011-03-26
i'm trying to install new icon themes. i tried following the steps on this post: [http://ubuntuforums.org/showthread.php?t=433955](http://ubuntuforums.org/showthread.php?t=433955)

the files are in /usr/share/icons, and i can see the other icon themes listed in same folder; however, when i go to applications, and select appearances, then icons, the theme is not listed. 

files have been extracted -- but i'm not sure if i did that right. i just moved the zip file to my "wallpaper" folder, and then selected "extract here". 

thanks

---

### Post by noob.bot76 on 2011-03-27
bump

still no luck -- i followed a suggested youtube tutorial and copied files into my .themes folder. no change. 

any suggestions?

---

### Post by Enigmapond on 2011-03-27
What theme are you trying to install? I ask because both of the ways you listed should have worked. There is also another, open your pref/appearances and just drag the unzipped folder over it. It should install by itself.

---

### Post by TeoBigusGeekus on 2011-03-27
The icons should not be extracted in your wallpaper folder and they should not be extracted in your themes folder as well.
Extract the archive to your
```
~/.icons
```
folder.

---

### Post by noob.bot76 on 2011-03-27
the icon set is called "leaf folder icons" -- i downloaded them from either xfce-look or gnome-look (can't remember which)

i don't seem able to drag and drop the folders to to my icon list. when i open "appearances" and select the icon tab, i get my list of icons. but when i try to drag and drop the "leaf folder" it doesn't work. 

the reason i did an "extract here" in my wallpaper folder is because whenever i tried the "extract to" option i got an error message: "the folder contents could not be displayed: operation not supported"

do i move the zip file to my /usr/share/icons folder and then perform "extract here"? 


thanks

---

### Post by TeoBigusGeekus on 2011-03-27
See if you have an .icons folder in your home partition. If not, create one
```
mkdir ~/.icons
```
Extract the archive into the folder and you're done.

---

### Post by noob.bot76 on 2011-03-27
teo, 

sorry to be so ignorant, but i'm still not sure how to successfully perform the extraction. 

i have an .icons folder in my home folder. but, as i said in previous posts, when i try to "extract to" i get an error message. can i drag an drop my "extracted here" files to my .icon folder?

thanks

---

### Post by GWBouge on 2011-03-27
I'm not sure that I've ever had to manually extract a theme ...

Have you tried just opening up System -> Preferences -> Appearance, and drag-n-dropping the archive (the original download, not the extracted folder) into the Theme window?

---

### Post by Enigmapond on 2011-03-27
> **noob.bot76 said:**
> teo, 

sorry to be so ignorant, but i'm still not sure how to successfully perform the extraction. 

i have an .icons folder in my home folder. but, as i said in previous posts, when i try to "extract to" i get an error message. can i drag an drop my "extracted here" files to my .icon folder?

thanks

What error are you receiving when attempting to extract? There may be a problem with the archive.

---

### Post by noob.bot76 on 2011-03-27
ERROR: "the folder contents could not be displayed: operation not supported"

i've never really extracted things before -- so don't put an stupid mistake past me!

---

