---
title: "Navigating and opening all kinds of files via command line?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by unagimiyagi on 2011-05-10
Hi there,

What is the preferred / most efficient way to navigate the file system?  

For example, I see:  Nautilus, a terminal window, and NERDTree inside VIM.

For text files and source code, I see how I could use NERDTree to open things.  But what if I want to view powerpoint files, pdfs, word documents?  Do the pros constantly switch in and out of Nautilus for all those needs?

I see NERDTree and the terminal, and I can get to my files.  But only on some of them can I actually open them, close them, and return to the terminal.  

The reason I ask this is b/c I am under the impression that seasoned Linux users don't really use Nautilus and gui-based stuff for navigation the file system (and in general except for a web browser maybe).

Any suggestions?  Because it seems to me that alot of the efficiency of using the command line will be lost when I need to view a pdf or ppt or non-text based file.

Thanks

---

### Post by deconstrained on 2011-05-10
It really depends on the task at hand. If I'm going to end up using the command line, i.e. if I'm going into a directory where there's source code, or if I'm going to be editing configuration files with Emacs, I start by opening a terminal. To open documents, pictures, videos etc. I just use Nautilus.

There's no good reason to use only one method; you lose the advantages and conveniences of other methods.

---

### Post by jtarin on 2011-05-10
A two-pane file browser along the lines of Norton Commander (most can be run in terminal)......look in Synaptic and search for commander. Some very good ones there......terminal and GUI.

---

### Post by hreichgott on 2011-05-10
Hi, I use the command line most of the time.
To open any kind of file, type the name of the program you want to use, then the name of the file. like this

heather@Data:~$ evince blah.pdf
(opens a .pdf with Evince, a .pdf viewer)

heather@Data:~$ openoffice blah.doc
OR
heather@Data:~$ libreoffice blah.doc
(opens a Word document with LibreOffice, which used to be called OpenOffice)
I'm pretty sure LibreOffice can open .ppt files. LibreOffice's "Presentation" is a PowerPoint replacement.

To get around the directory structure use cd:

heather@Data:~$ 
(I'm in my home directory)
heather@Data:~$ cd Documents
heather@Data:~/Documents$
(Now I'm in my Documents directory)
heather@Data:~/Documents$ cd ..
heather@Data:~$ 
(Back in the home directory)

At any point, type "ls" for a list of everything in the current directory.

A nifty shortcut for all that typing is tab completion. When I entered "cd Documents", I actually just typed "cd Doc" and hit TAB, and the terminal filled in "uments" for me.

So if you know exactly where a file is, you can type for example:
"libr" TAB "Doc" TAB "wo" TAB "resu" TAB ENTER
and you'll see "libreoffice Documents/work/resume.doc" appear in the terminal, and it will politely start libreoffice and open the file for you.

---

### Post by hreichgott on 2011-05-10
Oh, and if you want the terminal to open a program but still let you use the terminal while the program is open, use &, like this:

heather@Data~$: libreoffice blah.doc &

That will open the program as a separate process, so you can use the terminal for something else.

---

### Post by dcsoldschool53 on 2011-05-10
Sometimes, when I can not remember the name of a program that will open a .pdf file, text, or office file, I will use the gnome-open command. It will open pictures, pdfs, text files, websites and more.

[http://ubuntuforums.org/showpost.php?p=1897940&postcount=1](http://ubuntuforums.org/showpost.php?p=1897940&postcount=1)

I agree with what hreichgott had to say, but I like to add this one little thing. Instead of cd-ing into a directory or folder to open a file, you can also open a file right where you are in the terminal. Just, type the command that you need to open that file and the path/to/it with the files name and extension (if it has one).```
evince ~/PDF/ubuntuhowto.pdf
```

---

### Post by jtarin on 2011-05-10
> **hreichgott said:**
> Oh, and if you want the terminal to open a program but still let you use the terminal while the program is open, use &, like this:

heather@Data~$: libreoffice blah.doc &

That will open the program as a separate process, so you can use the terminal for something else.I think this is the first time,in memory, that I have seen someone use the exclamation "Oh!" in starting a sentence in a forum. I thought I would pass on that observation.:P

---

### Post by unagimiyagi on 2011-05-11
> **hreichgott said:**
> Oh, and if you want the terminal to open a program but still let you use the terminal while the program is open, use &, like this:

heather@Data~$: libreoffice blah.doc &

That will open the program as a separate process, so you can use the terminal for something else.


Thanks alot for the tips!  Since I'm new, I just want to make sure that I learn the right habits first.  If there are any more, keep them coming!

---

