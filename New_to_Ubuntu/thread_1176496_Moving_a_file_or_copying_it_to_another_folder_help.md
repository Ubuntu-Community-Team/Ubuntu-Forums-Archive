---
title: "Moving a file or copying it to another folder help"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by adventure man on 2009-06-02
Hey guys, just wondering how can I move a file to another folder.  Say a picture, from "Picture" folder to "Music" folder.  Also how can I just copy the same file between folders.  I did this in Windows xP for organizing my music/pictures a lot. I would either right click the mouse over the file/folder or on the side of the window there were usually the commands there (move/copy).  I searched in ubuntu and then forums couldn't find anything.  Thanks a bunch guys :D

---

### Post by Mornedhel on 2009-06-02
Uhm ?

On Jaunty here, Cut and Copy are available when right-clicking files and folders. I don't remember exactly but I do believe it hasn't changed since Hardy (at least).

At worst, you can still use the same keyboard shortcuts as in Windows (Ctrl+X to cut or Ctrl+C to copy, then Ctrl+V to paste).

---

### Post by Celauran on 2009-06-02
```
cp /source/path /destination/path
mv /source/path /destination/path
```

---

### Post by adventure man on 2009-06-02
Thanks guys :)  Mornedhel that pretty much solves my copying files issue.  I guess "moving files" a la windows is actually just copying to destination folder and then deleting the original file?  

Hey Celauran, can you give me an example using those codes.  Say if I want to move a picture titled "pic173" from pictures folder to music folder.  Would this be the correct way of typing the code into terminal:

mv /source/home/name/Pictures/pic173/destination/home/name/Music/pic173

I appreciate your help guys thanks :D

---

### Post by philinux on 2009-06-02
```
mv ~/Pictures/pic173  ~/Music/pic173
``` Also beware linux is case sensitive, the ~ character signifies home. Saves a lot of typing eh. ;)

---

### Post by Commander_Keen on 2009-06-02
> **adventure man said:**
> Hey guys, just wondering how can I move a file to another folder.  Say a picture, from "Picture" folder to "Music" folder.  Also how can I just copy the same file between folders.  I did this in Windows xP for organizing my music/pictures a lot. I would either right click the mouse over the file/folder or on the side of the window there were usually the commands there (move/copy).  I searched in ubuntu and then forums couldn't find anything.  Thanks a bunch guys :D

Don't forget, you should be to drag and drop as well.

---

### Post by adventure man on 2009-06-02
thanks philinux, works like a charm.  Hopefully in some future build somehow "move" can be incorporated with copy when right clicking the mouse :D

@commander_keen - yeah i was doing that for a while, just wanted to broaden my knowledge base on moving and copying files LOL :D

---

### Post by mcduck on 2009-06-02
> **adventure man said:**
> thanks philinux, works like a charm.  Hopefully in some future build somehow "move" can be incorporated with copy when right clicking the mouse :D

@commander_keen - yeah i was doing that for a while, just wanted to broaden my knowledge base on moving and copying files LOL :D

Drag the file/directory with middle mouse button and you'll get a popup window asking if you want to copy, move or link it..

---

### Post by aktiwers on 2009-06-02
I have copy/paste on right-click? Also CTRL+C and CTRL+V works great?

---

### Post by Mornedhel on 2009-06-02
> **adventure man said:**
> Hopefully in some future build somehow "move" can be incorporated with copy when right clicking the mouse

Moving files is the same as cut then paste (copying files is copy then paste).

As other posters mentioned, you can also drag and drop files and folders from one Nautilus (the file explorer) to another, or you can use the mv command in a terminal.

---

### Post by adventure man on 2009-06-02
Wonderful, thanks for the input guys, I've learned a lot here. :D

Nautilus reminds me a lot of explorer very easy to use, thanks

---

### Post by jonobr on 2009-06-02
Hello

If your going to use terminal to move and copy, I would recommend learning the directory structure and absolute and relative paths.

You can find info on the dir structure all of the place,
[Here]("http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html")
Is a good example.

Once you have that, heres a few basic commands.

pwd - aka print working directory , this will show you where you are in the dir structure

ls  this will list the contents of the directory
ls -l  this will list the contents in a long fashion showing properties
ls -al shows all contents including hidden files

Wherever you are in the dir, enter cd<enter> or cd ~ this will bring you to your home directory
(~ = home directory for the user you are.

cd.. brings you up a directory  
cd ../.. will bring you up two directories.
and so on,

Now for relative and absolute pathnames

Imgagine you are in your home directory , 
to get to your home desktop from there you could

cd /home/myhome/Desktop
or 
cd Desktop

Option one is the absolute pathname where you are designating where to go from the root directory.

The second is relative, where you are designating where to go relative to where you are now.

You could get real fancy using absolute pathnames,
mixing .. with files

eg cd ../../directory/subdirectory 

I.e. go up twice and then into the directory and subdirectory

Using the ~ in a cd a cp (copy) mv (move) 
indicates start from the home direcotry
eg 
cp ~/mystuff   ~/Desktop

This copied the file or directory mystuff to the desktop

Learning all this will make you more confident on the terminal, 
hope it was useful

I enjoyed typing this.........

---

