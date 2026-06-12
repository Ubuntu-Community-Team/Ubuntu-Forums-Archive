---
title: "Where do I put these folders?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by lems on 2009-10-31
I've downloaded a few programs such as eclipse, but I have no idea where to put the files. I just have them on my desktop. Is there a proper place to put these programs? In windows, they were put in C:/program files

is there something similar in linux?

---

### Post by jrrader on 2009-10-31
Don't download from http. 
Go to **synaptic package manager**(system>administration>synaptic package manager), **software center**(applications > software center((or add/remove programs if you're not useing 9.10))), or type in **termina**l (applications> accessories> terminal):
```
sudo apt-get install eclipse
```

Doing it this way will insure you get the correct build for your system.  Sometimes you can use .deb packages but they won't always be right for your OS.

---

### Post by Darce on 2009-10-31
If your referring to the .deb install files, you can delete them after you've installed the program
If your talking about files your creating, make a directory under your 'home folder' and put them in there.

---

### Post by lems on 2009-10-31
> **jrrader said:**
> Don't download from http. 
Go to **synaptic package manager**(system>administration>synaptic package manager), **software center**(applications > software center((or add/remove programs if you're not useing 9.10))), or type in **termina**l (applications> accessories> terminal):
```
sudo apt-get install eclipse
```

Doing it this way will insure you get the correct build for your system.  Sometimes you can use .deb packages but they won't always be right for your OS.

package manager has eclipse 3.2. I need 3.5 so I just went and downloaded eclipse from their main site. It gave me a folder with all the files and executables. I was wondering where to put such a file.

> **Darce said:**
> If your referring to the .deb install files, you can delete them after you've installed the program
If your talking about files your creating, make a directory under your 'home folder' and put them in there.

Hmm I'll look into the deb file.

---

### Post by peculiar penguin on 2009-10-31
Typically /usr/local or /opt, not sure which one is better/preferred in Ubuntu.
But as jrrader said, if the repositories have the version you want/need consider installing it from there.

---

### Post by Darce on 2009-10-31
Bizarre.....  my package manager has Eclipse at ver 3.5.1+repack !?

---

### Post by jrrader on 2009-10-31
Applications generally go in /usr/bin  
If you open terminal and type ```
echo $PATH
``` you will see your search path.  This is the path that shell looks in when you give it a command.  Put the file somewhere in the search path and you can call up the program by typing its name in terminal.  /usr/bin contains no folders, they are generally in /usr/lib32 or /usr/lib64.

I just downloaded the eclipse folder I think you are talking about from their website and it does work without compiling it.  So you can probably just drop it in the search path but like Darce said, my software center shows 3.5.1 as well.

---

