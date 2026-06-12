---
title: "Renaming files in date order?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by MarkX on 2010-09-16
As above, looking for a file renamer that will rename (or re-number) files in date-created order please.

---

### Post by nothingspecial on 2010-09-17
As far as I know, linux does not store "date created"

You can only find files by when they were accessed, modified or changed status last.

So what you want to do is impossible unless, none of the files have been changed in anyway or even looked at since they were created.

So, if for example you are wanting to rename a load of photos in date order it will only work if you have never viewed them.

I fully expect to be corrected on this however.

---

### Post by coffeecat on 2010-09-17
> **nothingspecial said:**
> So, if for example you are wanting to rename a load of photos in date order it will only work if you have never viewed them.

I fully expect to be corrected on this however.

Indeed! :p

With photos you have the EXIF data and apps like gThumb can rename the file and include the creation date from the EXIF data in the filename.

The OP poses an interesting question, however. In theory I would have thought it would be possible to include the last modified date (which is in the file header) in the filename. This, of course, may not be the same as the creation date, but I wasn't able to find an app which would do even this. The repository apps GPRename and pyRenamer look to be decent basic file renamers but I can't find an option to include modified date in either of them.

---

### Post by Rubi1200 on 2010-09-17
What about using a bash script to handle the additional information?

---

### Post by coffeecat on 2010-09-17
@MarkX, if you're looking for a GUI app, try KRename. It has a fairly user-hostile interface and being a KDE app will drag a load of KDE stuff in if you're using gnome, but it can include the modified date in the filename. Not exactly what you want, I know.

---

### Post by nothingspecial on 2010-09-17
> **coffeecat said:**
> Indeed! :p

With photos you have the EXIF data and apps like gThumb can rename the file and include the creation date from the EXIF data in the filename.


Ha ha, photos was the worst example.

---

### Post by MarkX on 2010-09-17
> **coffeecat said:**
> @MarkX, if you're looking for a GUI app, try KRename. It has a fairly user-hostile interface and being a KDE app will drag a load of KDE stuff in if you're using gnome, but it can include the modified date in the filename. Not exactly what you want, I know.

I'll give it a go.

---

### Post by David Andersson on 2010-09-17
> **coffeecat said:**
> The repository apps GPRename and pyRenamer look to be decent basic file renamers but I can't find an option to include modified date in either of them.

**pyRenamer** can insert [s]modification date (Unix) and/or[/s] **image creation date** (EXIF). Check the Patterns and Images tabs.

**GPRename** can neither, it appears (but can be useful for other tasks).

Both pyRenamer and GPRename have **preview** modes, so you can see what they will do to your files before they do it.

In pyRenamer, hover the mouse to see a bubble with syntax description. By "catched item" in the rename pattern they mean anything matching "{@}", "{X}", "{C}" or "{L}" in the original name pattern. If you use the default "{X}" then "{1}" in the new name is where the old name is kept.

**Example**: to add time at the beginning of the name for easy ordering, use "{X}" for original pattern, and for rename pattern "{imageyear}-{imagemonth}-{imageday}_{imagehour}:{imageminute}_{1}".

**Example**: to later remove the time at the beginning of the name, use "{#}-{#}-{#}_{#}:{#}_{X}" for original pattern, and  for rename pattern "{6}".

---

### Post by coffeecat on 2010-09-17
> **David Andersson said:**
> **pyRenamer** can insert **modification date** (Unix) and/or **image creation date** (EXIF). Check the Patterns and Images tabs.

**GPRename** can neither, it appears (but can be useful for other tasks).

Thanks for that. I must have missed that when I looked at pyRenamer. I'll have another look when I get a moment later. The OP might find pyRenamer better than krename. Krename almost reduced me to tears of frustration and rage trying to work out how to use it when I first started with Linux 5 years ago. Even without the K prefix you can tell it was developed by a KDE enthusiast. :rolleyes:

---

### Post by digitography on 2010-09-17
pyrename is the way to go, even gives you a "Preview" option so you can check that what you think you are asking it to do is what it will actually do.
Saved my sanity.

---

### Post by coffeecat on 2010-09-17
> **David Andersson said:**
> **pyRenamer** can insert **modification date**

Sorry, no, can't work that one out. {imagedate} gives you the EXIF creation date. If you use {imagedate} in the Images tab with non-image files it get ignored. If you use {imagedate} in the Patterns tab with non-image files you get "{imagedate}" added to the filename. :| {date} simply gives you today's date. There doesn't seem to be an option for the Unix modification date. Certainly not listed when you hover the mouse and everything I've tried doesn't work.

---

### Post by David Andersson on 2010-09-17
> **coffeecat said:**
>  :| {date} simply gives you today's date. There doesn't seem to be an option for the Unix modification date.

Sorry. I was wrong. Didn't test that. Is the command line acceptable?

Then there is the **prename** command. It can use modification time, or anything else in the world if you like.
Simple example, lowercase the suffix:
```
prename 's/JPG/jpg/' *.JPG
```
Example, add file modification time to the beginning of filenames:
```
prename 's/(.*)/use POSIX qw(strftime);strftime("%Y-%m-%d_%H:%M:%S_",localtime((stat($1))[9])).$1/e' *.JPG
```
Example, remove time from the beginning of filenames:
```
prename 's/^....-..-.._..:..:.._//' *.JPG
```
This I have tried.
Add command option **-n** for preview.

---

### Post by coffeecat on 2010-09-18
> **David Andersson said:**
> Is the command line acceptable?

I wasn't sure whether you were asking the OP or myself. But thanks for that.

---

### Post by candtalan on 2010-09-18
I needed to rename some big bunches of files in different ways (add prefix and whatever) and found that Thunar File manager had a good re naming capability. It was perfect for me, and all GUI too.

---

