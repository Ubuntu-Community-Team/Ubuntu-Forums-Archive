---
title: "Does Skype work on 64bit machines?"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-16
Hi

I have uninstalled ndiswrapper because I needed to load a 64bit flash player...because my system crashed all the time when running the repos 32bit version.

I am now trying to run Skype. I am using the repos version. It will not run from the Applications drop down menu but I can get it to run by opening a terminal and simply typing in 'skype'. I get this error reported > bob@bob-desktop:~$ skype
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64


I presume there is a problem because I run a 64 bit machine.

Curiously I can get Skype to work (sort of) but the options selected do not always work as expected. Video in particular seems to be erratic.

Can anybody throw any light on the issue? I would like to get Skype running from the Applications menu, all working as expected.

---

### Post by freak42 on 2009-04-16
first link should work:
[http://www.google.ch/search?q=install+skype+64+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ch/search?q=install+skype+64+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by bwallum on 2009-04-20
Got there in the end! Thank you for the steer! 64bit skype now installed although it may just be a 32bit version with it's own 64bit 'wrapper'.

What I discovered is that when you load skype from the repos it also auto loads skype-common. This leads to problems such as the skype sounds are heard but the application windows are not started and other such erratic behaviour.

This is what I did to get it working. First COMPLETELY remove skype (or skype-static and skype-oss) and skype-common using System>Administration>Synaptic Package Manager (search for skype).

I downloaded the 64bit file directly from skype with```
wget http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb
```

Then ```
sudo dpkg -i skype_ubuntu-2.0.0.72-1_amd64.deb
```then ```
sudo apt-get -f install
```

It worked. I don't run ndiswrapper (the wrapper that allows 32bit programmes to run on 64 bit systems) any more and have not tested the above solution with ndiswrapper installed. Note that if you remove ndiswrapper you will need to look at installing 64 bit versions of flash (the new 64bit beta works ok) and possibly other programmes such as java.

---

### Post by lisati on 2009-04-20
Thanks from me too.

---

### Post by lduvall on 2009-04-25
I followed the above this morning on a fresh install of 9.04 and it works "as advertised". Thanks!

---

### Post by Dougie187 on 2009-04-25
Couldn't you just add the medibuntu repositories and then sudo apt-get install skype?

At least thats what I did.

---

