---
title: "How to extract rar files?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by henel on 2009-08-15
Guys
I can't open rar files.  I have loaded unrar through Synaptic.  But what to do next?
I clicked on the files.  It sends me to archive.  I clicked extract.  after that displays: "extraction completed sussessfully" and two options: Open the distination or Close.
Any clicks and nothing happened. I am totally confused!

Thanks

---

### Post by coldReactive on 2009-08-15
```
sudo apt-get install unrar
```

in terminal and then install xarchiver, then open the RAR by double clicking it.

---

### Post by whitethorn on 2009-08-15
Sometimes I use the terminal to extract .rar files.  You need to install unrar, then cd to the folder your file is in and 

```
unrar e filename
``` 

I think the "e" is for extract, you can look at the options for unrar in the man pages.  

```
man unrar
```

---

### Post by wgarciamachmar on 2009-11-22
Thanks. Had the same problem, and it worked, except that i can't get xarchiver to open the files by simply double clicking them. I can't get it to be the default "opening app".

---

### Post by sldavid on 2009-11-22
I'm able to use the command line or right-click the rar file in Nautilus and choose extract. It will even prompt for a password if necessary.

I installed unrar 1:3.93-1 (Unarchiver for .rar files non-free version) using Synaptic. To find the file just type unrar in the toolbar quick search field at the top of the Synaptic window.

Note: In the process above Synaptic also revealed an additional unrar package call 'unrar-free' but I get much better results from the non-free version. The free version had difficult extracting some archives.

---

