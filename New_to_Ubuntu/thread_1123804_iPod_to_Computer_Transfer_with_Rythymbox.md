---
title: "iPod to Computer Transfer with Rythymbox"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by alanfang on 2009-04-12
I am trying to transfer some files from my iPod to my computer. I can do that fine, but I would like to leave the original file/folder structure intact. Is this possible?

---

### Post by llamabr on 2009-04-12
Yes.  Just use the 'cp' command, rather than the 'mv' command.

---

### Post by alanfang on 2009-04-12
cp? Is this from the terminal or the gui?

---

### Post by llamabr on 2009-04-12
cp means copy, mv means move.

so if you want to leave it where it was, and put another copy in the new place, you want 'cp'.

If you want to put it in a new place, and remove it where it was, you want 'mv'.

This is via the command line.

---

### Post by alanfang on 2009-04-12
The issue isn't having copying the files.

The issue is when I copied the files to my iPod I had a folder setup with artists albums etc. I want to keep that folder hierarchy when I transfer the songs from my iPod to my computer. Given the amount of music I have doing it by hand would be a huge hassle.

---

### Post by llamabr on 2009-04-12
Doing it one by one would be a hassle.  This is the strength of writing scripts with the command line.

What are you trying to do?

---

### Post by drowner on 2009-04-12
> **alanfang said:**
> The issue isn't having copying the files.

The issue is when I copied the files to my iPod I had a folder setup with artists albums etc. I want to keep that folder hierarchy when I transfer the songs from my iPod to my computer. Given the amount of music I have doing it by hand would be a huge hassle.

Rhythmbox won't do that.

A command from the terminal is easiest, or just drag and drop.

How did you get your files organised on your ipod, btw?

---

### Post by Simian Man on 2009-04-12
Unfortunately there is no simple way to do this since the iPod doesn't organize your music in any logical way.

What you can do, if you have the id3 tags intact, is write a script to use the album and artist info to automatically create the directory hierarchy and copy in your music.

---

### Post by drowner on 2009-04-12
> **Simian Man said:**
> Unfortunately there is no simple way to do this since the iPod doesn't organize your music in any logical way.

What you can do, if you have the id3 tags intact, is write a script to use the album and artist info to automatically create the directory hierarchy and copy in your music.

I've been looking for such a script for a long time. I would write it myself but i don't have the knowledge.

My computer has the ability to read and write mp3, aac and m4a tags, so I guess everything is there - just don't know how to write the script!

---

