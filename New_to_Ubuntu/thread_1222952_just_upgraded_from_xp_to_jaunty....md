---
title: "just upgraded from xp to jaunty..."
date: 2009-07-25
forum: New to Ubuntu
---

### Post by tyler.mcg on 2009-07-25
intro:
Well I think I have to learn everything all over again. Oh well, I'm finally done with windows once and for all. !!! *tada*

[main] I was hoping someone could tell me an application that will sort files into folders by types. ie (music, videos, documents) the reason is I have a partition (ntfs) for all my backed-up media when my windows xp got those couple hundred viruses or so. its just disorganized so badly I want it to scan and file them in the right folders. (and delete duplicates if possible)


**aside: could a windows virus infect me? if I have WINE installed?**

---

### Post by halitech on 2009-07-25
welcome aboard and hope you enjoy :)

as far as sorting things, I don't know of any programs with a gui that will do it but you could try something like this from the terminal

```
cp /mount/point/*.mp3 /home/(USER)/Music/*.mp3
```

cp will copy, if you want to move them then use mv instead of cp. change /mount/point to reflect the actual location and change (USER) to your username. You can do the same with *.avi, etc but make sure you create the destination folders first.

---

### Post by esalnoj on 2009-07-25
Nautilus by default can only sort by clearly defined sorting methods such as alpa-numeric, time modified, and etc.

The only difference it knows between "band.mp3" and "banana.mp3" is alpha-numeric and file modified/created date-time, also permissions. It does not know to sort "band.mp3" into "/media/storage/band" on its own.

In short, you tell files and folders where to go. Nautilus just does it graphically for you.

---

### Post by tyler.mcg on 2009-07-25
> **halitech said:**
> welcome aboard and hope you enjoy :)

as far as sorting things, I don't know of any programs with a gui that will do it but you could try something like this from the terminal

```
cp /mount/point/*.mp3 /home/(USER)/Music/*.mp3
```cp will copy, if you want to move them then use mv instead of cp. change /mount/point to reflect the actual location and change (USER) to your username. You can do the same with *.avi, etc but make sure you create the destination folders first.

where do I create the destination folder?

---

### Post by halitech on 2009-07-25
I created folders for my music and photos right in my home folder using Nautilus

---

### Post by k3lt01 on 2009-07-25
> **tyler.mcg said:**
> where do I create the destination folder?

> **halitech said:**
> I created folders for my music and photos right in my home folder using Nautilus

When you install Ubuntu it sets up various folders in your /home/(user) folder. If you go up to Places in the top panel you will see Home Folder, Desktop, Documents, Music, Pictures, Videos. These folders are already created for you so if your /home partition-folder is large enough you can copy everything to the appropriate folder (i.e. Music) there.

---

