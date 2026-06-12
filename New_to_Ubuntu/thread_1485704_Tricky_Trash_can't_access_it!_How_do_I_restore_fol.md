---
title: "Tricky Trash: can't access it! How do I restore folder I accidentally deleted?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-17
Pressed delete key accidentally while a folder was highlighted and lost it, because for some reason I can't open Trash and just see its contents.

---

### Post by ENigma885 on 2010-05-18
You can access the "Trash" folder by going to *trash:///* from Nautilus' location bar.

or an easier way to do it is to press *"Alt+F2"* then paste ```
nautilus trash:///
```

---

### Post by Ubunser on 2010-05-18
ENigma, thank you for reply, but that's not the issue. I've been using Ubuntu for a year already so, of course, I would know how to go to Trash. The problem is when I'm opening it it just keeps loading forever. Like this look...

---

### Post by Ubunser on 2010-05-18
I also got to say, yesterday when I got to know the actual place of all files that I delete and went there I saw a huge load of files. I then wanted to delete them finaly but they would appear again after a second on their old place. I tried to do that as root via gksu nautilus but its all the same.
One good news is I could find the precious folder I was looking for :D

But this accident got me angry on Trash and I really seem to want to figure out what's wrong with it.

---

### Post by ajgreeny on 2010-05-19
What happens if you put the "Deleted Items" applet into your panel and click on that?

---

### Post by inigo48 on 2010-05-30
i have the same problem. if i try to reach the trash in nautilus it just loads for a long time then shows nothing. what can be wrong?

---

### Post by ENigma885 on 2010-05-30
@inigo48
I suppose you have deleted many files and/or folders. And unfortunately, Nautilus is not the file manager you can depend on when you have many files in one folder; its loading time is HORRIBLE.  

****You have 2 options here:-**
**1-** You can install another file manager, temporarily, as to access the files in your trash which is the best choice in case you're going to recover multiple files. I recommend PCMan. Installable via ```
sudo apt-get install pcmanfm
``` in a Terminal window (*(Application>>Accessories>>Terminal)*
Then launch it from*(Application>>System Tools>>PCMan File Manager)*
and in its address bar paste ```
~/.local/share/Trash/files
```
**2-** Use command line to access and recover files. In Terminal paste ```
cd ~/.local/share/Trash/files
```
To list the folders and files in there paste
```
ls -a
```
to go in a folder of the list
```
cd FOLDERNAME
```
then copy the files you want to recover
```
cp FILENAME TOWHERE
``` TOWHERE is a folder you want the file(s) to be recovered there.
in case it's a folder that u want to copy
```
cp -r FOLDERNAME TOWHERE
```

---

### Post by inigo48 on 2010-05-30
Thank you for trying help ENigma885! :)

The issue here was a different one. It seem like if I delete files with "invalid encoding" in the filename the trash will be unaccessible until i remove those files from it. It may be a bug.

---

### Post by inigo48 on 2010-05-30
> **Ubunser said:**
> I also got to say, yesterday when I got to know the actual place of all files that I delete and went there I saw a huge load of files. I then wanted to delete them finaly but they would appear again after a second on their old place. I tried to do that as root via gksu nautilus but its all the same.
One good news is I could find the precious folder I was looking for :D

But this accident got me angry on Trash and I really seem to want to figure out what's wrong with it.

i think that your problem is that, you used the "Move to trash" thing in Nautilus so it moved the files back to the trash :) In the Nautilus preferences/behavior/trash choose the "include a delete command that bypasses the trash". this delete command will remove a file permanently. use it on the files in the trash folder.

---

