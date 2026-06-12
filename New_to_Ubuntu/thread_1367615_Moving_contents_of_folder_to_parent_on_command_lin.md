---
title: "Moving contents of folder to parent on command line"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by humphreybc on 2009-12-29
I'm transferring data to my server from my external hard drive (command line - no GUI) and last night I accidentally added all my Music to Music/Music instead of just /Music - ie the command was:

```

cp -R -v /media/external/Music /data/media/Music

```

When it should have been:

```

cp -R -v /media/external/Music /data/media

```

How can I move the contents of /data/media/Music/Music to /data/media/Music without copying it?

Also, I copied my Movies folder across, but then realized I had some missing, so I added those to my external from my laptop. What's the equivalent copy command for the terminal to copy everything from a folder, but skip all the duplicates?

Thanks

---

### Post by nerdy_kid on 2009-12-29
mv /data/media/Music/Music ../Music

---

### Post by humphreybc on 2009-12-29
See I think I tried that but got this:

mv: cannot move `/data/media/Music/Music' to `/data/media/Music': Directory not empty

---

### Post by thatguruguy on 2009-12-29
have you tried it with wild cards? cd to the /Music/Music/ directory and type:

mv *.* ../

---

### Post by humphreybc on 2009-12-29
Sorry I'm not sure what you mean. What are wild cards?

---

### Post by thatguruguy on 2009-12-29
Wildcards are place holders.

If you type "mv fred.*", your computer will move fred.ogg, fred.mp3, fred.whatever, etc.

If you type "mv *.mp3", your computer will move anything with an .mp3 extension.

By typing "mv *.*", you are telling the computer to move everything in the directory, irrespective of the filename and/or extension.  Therefore, typing:
```
mv *.* ../
```
... tells the computer to move everything within the directory where you are one level up.

---

### Post by Miljet on 2009-12-29
> mv /data/media/Music/Music ../Music 
You missed the two periods before /music. Look again closely. One period stands for the current directory and two periods represent the parent directory.

---

### Post by falconindy on 2009-12-29
> **humphreybc said:**
> See I think I tried that but got this:

mv: cannot move `/data/media/Music/Music' to `/data/media/Music': Directory not empty
Because you're trying to move a directory into a directory of the same name. Won't fly. Here's what I recommend:
```
mv /data/media/Music/Music /data/media/music
rmdir /data/media/Music
mv /data/media/{m,M}usic
```
I use rmdir rather than rm -r because rmdir will fail if there are still files in the folder (which you can then address).

edit: the last mv command uses a trick called brace expansion to rename the folder. It's a great way to save keystrokes.

[QUOTE=humphreybc]What's the equivalent copy command for the terminal to copy everything from a folder, but skip all the duplicates?[/QUOTE]
man cp

---

### Post by Iyunkateus on 2009-12-29
> **humphreybc said:**
> Sorry I'm not sure what you mean. What are wild cards?
Wild cards are special characters or sequences of characters that can mean certain characters or any character.

The wildcard * means any character, any number of times.
The wildcard ? means any single character.
Brackets [] mean anything in the brackets. [abc] means a, b, or c.

I think the command you need is
```
mv * ..; cd ..; rmdir Music/
```Let's break it down:
(by the way, if you seperate commands with a semicolon, each one will be executed after the one before it finishes)
```
mv * ..
```This moves * (everything in the folder) to .. (shorthand for the parent directory, the first Music folder)
```
cd ..
```This changes the working directory from /data/media/Music/Music to /data/media/Music, the parent directory
```
rmdir Music/
```This removes the duplicate directory.

Edit: Oh meh, took too long and someone else responded. Oh well.

---

### Post by jamieleshaw on 2009-12-29
> **humphreybc said:**
> I'm transferring data to my server from my external hard drive (command line - no GUI) and last night I accidentally added all my Music to Music/Music instead of just /Music - ie the command was:

```

cp -R -v /media/external/Music /data/media/Music

```

When it should have been:

```

cp -R -v /media/external/Music /data/media

```

How can I move the contents of /data/media/Music/Music to /data/media/Music without copying it?

Also, I copied my Movies folder across, but then realized I had some missing, so I added those to my external from my laptop. What's the equivalent copy command for the terminal to copy everything from a folder, but skip all the duplicates?

Thanks
Have you tried it with the -f parameter?

---

### Post by humphreybc on 2009-12-29
> **falconindy said:**
> Because you're trying to move a directory into a directory of the same name. Won't fly. Here's what I recommend:
```
mv /data/media/Music/Music /data/media/music
rmdir /data/media/Music
mv /data/media/{m,M}usic
```
I use rmdir rather than rm -r because rmdir will fail if there are still files in the folder (which you can then address).

edit: the last mv command uses a trick called brace expansion to rename the folder. It's a great way to save keystrokes.


man cp

Hey, that worked. Thanks!

---

