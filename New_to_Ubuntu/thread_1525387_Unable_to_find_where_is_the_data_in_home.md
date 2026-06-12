---
title: "Unable to find where is the data in /home"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by dagarshali on 2010-07-06
HI,
I have lucid lynx 64 bit installed with /home = 56 GB.

I got a message saying I just have 16KB left on /home and that I need to free up some space..

When I used du -sh, i get a total of 56GB..
but when I use the disk usage analyzer, which lists all the directories including the hidden folders, i am not seeing anything that adds up anywhere close to 56 GB. Any help as to find where I might have lost the space or to what I might have lost the space..

Regards,
Vishwa

---

### Post by GreenN00b on 2010-07-06
Use ```
du -h | less
``` and look at the output carefully. This may take a while ...

---

### Post by dagarshali on 2010-07-06
Hi,
I have tried du -h and looked it up.. I don't have 51GB of data. I am not sure where it is..

i checked the disk Usage utility and I looked at it. I have about 11GB of data

Regards,
vishwa

---

### Post by warfacegod on 2010-07-06
Try emptying your Trash as well as root's Trash.

---

### Post by m_kelly on 2010-07-06
The Disk Usage Analyzer will only show you the size of the folders. If I understand correctly, Disk Usage Analyzer is showing you that you have 11GB of folders in /home; if you had a 45GB file in /home, it would not show up in Disk Usage Analyzer, other than in the 56GB size of /home. 

I looked at the man page for du and you may want to try running

```
du -a | sort -nr | less
```

The -a option will list files as well as folders, and sort will put the largest files and folders at the top. The file sizes won't be "human readable", but you should be able to get a good idea.

---

### Post by oldfred on 2010-07-07
Some more commands:

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

---

### Post by KIAaze on 2010-07-07
If you don't mind installing some KDE libraries:
```
sudo apt-get install konqueror konqueror-plugin-fsview
```

And then just open your home folder in konqueror and select the "File size view" option. :)
Looks like this: [http://ubuntuforums.org/showthread.php?t=404485](http://ubuntuforums.org/showthread.php?t=404485)

Tool to find and remove duplicates, empty files, etc:
```
sudo apt-get install fslint
fslint-gui

```

Clear package cache to make space on your / partition:
```
sudo apt-get clean
```

And an extremely useful alias which lists your files and folders by disk usage:
```
alias ducks='find . -maxdepth 1 -mindepth 1 -print0  | xargs -0 -n1 du -ks | sort -rn | head -16 | cut -f2 | xargs -i du -hs {}'

```

---

### Post by laffinet on 2010-07-07
Check your trash: [http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by Paqman on 2010-07-07
> **dagarshali said:**
> 
but when I use the disk usage analyzer, which lists all the directories including the hidden folders, i am not seeing anything that adds up anywhere close to 56 GB.

When you're hunting for mystery junk, it's useful to run the Disk Usage Analyser as root, so that it finds everything regardless of who owns it.

To do this, hit Alt-F2 and run:
```
gksu baobab
```

(Baobab is just the proper name of the Disk Usage Analyser app, gksu is just the GUI equivalent of sudo for command line apps)

---

