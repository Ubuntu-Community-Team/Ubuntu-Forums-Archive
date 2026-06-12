---
title: "Help understanding solution to 9.10 problem"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Jessicaski on 2009-11-04
I have a problem with my speakers and below is a long to the post that says how to fix it...

[http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

But I am VERY new to this (installed today) and don't understand what it means.  I don't understand what it menas by "commenting out"  Please help!!!

---

### Post by LunaticHiatus on 2009-11-04
basically, you go into terminal and type in 

sudo gedit

then you go to "file" then "open" in gedit.

then you go to "file system" (its under places on the left). then you go to the etc folder, then the modprobe.d folder, then look for a file called asla-base.conf and double click on it.

It will have a bunch of text of what looks like nonsense. but your going to go to the last line and put a # symbol at the beginning of the last line. after you do that, you will save and reboot.

they call putting the hash symbol (# <- that symbol) commenting out and it basically tells your computer to ignore that sentence.

---

### Post by iansane on 2009-11-04
I have no idea what the problem is but if you say this is how to fix it,

They are saying to open a terminal window by going to applications>accessories>terminal

Then type in the terminal

```
cd /etc/modprobe.d 
```

and then type

```
 sudo gedit alsa-base.conf 
```

When the file opens for edit go to the last line and put ## in front of it.

Thats commenting it out so the system won't read it.

example

```

This line is not commented
##this line is commented

```

I don't have that file so I can't show you the actual line to comment.

---

### Post by desperado665 on 2009-11-04
hit Alt+F2 copy and paste this in the command line:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

after the text editor opens, scroll down to the end of the file and place a # in front of the last line. Don't forget to save the file before exiting.

---

### Post by SunnyRabbiera on 2009-11-04
try to copy and paster commands if they are given, and hope your issue is solved.
Commandline can be scary at first but the linux commandline can copy and paste.

---

### Post by LewRockwell on 2009-11-04
please use "**gksudo**" with GUI applications and "**sudo**" with operations remaining in the terminal and command line

[http://ubuntuforums.org/showthread.php?t=1255407](http://ubuntuforums.org/showthread.php?t=1255407)

.

---

### Post by iansane on 2009-11-04
> **LewRockwell said:**
> please use "**gksudo**" with GUI applications and "**sudo**" with operations remaining in the terminal and command line

[http://ubuntuforums.org/showthread.php?t=1255407](http://ubuntuforums.org/showthread.php?t=1255407)

.

I was about to ask why because that's how I do it but I never really thought why.

You have to check the box "run in terminal" if you use alt+F2 and sudo.

I guess this could cause some confusion.

Thanks for the link so now I too can know why I am doing what I am doing. :-)

---

