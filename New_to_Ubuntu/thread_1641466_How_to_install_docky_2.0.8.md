---
title: "How to install docky 2.0.8"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-09
So i would like to learn how to install docky from the file I downloaded. I understand i can get it in the software center, or even add the PPA to do it, but i would like to know how to install it from the tar file i downloaded from launchpad for experience.  Thank you

[https://launchpad.net/docky](https://launchpad.net/docky)

---

### Post by hellblazer on 2010-12-09
I've had a look at the download and it seems a very nice install script has been included, so this is all you'll need to do:
[LIST=1]
[*]uncompress the files to a location of your choice
[*]got to the uncompressed files and run ```
sudo chmod +x install.sh
``` this will make the install script executable
[*]run the install script ```
./install.sh
``` this will execute the script. You will probably get howto use output, just follow the instruction and you should be good to go
[/LIST]
Hope that help, post updates if you're still stuck

---

### Post by karthick87 on 2010-12-09
Step 1: untar the file
```
tar -zxvf docky-2.0.8.tar.gz
```

Step 2: Give execute permission
```
chmod +x install-sh
```

Step 3: Configure it
```
./configure
```

Step 4: Install it
```
make install-sh
```

---

### Post by hellblazer on 2010-12-09
thanks karthick87, thats a much better route to follow as it will probably actually work ;)

---

### Post by jcaplette on 2010-12-09
Try this solution, it's from the Docky wiki, I installed it with those commands:

```
sudo add-apt-repository ppa:docky-core/stable
sudo apt-get update
sudo apt-get install docky
```

---

### Post by karthick87 on 2010-12-10
@jcaplette he wants to install it from tar for learning purpose.

---

### Post by tora201 on 2010-12-28
can't install here from tar.
./configure gives an error at the end:


checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gapi2-fixup... no
configure: error: No gapi post-processor found

And, I can't install from the PPA either. Well, I can, but then I don't get any Helpers. Have yet to figure this one out. The reason I want the latest version is so I can get my hands on the Skype helper in particular. It is missing from 2.0.7  Even if I could install Skype Helper by itself that would be acceptable....

Any ideas??

---

### Post by KaYnemO on 2010-12-28
Upgraded to 2.1.0 Everything works !!!

---

### Post by tora201 on 2010-12-29
care to tell us you did that? PPA? I am having trouble with PPAs - missing helpers after install. Always have to revert back to repository version. :-(

---

### Post by hunter99507 on 2010-12-29
> **tora201 said:**
> care to tell us you did that? PPA? I am having trouble with PPAs - missing helpers after install. Always have to revert back to repository version. :-(

You should be able to add the docky PPA using terminal

```
sudo apt-get-repository ppa:docky-core/stable

```Then run an update.

```
sudo apt-get update
```Then install

```
sudo apt install docky
```Or you can find it in Synaptics or the software center.

---

### Post by tora201 on 2010-12-29
yeah I know. But I get some error about a dependency it can't install. (Forgot what it was now). I am sticking with 2.0.9 in the meantime (that worked). But still no skype helper. Any ideas?

---

