---
title: "cp omitting directory"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Canime on 2011-03-29
I have a question about how to copy one directory to another. The directory I need to copy is a theme package in the downloads section of my home directory. It has been un-zipped etc, now I need to copy it to ~/.icons directory. The file explorer can't let me view the ~/.icons directory, and when I run the command:
```
sudo cp /home/downloads/theme ~/.icons
```
it says that the directory /home/downloads/theme is being omitted. 

Any way to view these files from the places menu, or copy it using the terminal.

---

### Post by mcduck on 2011-03-29
Couple of things here:

1. Don't use "sudo". you don't need it, you already have the permissions to write stuff in your own home directory.

2. You can easily view hidden files and directories in the graphical file manager by selecting View/Show Hidden Files from the menu. Or by pressing Ctrl-H.

3. You need to use the "-R" option in the cp command to copy a directory and it's contents.

4. /home isn't your home directory. /home/*username* is. So you are probably trying to copy from wrong place.

5. The shell is case sensitive, so ~/downloads and ~/Downloads are two different things.

Assuming the download directory is actually called "Downloads", like it is by default, try this instead:
```
cp -R ~/Downloads/theme ~/.icons
```

---

### Post by Canime on 2011-03-29
That works well, from both the file browser and the terminal. Yeah I will defiantly use Ctrl-H to view hidden files and -R to copy the directory. I think i made the mistake of calling my home directory that just because I wanted to leave out my user name! Thanks a lot!

---

