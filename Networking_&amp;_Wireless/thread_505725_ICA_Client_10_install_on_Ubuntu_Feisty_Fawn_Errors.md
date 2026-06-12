---
title: "ICA Client 10 install on Ubuntu Feisty Fawn Errors"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by stevesheldon on 2007-07-20
I downloaded the tar.gz file en.linuxx86.tar.gz file, using archive manager to decompress it. I saved it to my home directory, and then tried running the setupwfc file with the command ./setupwfc and I get the following error: 


/home/steve/temp/./linuxx86/hinst: 3595: /home/steve/temp/./linuxx86/echo_cmd: not found

this error is listed several times then the script just hangs.

I have an AMD64 PC with 1Gb ram, running Ubuntu Feisty Fawn for AMD64 architecture.

I am very open to suggestions...

Regards
Steve Sheldon
[email]steve.sheldon@solidlinux.co.uk[/email]

---

### Post by KiloEleven on 2007-07-20
I just installed this like last week. However, I did not use the GUI to uncompress. I saved the tar file to my home folder, then ran
```
tar -xvzf en.linuxx86.tar.gz
``` 
then ran
```
sudo ./setupwfc
```
This allowed the program to run through the installation routine as expected.

---

