---
title: "Linksys USB on Ubuntu 6.10 (Please..)"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by m|sha on 2007-02-05
Alrighty, I'm sure everyone is sick of hearing the same questions over and over about these USB NICs.. But yeah I haven't made any progress in three days (With the exception of finding the INF file I need).

Here's what I've done so far..

**1.) I found the INF file I need for my driver **
(I'm pretty sure it's rt73.inf)
**2.) I've checked to see if I have ndiswrapper already installed... And I don't.**
I did this by opening the terminal and simply typing "ndiswrapper" (no quotes) and it said "command not found". I also went *to Administration > Syntec Package Manager *(<-- I forget what it's called) and I checked to see if it was there (It wasn't)
**3.) I downloaded the latest version of ndiswrapper from SourceForge (1.37) on my Windows system and copied it to my USB Drive.**
Downloaded it from here: [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148)
**4.) I logged in as root**
**5.) I copied  ndiswrapper-1.37.tar.gz from my USB Drive to my /home directory on Ubuntu**
**6.) I extracted it to the current directory**
**7.) I opened the Terminal and navigated to the directory where the files were extracted to**
**8.) I ran the following commands:**
[FONT="Courier New"]
make distclean
make
sudo make install
[/FONT]

The first "make distclean" worked.. The others I got a bunch of errors. A BUNCH.

I know I'm supposed to install Linux headers or something.. But I can't do that without an internet connection on Ubuntu!


ANY help at all is appreciated please.... I'm new to Linux and I'd really just like to get my internet up and running.. Thanks

MISHA

---

### Post by renzokuken on 2007-02-05
you'll have to get the linux-headers package from somewhere else, perhaps a friend with a net connection, i dont think the file is big, copy them to your pc and install them first.

then run ndiswrapper.

---

### Post by m|sha on 2007-02-05
Ok, I installed Linux headers from the Ubuntu website for Edgy:
linux-headers-2.6.17-10_2.6.17-10.33_i386.deb

I started Ubuntu and logged in as root.

I clicked the package and installed it..
I attempted to install ndiswrapper and I'm still getting a bunch of errors..

Did I download the wrong file?

Most of the errors I got were saying invalid file or directory
and also errors dealing with lines of codes and stuff in the files..

(I'm running with PIII just so yeh know)

---

### Post by renzokuken on 2007-02-05
ok, sorry, forgot to mention earlier, you will need to install the build-essential package if you are compiling from source.

```
sudo apt-get install build-essential
```

---

### Post by m|sha on 2007-02-05
Sorry I know I'm such a noob.. Heh thanks for bearing with me. Uh.. This is the error I got when I ran that command:

> **misha@misha-desktop:~$ sudo apt-get install build-essential**
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by renzokuken on 2007-02-05
hehe......tis ok, you need to enable the universe and multiverse repos.

you can either do this in Synaptic's settings, or

```
sudo gedit /etc/apt/sources.list
```

and uncomment (remove the # from the front of the line) the repos (the lines that go "deb [http://ubuntu.etc.etc.etc](http://ubuntu.etc.etc.etc) blah") for multiverse and universe (it will make sense when you see the file.

then run

```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by Mavvy on 2007-02-06
Try this method..

[http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/](http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/)

It works well for me.. You need root to build the driver in terminal mode.

After setting the ESSID and running dhclient.. it instant connect to my router.. :lolflag:

---

