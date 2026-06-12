---
title: "How do I install a .deb file?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by todayisgood on 2010-01-17
I don't know how to do this.

---

### Post by Hallvor on 2010-01-17
sudo dpkg -i nameofyourdeb.deb

---

### Post by halitech on 2010-01-17
what are you trying to install? Normally its best to not install random downloads unless you need to. If the program you are trying to install is not listed in Synaptic, to install a .deb file you would open a terminal and run
```
sudo dpkg -i <filename>.deb
```
alternately, you can double click on it

---

### Post by todayisgood on 2010-01-17
> **Hallvor said:**
> sudo dpkg -i nameofyourdeb.deb

That didn't seem to work.

Do I put the full file location name in there?

Name/downloads/whatever.deb?

---

### Post by halitech on 2010-01-17
you need to be in the directory where the file is located in order to install it

---

### Post by lisati on 2010-01-17
> **todayisgood said:**
> That didn't seem to work.

Do I put the full file location name in there?

Name/downloads/whatever.deb?

Just like in Windows, Ubuntu needs to know where to find it. do a "cd" to the directory where the file is first..... (or just put in the full file name)

---

### Post by Hallvor on 2010-01-17
If the file is in your home directory, that command will work. Or else you need to navigate to it.

If you are lazy, just click it.

---

### Post by Kyugetsuki on 2010-01-17
you could just right-click on the file and open it with gdebi package manager(this is by default) if there are dependencies(other nescessary deb files for intsallation), then you can:

1.connect to the *net and let gdebi do the rest
2. get the dependencies yourself

I recommend doing #1, it's less hassle, plus it is a 'while u wait' process, so you can practically do other stuff while the install happens.

---

### Post by todayisgood on 2010-01-17
I actually have a related problem now. Basically what I'm trying to do is install Virtual Box. I had the Open Source version installed (from the Software Center) however since USB pass-through isn't supported I had to get the PUEL release which is a .deb which led me here.

I uninstalled Virtual Box, then just installed the .deb but a message popped up when I installed it saying Error: Conflicts with the installed package 'virtualbox-ose'

Can anyone help me out there?

---

### Post by nick_goodfate on 2010-01-17
to install it just double click on it . to UNISTALL it search for it in synaptic System->Administration->Synaptic and check it for unistall . Or if you have ubuntu 9.10 , open computer janitor System->Administration->Computer janitor . For some reason it suggest you do remove any package you have installed by a .deb file ....8-[

---

### Post by admiralspark on 2010-01-17
sudo aptitude remove virtualbox-ose
or
sudo apt-get remove virtualbox-ose

The second is pretty much guaranteed to work, but out of good habit I use aptitude.

---

### Post by mk1w86 on 2010-01-17
> **nick_goodfate said:**
> to install it just double click on it . to UNISTALL it search for it in synaptic System->Administration->Synaptic and check it for unistall . Or if you have ubuntu 9.10 , open computer janitor System->Administration->Computer janitor . For some reason it suggest you do remove any package you have installed by a .deb file ....8-[

Be careful using System Janitor, make sure you actually want to remove the packages it suggests. ;)

You could run:

```
sudo apt-get autoremove
```

instead to remove unneeded dependencies.

---

### Post by todayisgood on 2010-01-17
Ah it didn't work. I got this:

> Install finished

Failed to install package 'virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb'

TERMINAL:

Selecting previously deselected package libqt4-opengl.
(Reading database ... 140068 files and directories currently installed.)
Unpacking libqt4-opengl (from .../libqt4-opengl_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Setting up libqt4-opengl (4.5.3really4.5.2-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package virtualbox-3.1.
dpkg: regarding .../virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb containing virtualbox-3.1:
 virtualbox-ose-source conflicts with virtualbox
  virtualbox-3.1 provides virtualbox and is to be installed.
dpkg: error processing /home/name/Downloads/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb (--install):
 conflicting packages - not installing virtualbox-3.1
Errors were encountered while processing:
 /home/name/Downloads/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb





---

### Post by happyhamster on 2010-01-17
Get rid of virtualbox-ose-source as well:

sudo apt-get remove virtualbox-ose-source

---

