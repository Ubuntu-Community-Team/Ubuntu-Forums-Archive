---
title: "Why are my text files considered &quot;executable&quot;?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-05-16
I am transferring some text files from Windows to Linux.  Ubuntu says that the text files are executable, but clearly they aren't.  It then gives me three options to display, run in terminal or execute.

I just want to open the text files with something like GEdit.  What should I do? Is there some setting somewhere?  It doesn't seem right that I should have to keep clicking "Display"
all the time.

By the way, they aren't batch files or anything, they are just files with text in them. Since they were originally Windows files, they have a .txt extension.

---

### Post by ryan! on 2011-05-16
click display or in terminal ```
gedit path/to/file
```
EDIT: you could just right click on the file then open with your favorite text editor

---

### Post by pricetech on 2011-05-16
Choose the "display" option to open them in your default text editor, probably gedit.

---

### Post by mcduck on 2011-05-16
In Linux any file with the execute permission is considered as executable. No matter if it actually contains anything that could be executed or not.

Just remove the execute permission from the files and you won't get complaints about it any more. (right-click, select "Properties" and on the Permissions-tab unmark "Allow executing file as program".

Another option is to just set Nautilus to always open files instead of executing them. To do that just open a file manager window, go to Edit->Preferences, and on the Behavior-tab set it to "View Executable files when they are opened"

---

### Post by wojox on 2011-05-16
Right click the file go to Properties > Permissions and uncheck the Executable bit.

---

### Post by akand074 on 2011-05-16
> **Learning Linux 2011 said:**
> I am transferring some text files from Windows to Linux.  Ubuntu says that the text files are executable, but clearly they aren't.  It then gives me three options to display, run in terminal or execute.

I just want to open the text files with something like GEdit.  What should I do? Is there some setting somewhere?  It doesn't seem right that I should have to keep clicking "Display"
all the time.

By the way, they aren't batch files or anything, they are just files with text in them. Since they were originally Windows files, they have a .txt extension.

You got some good advice as to prevent such behaviour. If you were wondering, it could be because they are marked by Ubuntu as executable by default not knowing it's content coming from Windows? The reason a text file can be considered executable is that if a .txt file has code in it (a script usually) it can be executed. In ubuntu, by default you don't give it an extension at all and it'll open in gedit unless marked as executable. Set .txt files to open with gedit.

---

### Post by Morbius1 on 2011-05-16
Just curious but what version of Ubuntu are you using? And are you mounting the Windows partition through Places or do you have an fstab entry for this Windows partition.

If you have a older version of Ubuntu and you don't have an  fstab entry it will mount the partition such that all files are executable. New versions of Ubuntu will not.

---

### Post by hsweet on 2011-05-16
None of my .txt files are executable and I don't think any system files are either. 

Anyhow, I finally got annoyed enough to fix it on my computer using find to change all the .txt files permissions 

This should find all the .txt files in your folder
```
find . -name \*.txt
```
Adding this bit will find them and remove all the executable bits off so you can just click and they open.
```
 find . -name  \*.txt -exec chmod 664 '{}' \;

```
664 gives you read and write permissions and everybody else on your computer read.  If you want to be more private, make it 660.

---

