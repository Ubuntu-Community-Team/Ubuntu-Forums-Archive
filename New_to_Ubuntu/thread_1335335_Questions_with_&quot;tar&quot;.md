---
title: "Questions with &quot;tar&quot;"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by emigrant on 2009-11-23
hi all,
im having the following doubts with tar



[LIST=1]
[*]what i have seen is the tarball is created at the destination where the prompt is now. how to direct the archive creation to another destination? ie. in my desktop i have a folder called Pictures. i want to tar this and put in a new folder in my documents. i think if i show it in code it would be much clear (im now in desktop):tar ```
cvjf pictures.tar.bz2 ~/Desktop/Pictures  <to/the/destination>
```
[*]i have several folders and files in my /Documents i want to mark a few from them and create an archive
[/LIST]

thank you all :popcorn:

---

### Post by Sam on 2009-11-23
Use the -C switch:
```
tar cvjf file.tar.bz2 -C destination/directory
```

Get help with:
```
man tar
```

EDIT: Oops wrote too fast, I didn't see it was for creating tar files.

---

### Post by emigrant on 2009-11-23
man tar didn't help much :( or may be im too lazy...

scenario:
i want to create an archive of /Desktop/Picrures and put it into a new folder 123 (tar should should create it) in the desktop
```
emigrant@emigrant-desktop:~$ pwd
/home/emigrant
emigrant@emigrant-desktop:~$ **[COLOR=DarkRed]tar cvfj hallo.tar.bz2 Desktop/Pictures/ -C Desktop/Pictures/123[/COLOR]**
Desktop/Pictures/
Desktop/Pictures/hallo.jpeg
Desktop/Pictures/fddd.png
Desktop/Pictures/drawing.png
Desktop/Pictures/Ubuntu_logo_wall_by_gigatwo.png
Desktop/Pictures/lucidlynx_black_nologo.png
Desktop/Pictures/g4569.png
Desktop/Pictures/lucid_lynx-wallpaper.svg
Desktop/Pictures/fddd.svg
Desktop/Pictures/fdd1d.png
Desktop/Pictures/NATURE-AcadiaRockyBeach_1920x1200.png
tar: Desktop/Pictures/123: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
```

---

### Post by emigrant on 2009-11-23
in other words:

```
emigrant@emigrant-desktop:~$ tar cvfj /home/arshad/Desktop/[COLOR=DarkRed]123[/COLOR]/mytar.tar.bz2 Desktop/Pictures/
```
that 123 folder should get created automatically

---

### Post by emigrant on 2009-11-23
another problem (more preferred than the above) :KS

how to untar like this:

```
tar xvjf </the/file/from/source.tar.bz2> </the/destination/to/extract>
```

---

### Post by reeboker on 2009-11-23
[http://www.linuxconfig.org/tar]("http://www.linuxconfig.org/tar")

Be happy and UTG (use the google). :D

---

### Post by ShadowMage on 2009-11-23
> **emigrant said:**
> hi all,
im having the following doubts with tar



[LIST=1]
[*]what i have seen is the tarball is created at the destination where the prompt is now. how to direct the archive creation to another destination? ie. in my desktop i have a folder called Pictures. i want to tar this and put in a new folder in my documents. i think if i show it in code it would be much clear (im now in desktop):tar ```
cvjf pictures.tar.bz2 ~/Desktop/Pictures  <to/the/destination>
```
[*]i have several folders and files in my /Documents i want to mark a few from them and create an archive
[/LIST]

thank you all :popcorn:

You can move the archive afterward by doing mv <<archive filename>> <<to/the/destination>>. For example,
```
mv pictures.tar.bz2 ~/Documents
```When executing the tar command to create the archive, though, i believe the format is
tar <<switches>> <<archive filename>> <<list of files to tar>>
so for example if you type
tar cvjf pictures.tar.bz2 ~/Desktop/Pictures something/else
it will put both "~/Desktop/Pictures" and "something/else" in an archive called pictures.tar.bz2

Hope this helps.

---

