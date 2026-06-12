---
title: "Synaptic Package Manager unable to Download Package Info"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by maryalesia on 2010-04-06
Hey guys, I'm back again ...

I'm really new to this, so sorry if I'm unclear. 

I just got my OS up and running (9.10 64-bit),and I can't install flash 10. The plug-in in the software center says that it isn't available for my hardware architecture. 

After googling like crazy, I found something about enabling universe-multiverse, and tried doing just that (only to discover that it was already enabled). However, in both synaptic package manager and software sources, I am unable to download package info. I get this error message:
_________________________________________________________________
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  
Some index files failed to download, they have been ignored, or old ones used instead.
___________________________________________________________

Does anybody know what this means, or how I can download flash 10? I'm addicted to hulu, so flash is a necessity.

---

### Post by Temposs on 2010-04-06
It seems like you put in some software source from google. You should remove that from System->Admin->Software Sources

---

### Post by lidex on 2010-04-06
Try this instead:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")

---

### Post by maryalesia on 2010-04-06
> **lidex said:**
> Try this instead:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")


I know this is pathetic, but the instructions in that link might as well be in german. I've got no idea what I'm doing.

---

### Post by maryalesia on 2010-04-06
> **Temposs said:**
> It seems like you put in some software source from google. You should remove that from System->Admin->Software Sources

This fixed my synaptic problem, but I'm still having trouble with flash.

---

### Post by maryalesia on 2010-04-06
> **maryalesia said:**
> I know this is pathetic, but the instructions in that link might as well be in german. I've got no idea what I'm doing.

wait hold on I think I did it ...

just let me try and download from the internet ...

---

### Post by maryalesia on 2010-04-06
> **maryalesia said:**
> wait hold on I think I did it ...

just let me try and download from the internet ...

nope. still no dice.

BTW, I'm doing this from chrome. I tried from firefox, but it didn't work there, either.

---

### Post by maryalesia on 2010-04-06
> **maryalesia said:**
> nope. still no dice.

BTW, I'm doing this from chrome. I tried from firefox, but it didn't work there, either.

1. I feel weird quoting myself this many times
2. I just went back to hulu from chrome, and everything is loading fine, making this a moot point. I don't know it was solved, but I think I got it installed. Thanks for the help!

---

