---
title: "How Do I Install a Package via .tar?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by mulluysavage on 2010-01-10
I'd like to upgrade to the latest ALSA drivers, but in Synaptic what appears is an older one. I went to the ALSA site, to find that what's available are not .deb but .tar.bz2. What's the procedure for installing this?

---

### Post by sahabcse on 2010-01-10
untar the file then go through the read-me or INSTALL file for installation details.

mostly we follow below steps

open the terminal 

sudo apt-get install build-essential
tar -xvjf packagename
cd packagename
./configure
make 
make install

For install binary package we need to install build-essential first

---

### Post by mulluysavage on 2010-01-10
When I enter "configure" it says "no such command or directory" which is strange because I can see it when I enter "dir"

---

### Post by mulluysavage on 2010-01-10
sorry - I thouht "./" stood for the directories it was in, I now realize you have to make it part of your command, so that is working for me.

---

