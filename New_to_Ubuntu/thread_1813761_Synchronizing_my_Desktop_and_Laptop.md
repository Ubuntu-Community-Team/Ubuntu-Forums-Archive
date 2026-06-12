---
title: "Synchronizing my Desktop and Laptop"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by meadhikari on 2011-07-28
I have Ubuntu 11.04 installed on both my laptop and Desktop.

I need to make them look identical in terms of all the application installed and all the configuration files. 

I want to sync files like vim configuration files and the latest score in Armagetron to the latest python library that I have installed in the desktop. 

I do not want to sync all those mp3's and movie files between the systems.

How could I achieve that?
Any software that I could use to achieve that?

Thanks in advance

---

### Post by androssofer on 2011-07-28
> **meadhikari said:**
> I have Ubuntu 11.04 installed on both my laptop and Desktop.

I need to make them look identical in terms of all the application installed and all the configuration files. 

I want to sync files like vim configuration files and the latest score in Armagetron to the latest python library that I have installed in the desktop. 

I do not want to sync all those mp3's and movie files between the systems.

How could I achieve that?
Any software that I could use to achieve that?

Thanks in advance

ubuntu one! :-)

i think.... 

not sure if it could natively do it... is 2 options. sign up to ubuntu one.... open the file browser, go into where the folders are for those files etc and c if u can click the txt box to sync wit ubuntu one... 

or make symbolic links!

```
cd ~/Ubuntu One
ln -s /configurationFilesFilePath/ configsLinkName
```

do tht in both comps. (replaceing the file path with the config files path and the link name to whatever you think is relevant for it) it will link the configuration files into ur ubuntu one folder, which will sync it to ur other computers ubuntu one folder (via the cloud), the links will put the changes into the other config folder. job done :-)

EDIT: note, i've nvr actually done this... all just guess work. tho i might try it for my minecraft saves :-)

---

### Post by meadhikari on 2011-07-28
One problem is that I do not have internet connection in one of the computer. :(

I not only one to sync the configuration files but all the application installed too.

---

### Post by androssofer on 2011-07-28
> **meadhikari said:**
> One problem is that I do not have internet connection in one of the computer. :(

I not only one to sync the configuration files but all the application installed too.

so you want to be able to transfer across your installed apps and their config files? but not all the mp3s etc etc?

wudnt b sure how to do tht...

---

### Post by Paqman on 2011-07-28
> **meadhikari said:**
> One problem is that I do not have internet connection in one of the computer. :(


Are they networked together?

---

### Post by meadhikari on 2011-07-28
Not networked :(

---

### Post by whitethorn on 2011-07-28
Just read that they're not networked. Rsync the whole thing to a usb drive.

I'd use rsync for what you want to do. I think the best bet would be to write a small script and when you want to sync just run it.

Another option is to use a program called unison. Unison is slower than rsync though.  As for synchronizing installed programs, I don't think that's a good idea. Probably be better to sync the local .deb repository and then let apt-get/dpkg/aptiture install/update all the packages.

---

### Post by meadhikari on 2011-07-28
What would the rsync 'ing of the file system excluding the Documents,Videos..... folder do.

Would it be creating a identical system in terms of all the application installed and configuration files?

---

### Post by whitethorn on 2011-07-28
Depending on what you rsync, it would make a copy of everything minus whatever you exclude. It will even keep all the permissions, but if you want to do this then you should do it from a Live CD. Take a look at the manpage for rsync.

---

