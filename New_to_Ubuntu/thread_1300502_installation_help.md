---
title: "installation help"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by houserparker on 2009-10-25
Hi all,

As an absolute noob to linux and ubuntu i am just starting to get my head around some simple script but in the mean time until i learn more i am having real trouble installing up to date applications rather than installing old errorness apps from ubuntu's repository.

An example is that i am trying to install an up to date version of nicotine+-1.2.14 that i have extracted from the arcive manager to no avail.

The basic sript i have been using is as follows:-

cd /home/ben/Desktop/nicotine+-1.2.14/
,/configure
make
sudo make install

The problem is that when i change directory successfully and then type ./configure it says "no such directory"

Can anybody please help as I have been working on this for weeks and just cant get it to work.

Thanks,

Ben

---

### Post by mapes12 on 2009-10-25
Why compile? Nicotine is in Synaptic.

---

### Post by houserparker on 2009-10-25
I installed nicotine from synaptics but it seemed to be an old version and problematic. The only reason i wanted to take the compilation route was because i cant see any other way of updating nicotine.  Any help would be much appreciated.  Ben

---

### Post by 3rdalbum on 2009-10-25
In the directory that you are switching to, is there a file called "configure"?

The "./configure" bit says "Run a file in this directory called configure". If there is no such file, then you need to navigate to the directory that does actually contain the file. If the file is there, then you will need to make it executable (Right-click, Properties, Permissions, Allow this file to execute).

---

