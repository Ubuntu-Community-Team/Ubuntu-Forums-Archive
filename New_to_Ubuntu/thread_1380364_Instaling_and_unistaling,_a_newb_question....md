---
title: "Instaling and unistaling, a newb question..."
date: 2010-01-13
forum: New to Ubuntu
---

### Post by User X on 2010-01-13
When I install software I see that it often needs dependencies, and I understand this, however I notice when I mark something for removal, it only seems to remove the one component and leaves the dependencies behind.  I realize that none of the components are very large, but do I need them after the software I was using is gone?  Is there a way to remove the selected program, and all the dependancies it installed when it was added to the system?

---

### Post by DestructionsRightHand on 2010-01-13
man aptitude
sudo aptitude --purge-unused
file 
remove unused files

---

### Post by mk1w86 on 2010-01-13
```
sudo apt-get autoremove
```

will also remove uneeded packages. ;)

---

### Post by DestructionsRightHand on 2010-01-13
not exactly related but

sudo aptitude update
sudo aptitude full-upgrade

will help keep packages up to date and clean

---

### Post by Sef on 2010-01-13
Some dependencies of one program are used by another program as well; hence, they will stay installed.   Not true of all depencies.

---

### Post by User X on 2010-01-14
Thank you.  This is very useful!

I will be quite honest I have not placed a lot of thought behind this portion of the response, but if these commands purge the unused packages, why is it not run by default after synaptic removes something?  Thanks again.

---

### Post by nothingspecial on 2010-01-14
Because a dependency of something maybe a useful package in it`s own right that you do not want removed.

For example get-iplayer depends on ffmpeg and mplayer. I might want to remove get-iplayer but keep those 2 around.

---

### Post by Cheesemill on 2010-01-14
This is why I use aptitude instead of apt-get.
By default aptitude removes all unneeded dependancies when you do:
```
aptitude remove <packagename>
```
I believe this only works if you used aptitude to install the package in the first place though.

---

### Post by Rex Bouwense on 2010-01-14
Run computer janitor and it will remove unneeded dependencies at least it did for me when I installed and then later uninstalled programs that I thought I needed.  It will also offer you the option of uninstalling old and unsupported programs.  You can pick and choose which you want to zap.

---

### Post by audiomick on 2010-01-14
> **Rex Bouwense said:**
> Run computer janitor and it will remove unneeded dependencies...

But keep an eye on what it wants to throw out.;)

I have read in various threads that it still sometimes wants to get rid of things that you should actually keep. Having said that, I have run it on my machine without problems.

---

### Post by Rex Bouwense on 2010-01-14
You are right on Audiomick.  Janitor wanted to uninstall a program that I needed to run my old printer and I have to uncheck it everytime I run it.  BTW what is an Australian doing in Germany?  Just kidding.

---

### Post by audiomick on 2010-01-14
> **Rex Bouwense said:**
> .. what is an Australian doing in Germany?  
looking at the Ubuntu forums!;)
Came here 14 years ago, and I'm not "finished" yet...

---

