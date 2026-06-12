---
title: "Running Softwares"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Himym on 2009-06-07
Hey I have a NFTS harddrive where I have all the softwares I downloaded on Windows. Whenever I try to run them,i get the message:

[/media/DATA/Mina Program/Audacity/audacity.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/DATA/Mina Program/Audacity/audacity.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/DATA/Mina Program/Audacity/audacity.exe or
          /media/DATA/Mina Program/Audacity/audacity.exe.zip, and cannot find /media/DATA/Mina Program/Audacity/audacity.exe.ZIP, period.

Is this because they are not supported by Linux, or because the filesystem is NTFS?

---

### Post by amingv on 2009-06-07
In order to run windows programs in linux, you should install a program called "wine" (which will run some, not all), your computer is trying to open the package as a compressed file (which it thinks it is) so it won't work.

For programs like Audacious, you'll be better off if you install the native linux version.

Both this things you can do with Add/Remove Software in the menu.

---

### Post by Himym on 2009-06-07
Ok, how about drivers? Will Ubuntu detect drivers from windows or do i have to reinstall them all?

---

### Post by whoop on 2009-06-07
There are linux versions or linux alternatives for the programs you where running on windows. Audacity for instance also has a native linux version.
```

sudo apt-get install audacity

```
or start up system-->Administration-->synaptic, search for audacity, mark for installation and apply.
Some software may not have a linux version, there are various places on the internet you can look for alternatives. Example:
[http://linuxappfinder.com/alternatives?page=7](http://linuxappfinder.com/alternatives?page=7)

There is also a chance that you find no useful linux alternative, in that case you can try running the native windows application through wine
```

sudo apt-get install wine

```
then run the windows binary like:
```

wine /pathto/windowsbinary.exe

```

hope this helps.

---

### Post by amingv on 2009-06-07
Ubuntu will detect/install most native drivers by default without you needing to do anything else (a common exception to this being video drivers, and some audio ones), so you wouldn't need to use your windows drivers anyway.

There are some cases in which you would need them (for installing unsupported wifi or network cards, for example) but if your network is working fine then there should be no need.

---

### Post by whoop on 2009-06-07
> **Himym said:**
> Ok, how about drivers? Will Ubuntu detect drivers from windows or do i have to reinstall them all?

You don't use windows drivers to run your hardware in linux. linux has it's own drivers, most of them will be installed by themselves. If you have specific problems with some hardware, you can troubleshoot that on this forum as well.

---

### Post by Ms_Angel_D on 2009-06-07
You might wanna have a look at this page. [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) 

It will help answer some of your Ubuntu Questions.

---

### Post by kwacka on 2009-06-07
Another site that might be useful is: [http://www.medibuntu.org/](http://www.medibuntu.org/)

Some codecs, etc. are not installed automatically due to restrictions in certain countries (mainly the USA).

---

