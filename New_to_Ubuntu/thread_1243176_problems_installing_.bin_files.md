---
title: "problems installing .bin files"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by lfp on 2009-08-18
I am trying to install Adobe Air. I have downloaded the package to my desktop. I go into the desktop directory in terminal and then type:

 chmod a+x adobeAIRinstaller.bin

In response I get:

chmod: cannot access `adobeAIRinstaller.bin': No such file or directory

But I know the file is there - I can see it! Any ideas??

---

### Post by Perfect Storm on 2009-08-18
Are you sure you spelled it correctly and make sure the diffrences in upper and lower case letters?

---

### Post by Katalog on 2009-08-18
That was going to be my suggestion. Commands are case sensitive. It should probably look something more like:

chmod a+x AdobeAIRInstaller.bin

---

### Post by lfp on 2009-08-18
Thanks for the tip on the case sensitivity! Now I have another problem. 

I type:

sudo ./AdobeAirInstaller.bin

Then type my password

Then this pops up:

sudo: ./AdobeAirInstaller.bin: command not found


A related question - does Adobe have a repository so I can just get the software through the usual way?

---

### Post by Perfect Storm on 2009-08-18
It works for me, try copy paste from this, you forgot the case sensitive again. ;)

```

cd ~/Desktop
chmod a+x AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin
```


> A related question - does Adobe have a repository so I can just get the software through the usual way?

Nope - but you can suggest it to Adobe, but I doubt you'll get any responds.

---

