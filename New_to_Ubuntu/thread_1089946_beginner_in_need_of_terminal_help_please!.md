---
title: "beginner in need of terminal help please!"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Foster88 on 2009-03-07
Hello!

So of course I'm a beginner/noob. I'm getting acquainted with moving through out my OS Via terminal. I'm having trouble understanding the help options within the terminal. Could I please see an example or few of what one would type to lets say... install a file or move a file etc.I dont think I quite understand what the source and directory are. I'm hoping that this will help me learn to install various themes,and such other graphic/desktop customizations to my OS

Highly appreciate the feed back.

Thanks

---

### Post by avtolle on 2009-03-07
To install a package in the repositories through the terminal do```
sudo aptitude update
sudo aptitude install *name of package you want to install*
```Others will suggest using apt-get rather than aptitude; I started using aptitude "back in the day" and continue with it.

---

### Post by skymera on 2009-03-07
Well i know some terminal commands, but not greatly in depth.
I make some examples, hopefully someone can expand. I use example directorys and file names blah blah :)
Use sudo when moving stuff to places other than your home (or where you dont have write permissions)

Move a file
```
 sudo mv /home/USER/Desktop/file.txt /usr/share/ 
```

Copying
```
 cp /home/USER/Desktop/file.txt /home/USER/Documents 
```

You install a program using APT
```
 sudo apt-get update && sudo apt-get install htop 
```

Install .DEB files
```
 cd /location/of/file.deb
sudo dpkg -i filename.deb 
```

Some basic terminal commands, these you probably will use the most :)

---

### Post by bapoumba on 2009-03-07
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by taurus on 2009-03-07
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by DigiTan on 2009-03-07
In practical terms, what are the advantages of aptitude vs. apt-get?  I've heard aptitude is generally the stronger of the two.

---

### Post by ivanvajar on 2009-03-07
Search for Prentice.Hall.A.Practical.Guide.to.Ubuntu.Linux.Dec.2007.pdf on the web. It's a great Ubuntu book.

---

### Post by ekaqu on 2009-03-07
> **Foster88 said:**
> I'm having trouble understanding the help options within the terminal. Could I please see an example or few of what one would type to lets say... install a file or move a file etc.I dont think I quite understand what the source and directory are. 

the mv command moves a file to a new location and can also change a file.

```
 mv file1.txt file.txt 
```  This basically just renames the file file1.txt to file.txt

```
mv file.txt ~/Desktop
```
this moves the file.txt to the user's desktop.

```
cd ~ 
```
this changes your dir to the user's home dir.  

For installing files, that depends on what the file is.  If you want to install a program, you should first look if the repositories have it and use a command like:
```
 sudo apt-get install jedit 
```
This will install the program jedit.

if you have a .deb file, to install normally you type
```
sudo dpkg -i filename.deb 
```
This will install the filename.deb file

If you are given a program's source, the README file should normally tell you how to install, so read that then follow what is said there.

---

### Post by presence1960 on 2009-03-07
> **Foster88 said:**
> Hello!

So of course I'm a beginner/noob. I'm getting acquainted with moving through out my OS Via terminal. I'm having trouble understanding the help options within the terminal. Could I please see an example or few of what one would type to lets say... install a file or move a file etc.I dont think I quite understand what the source and directory are. I'm hoping that this will help me learn to install various themes,and such other graphic/desktop customizations to my OS

Highly appreciate the feed back.

Thanks

Download this and extract it. These are instructions for basic maneuvering and file operations in terminal. There are exercises at the end of each "lesson" to make sure you got it right. The name of the document is quaint but it helped me immensely with terminal.

---

