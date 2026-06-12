---
title: "How do I get a list of all my files?"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-07-02
I wonder whether someone here can help me with a bit of terminal code.

I have a folder in which I have about 500 folders, each of which contains between 1 and 100 files.

I want to create a spreadsheet of the folder names and file names, but obviously, ploughing through them all manually is going to take forever!

So, is there a moderately simple command I can paste into Terminal that will give me the information in text form where I can simply cut and paste it into a spreadsheet where I can then manipulate it as required?

---

### Post by SeijiSensei on 2011-07-02
"ls -R" will recurse an entire directory structure, but the results might not be well-formatted for your task.

If all the files have a common, unique root directory name, you'll probably get better results with the locate command.  Try "locate rootdirname" and see if that helps.  You'll probably want to pipe the results into a file with "locate rootdirname > dirlist.txt".

If you've recently added or deleted files from the directory, run "sudo updatedb" before running locate to refresh the database.

---

### Post by Roger Allott on 2011-07-02
Thanks, but all I'm getting is absolutely nothing. The file dirlist.txt gets created, but there's nothing in it - 0 bytes.

Because there are spaces in the folder names I'm using, the command I've used is 
```
locate "&#65279;/media/SYSTEM/Users/Roger/Downloads/folder/sub folder/next folder" > dirlist.txt
```

And yes, I did run sudo updatedb beforehand.

---

### Post by Matt__ on 2011-07-02
[FONT=monospace]try 
[/FONT]```
ls -R "&#65279;/media/SYSTEM/Users/Roger/Downloads"* > ~/Desktop/Directory_tree.txt 
```or just ~/downloads* if its in the standard downloads directory in your home.

---

### Post by Roger Allott on 2011-07-02
Ah, that gives me a list of files in the Downloads folder within /home.

The folder I need to access is on a different drive (it's my main Windows drive, as it happens).

---

### Post by Matt__ on 2011-07-02
edited for you..should direct you to the detachable media now.
if its still wrong just navigate to the directory and ctrl + L to get the correct path and change the /media/etc etc etc/downloads* part

edit: seems it does need the speech marks for external media on my system to see name spaced titles, but dosnt if I run it in a directory within home.

---

### Post by Roger Allott on 2011-07-02
Thanks.

The only way around this that I can think of is to do cd .. then cd .. then lots of cd commands to get me to the directory I'm interested in, then run "ls -R > filename.txt".

The output is reasonable enough for me to do what I want to do.

---

### Post by Matt__ on 2011-07-02
You could use wildcards to find the directories you want, if you have an idea of their names.
or
The text doc created first lists all upper directories, adapt the command line to search each one in turn to get a more manageable output, but I'm sure theres a better way to make the spreadsheet, cant you just import the text file into open office/libre as a tab delimeted import?

---

### Post by Matt__ on 2011-07-02
Ok found it.

create your text doc of the whole directory tree from the command above.

then in libre calc go to >
Insert / sheet from file

and select your txt doc, and it should give you a better starting point for your spreadsheet than entering everything manually.

(its still going to be a big job lol, but at least all the data will be there to play with)

---

### Post by Roger Allott on 2011-07-02
> **Matt__ said:**
> The text doc created first lists all upper directories, adapt the command line to search each one in turn to get a more manageable output, but I'm sure theres a better way to make the spreadsheet, cant you just import the text file into open office/libre as a tab delimeted import?

Oh yes, that stage is easy. All I need do is to amend the text output by the ls command and then, as you say, simply import it into OpenOffice.

Thanks for your help. I think we've cracked the problem for now.

---

### Post by AlphaLexman on 2011-07-02
Use the '**tree**' command,
```
tree "&#65279;/media/SYSTEM/Users/Roger/Downloads"* > ~/Desktop/Directory_tree.txt
```

---

### Post by hakermania on 2011-07-02
> **AlphaLexman said:**
> Use the '**tree**' command,
```
tree "&#65279;/media/SYSTEM/Users/Roger/Downloads"* > ~/Desktop/Directory_tree.txt
```
Tree is not default....

I would use
```

for i in /media/yourharddrive/any/other/path/*/*/*/*; do echo "$i" >>/home/$USERNAME/log.txt; done

```
where */*/*/* plays as many * as the subdirectories in which you want to search for files and put them into log.txt

---

