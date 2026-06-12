---
title: "Virtualbox"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Mr. Sir on 2010-07-09
Need help in choosing which Virtualbox version to install from the packet manager.

---

### Post by howefield on 2010-07-09
There are two editions, one is the OSE version installable via Synaptic Package Manager, (Open Source Version) and is fine unless you want USB support in which case you'll need to download the PUEL version (Personal Use and Evaluation Licence) from virtualbox.org

The benefits to using the PUEL version are outlined here, if they do not apply to you, then use the OSE version.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by Mr. Sir on 2010-07-09
> **howefield said:**
> There are two editions, one is the OSE version installable via Synaptic Package Manager, (Open Source Version) and is fine unless you want USB support in which case you'll need to download the PUEL version (Personal Use and Evaluation Licence) from virtualbox.org

The benefits to using the PUEL version are outlined here, if they do not apply to you, then use the OSE version.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)
Hi,
Thanks for the link.  It helps to understand more about it.
However, what I'm really trying to understand, is which one of the choices available in the packet manager do I check?  My CPU is an Intel 3.4 Ghz Prescott processor with 2 GB of RAM.  Is one of the 386 choices the right one?
From what I can see, my choice would be between the 'virtualbox-ose-modules-386 or the 'virtualbox-ose-guest-modules-386.  Am I understanding this correctly?

---

### Post by bacardiandwatermelon on 2010-07-09
i386 for 32bit ubuntu, AMD64 for 64bit ubuntu. I wouldn't use the ose version as it can't detect flash drives...

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by migs73 on 2010-07-09
I have the PUEL version as the USB capabilities are very handy.
According to the Ubunutu Software Centre (I have forgotten what the corresponding thing was called in Hardy) in 10.04 the corresponding Synaptic package is the virtualbox-ose-qt.

---

### Post by steveneddy on 2010-07-09
Install VirtualBox from the web site - that is what the other poster <snip> was telling you - the ose version is difficult to work with and you really want to version from the web site.

Here is an easy way to perform that task by using your terminal - and it will update with all of your other software through Update Manager.

Install the ppa so it will update easily:

Here's a link to the instructions:

[http://www.unixmen.com/linux-tutorials/995-install-virtualbox-from-ppa-repository-in-ubuntu-lucid-lynx](http://www.unixmen.com/linux-tutorials/995-install-virtualbox-from-ppa-repository-in-ubuntu-lucid-lynx)

There you go - simply three terminal commands:

```
sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian lucid non-free"
```

then

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

and finally

```
sudo apt-get update && sudo apt-get install virtualbox-3.2
```

Easy peasy

---

