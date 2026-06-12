---
title: "ubuntu restricted extras problem"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by USB_NL on 2010-01-04
hi made I my sdcard boot karmic koala
installed adobe flashplugin and moonlight

but i need also to install stuff to watch livestreams mp3 etc

this does not work:
```
sudo apt-get install ubuntu-restricted-extras
```

i get this:

```
ubuntu@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
```

cant find ubuntu-restricted-extras in synaptic package manager

:confused:
any sugestions?

---

### Post by MelDJ on 2010-01-04
.......:tongue:
follow the other posters way...

---

### Post by 3rdalbum on 2010-01-04
> **MelDJ said:**
> you have to add the medibuntu repo. add it by following the steps here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then install the package

No you don't - ubuntu-restricted-extras is in the Ubuntu repositories. You just have to make sure that all the repositories are enabled (in System > Administration > Software Sources, make sure the first four checkboxes are ticked) and then reload the package list by hitting the Reload button in Synaptic.

---

### Post by howefield on 2010-01-04
> **MelDJ said:**
> you have to add the medibuntu repo.

Why ?

What's Medibuntu got to do with ubuntu-restricted-extras ?

[http://packages.ubuntu.com/karmic/ubuntu-restricted-extras](http://packages.ubuntu.com/karmic/ubuntu-restricted-extras)

---

### Post by Soul-Sing on 2010-01-04
afaik this metapackage depends on some commonly used packages in the [COLOR="Red"]Ubuntu multiverse repository[/COLOR], so check if it is enabled....

---

### Post by USB_NL on 2010-01-04
medibuntu did not help to play mp3 nor livestreams

i now have some gstreamer plugins
installed after i tried playing a mp3
and mp3files now work

i'll try other options now

---

### Post by USB_NL on 2010-01-04
> **3rdalbum said:**
> No you don't - ubuntu-restricted-extras is in the Ubuntu repositories. You just have to make sure that all the repositories are enabled (in System > Administration > Software Sources, make sure the first four checkboxes are ticked) and then reload the package list by hitting the Reload button in Synaptic.

all four checkboxes where already ticked

but wen i reloaded got 35 new packages

And now this command line works: 
```
sudo apt-get install ubuntu-restricted-extras
```livestreams are working now :P

thank you it's solved

**Do i need to worry about medibuntu** i did copy pasted that command line into the terminal

i'm trying to figure out a perfect step by step install for the stuff i need and want

going to system - administration - software sources - then change something and change it back - close - reload : makes it get the essentials packages :)

i now can find vlc in synaptic package manager again for instance

thanks

---

### Post by howefield on 2010-01-04
> **USB_NL said:**
> Do i need to worry about medibuntu i did copy pasted that command line into the terminalthanks

No, you needn't worry about it.

The are a few packages you might find useful there, eg libdvdcss2, w32codecs, (or w64codecs if you run 64 bit Ubuntu) as well as a few others.

You can get rid of the Medibuntu stuff you installed by going into System > Administration > Software Sources, then click on the "Other Software" tab and remove the line which includes Medibuntu, then remove the Medibuntu  authentication key from the Authentication tab. Close your way out, and reload Synaptic Package Manager.  

But as I said, you don't have to, there is no harm leaving the info in your software lists, and potentially some good if you need any of the packages that Medibuntu includes.

For information, you can also download the individual packages from the Medibuntu site, and double click the downloaded file to start them installing. Long time since I added the repository for that reason.

---

### Post by USB_NL on 2010-01-04
> **howefield said:**
> No, you needn't worry about it.

I already got rid of it the way you discribe
Im running a fresh install from winxp on a sdcard presistently
if i get in big troubels i can make a quick new install but for now all feels fine again thanks very much

---

