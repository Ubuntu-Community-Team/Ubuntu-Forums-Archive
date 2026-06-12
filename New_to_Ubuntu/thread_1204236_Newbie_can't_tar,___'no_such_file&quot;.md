---
title: "Newbie can't tar,   'no such file&quot;"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by HawkeyeGuru on 2009-07-04
I'm new to linux.  

    I am trying to tar a downloaded file, but I don't know exactly how to do it.     I've downloaded Stylistic.3400-3500.hardy.tar.bz2'  to my desk top. 

```
root@chris-desktop:~# tar -xjf Stylistic.3400-3500.hardy.tar.bz2
```The reply is:


```
[LEFT]root@chris-desktop:~# tar -xjf Stylistic.3400-3500.hardy.tar.bz2[/LEFT]
    [LEFT]tar: Stylistic.3400-3500.hardy.tar.bz2: Cannot open: No such file or directory[/LEFT]
    [LEFT]tar: Error is not recoverable: exiting now[/LEFT]
    [LEFT]tar: Child returned status 2[/LEFT]
    [LEFT]tar: Error exit delayed from previous errors[/LEFT]
    [LEFT]root@chris-desktop:~#[/LEFT]

```
     [LEFT]

 I think the problem is that the file to be untarred needs to go to a specific place. Is that correct? I've been told took in '/etc/apt/sources.list'   but there is nothing there.  

 Also that there might be something wrong with my repository list.  I don't know what that means.

[/LEFT]
        [LEFT]So,  do I need to put the down loaded file somewhere specific or  what?[/LEFT]

---

### Post by ibizatunes on 2009-07-04
Hello and welcome to linux
What version of ubuntu are you using 9.04 if you are using 8.04 i would say install 9.04 as it will be easy and have more drivers

.tar are not nativate to debain based distro's like this wont 
.deb file are......

you can install .tar files, if you are like

---

### Post by Celauran on 2009-07-04
The error is that the file cannot be found. Are you running tar from your desktop directory?

```

cd ~/Desktop
tar xjf filename
```

---

### Post by scorp123 on 2009-07-04
> **ibizatunes said:**
>  if you are using 8.04 i would say install 9.04 as it will be easy and have more drivers What in the world do "drivers" (that is a Windows terminology!) have anything to do with this??

> **ibizatunes said:**
>  .tar are not nativate to debain based distro's  Only true for software packages, but *.tar archives are used nontheless for backups, moving files around, etc.

---

### Post by Nautilus112 on 2009-07-04
You have to specify where you have downloaded the file with 
cd Desktop
then write your codes to extract it and so on.

---

### Post by scorp123 on 2009-07-04
> **HawkeyeGuru said:**
>  I think the problem is that the file to be untarred needs to go to a specific place.  The problem is precisely what it says: "tar" can't find the file you're talking about. Can you please verify e.g. with "ls -al" that this *.tar.bz2 file really really is there? I'd say it's not. So you either have to use the "cd" command and go to the location where you stored that file. Examples:
```
cd ~/Desktop
cd /path/to/download/location
cd /home/yourusername/tmp/
cd /what/ever 
```

... And then repeat the command from there.

Or you change the command to include the path right away:
```
tar -xjf /path/to/where/you/downloaded/this/Stylistic.3400-3500.hardy.tar.bz2 
```

> **HawkeyeGuru said:**
>  my repository list.  I don't know what that means. Linux distributions that are based on Debian GNU/Linux such as Ubuntu, Mint, Knoppix, Sidux, and many others have so called "software repositories". These are server locations where the software that particular server is offering is stored. So on such a distribution you don't need to hunt for "SETUP.EXE" files and then click your way through some brain-dead installer program ... You just tell your package manager what you want and it checks with the repositories from where it can download the stuff you want + all the dependencies that are needed to satisfy the functioning of the program in question. So let's suppose you wanted to install the new Firefox 3.50, so you'd simply tell your package manager to go, fetch it for you and and install it:
```
sudo apt-get install firefox-3.5
```

The config files for those repositories (the list telling the package manager which program can be found on what server...) are in these locations:

[LIST]
[*]/etc/apt/sources.list
[*]/etc/apt/sources.list.d
[/LIST]

The first one (/etc/apt/sources.list) is a text file and ships per default with Ubuntu. The second one (/etc/apt/sources.list.d) is a sub-directory and is empty per default. So if you wanted to add more software repositories you'd download the *.list file from the makers of the software and put it into that sub-directory. Update your repos, and voila, you can install the software from there.

Let's suppose I wanted the repository from Opera, the guys in Norway who make this super-duper cool web browser. So I'd create a file called "opera.list" containing these lines:

```
# Upstream Opera
# wget -O - http://deb.opera.com/archive.key | apt-key add -

deb http://deb.opera.com/opera etch non-free

```

The first two lines are comments. I usually add comments that contain information on how to obtain the repository keys (some software needs a crypto key or else the package manager will complain when you try to install software from there!). So to obtain the keys for Opera's software I'd do what the comments say up there:
```
 wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
``` ... Voila, this would add the keys.

Now I just need to copy that "opera.list" file into /etc/apt/sources.list.d :
```
sudo cp /path/to/file/opera.list /etc/apt/sources.list.d/
```

... and trigger an update:
```
sudo apt-get update
```

And after this I can install the Opera web browser and Ubuntu's update manager will be so kind and inform me whenever there is a new release:
```
sudo apt-get install opera
```

So this is how software repositories are supposed to work.

If someone is telling you that "something isn't right with your repo" then they mean to tell you to check the "sources.list" file and the contents of the /etc/apt/sources.list.d sub-directory .... Sometimes people get the syntax in those list files wrong or there is a typo in the server name or something like that.

I hope this posting was helpful, despite its length :D

---

### Post by HawkeyeGuru on 2009-07-04
Thanks Every one,  especially scop123.  It was simply that I wasn't in the correct directory.  Seems simple now.

---

