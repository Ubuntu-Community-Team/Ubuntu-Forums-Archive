---
title: "Move all of my mp3 files to folder"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by marko_4454 on 2009-04-28
Hi all,
So I have my Amarok nicely organized using the subdirectory structure, but I want to copy all of the MP3's into this backup source **without** the folder structure. I found the following command that should do the task, however it doesnt work. Any help?

```
marko@my-desktop:/media/Program_Files/Amarok_Music$ find . -iname '*.mp3' -execdir cp {} /media/Program_Files/Music_Backup\;
find: missing argument to `-execdir'
```

Thanks!

EDIT: Oh yea, my music collection is ~4000 songs, so going folder by folder is out of the question, thats why I am trying to use a command to do it for me.

---

### Post by llamabr on 2009-04-28
You need -execdir {} +

don't forget the + sign

---

### Post by marko_4454 on 2009-04-28
> **llamabr said:**
> You need -execdir {} +

don't forget the + sign

Thanks for your post llamabr, but it still didnt work. I tried tar'ing it and it almost worked, but it kept the structure which I dont want. Maybe I am just misplacing the + sign. These are the commands I tried.

```

find /media/Program_Files/Amarok_Music/ -iname '*.mp3' -execdir mv {} /media/Program_Files/Music_Backup/ +
```
find: missing argument to `-exec'


```
find /media/Program_Files/Amarok_Music/ -iname '*.mp3' -execdir mv {} + /media/Program_Files/Music_Backup/
```
find: paths must precede expression: /media/Program_Files/Music_Backup/
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

---

### Post by marko_4454 on 2009-04-28
I got it!!!
So by looking at the following link: [http://ubuntuforums.org/showthread.php?t=407651](http://ubuntuforums.org/showthread.php?t=407651)

in the post by bashologist, you can just modify his command and remove the "--parents" part and its going to work. If you wanna keep the folder structure, then keep --parents.
Anyways, thanks!

---

### Post by jeff_re on 2009-08-27
To meet your needs on my setup it looks like this:

```
find . -type f -iname "*.mp3" -execdir mv {} "/cygdrive/c/Documents and Settings/Stegosaurus/Desktop/mp3
```but I am looking to keep the mp3s inside their parent directories.  The --parent argument doesn't work with mv so can you help me think of something that will work here?

My thought is if there's a variable name for the parent folder of the found .mp3 file a code like this would work:

```
find . -type f -iname "*.mp3" -execdir mv {} "/cygdrive/c/Documents and Settings/Stegosaurus/Desktop/mp3/*PARENT_FOLDER*/
```

Any ideas?

---

