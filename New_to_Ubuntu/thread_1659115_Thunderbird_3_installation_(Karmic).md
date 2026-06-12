---
title: "Thunderbird 3 installation (Karmic)"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by amaumau on 2011-01-03
Hi,

I've been trying to install Thunderbird 3 under Karmic Koala in two ways. None of them worked.

1) I'm typing three commands:

```
$ sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
$ sudo aptitude update
$ sudo aptitude install thunderbird-3.0 thunderbird-3.0-gnome-support
```

and get the error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
[B]No candidate version found for thunderbird-3.0
Couldn't find any package whose name or description matched "thunderbird-3.0-gnome-support"
No candidate version found for thunderbird-3.0
Couldn't find any package whose name or description matched "thunderbird-3.0-gnome-support"[/B]
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

2) I'm adding the lines

```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
```

to **/etc/apt/sources.list**

Then I'm typing

```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
$ sudo apt-get update
$ sudo apt-get install thunderbird-3.0 thunderbird-3.0-gnome-support
```

and I get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package thunderbird-3.0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird-3.0 has no installation candidate[/B]

```

What's wrong?

Thanks in advance!

---

### Post by davidmohammed on 2011-01-03
dont think thunderbird 3 is available through that repository for Karmic.  Suggest remove that repository and use the instructions in the forum sticky [here]("http://ubuntuforums.org/forumdisplay.php?f=251") or possibly  [ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") repository instead.

---

### Post by Crazedpsyc on 2011-01-03
Get the latest version: [http://download.mozilla.org/?product=thunderbird-3.3a1&os=linux&lang=en-US](http://download.mozilla.org/?product=thunderbird-3.3a1&os=linux&lang=en-US)
and installing it is as simple as extracting it. (right-click on the file, extract here) then open the folder and double-click on the file called "thunderbird"
Just be aware that that version is the "bleeding edge" alpha version. For a more stable version, go here:
[http://download.mozilla.org/?product=thunderbird-3.1.7&os=linux&lang=en-US](http://download.mozilla.org/?product=thunderbird-3.1.7&os=linux&lang=en-US)

---

### Post by spillage2 on 2011-01-03
Have you tried claws email..

I find it much better than thunderbird and have used it for quite a while..

---

### Post by amaumau on 2011-01-04
Thank you for your answers.

> **davidmohammed said:**
> dont think thunderbird 3 is available through that repository for Karmic.  Suggest remove that repository and use the instructions in the forum sticky [here]("http://ubuntuforums.org/forumdisplay.php?f=251") or possibly  [ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") repository instead.

Davidmohammed, I didn't find an answer to my question in that forum sticky, but I added the ubuntuzilla repository and installed Thunderbird (Shredder)! Will see how it works now.

> **Crazedpsyc said:**
> Get the latest version: [http://download.mozilla.org/?product=thunderbird-3.3a1&os=linux&lang=en-US](http://download.mozilla.org/?product=thunderbird-3.3a1&os=linux&lang=en-US)
and installing it is as simple as extracting it. (right-click on the file, extract here) then open the folder and double-click on the file called "thunderbird"
Just be aware that that version is the "bleeding edge" alpha version. For a more stable version, go here:
[http://download.mozilla.org/?product=thunderbird-3.1.7&os=linux&lang=en-US](http://download.mozilla.org/?product=thunderbird-3.1.7&os=linux&lang=en-US)

Crazedpsyc, would this really be a full installation of the program with all the integrations in my OS? Sorry if I say something inappropriately.
Anyway, I managed to install Shredder now; what do you think, is it unstable or unsafe?

> **spillage2 said:**
> Have you tried claws email..

I find it much better than thunderbird and have used it for quite a while..

Spillage2, I will try using Claws email if Shredder doesn't work well for me.

---

### Post by Crazedpsyc on 2011-01-04
It would integrate as well as installing it through the repository, but you still have to get the Ubuntu integration addon (just search "ubuntu" on [https://addons.mozilla.org/](https://addons.mozilla.org/)) for it to integrate with the Me Menu (the mail icon in the panel), but you have to do that either way. 
Btw, I do recommend the Alpha version, as I use it and it is stable enough for me. It has amazing graphical improvements!

---

