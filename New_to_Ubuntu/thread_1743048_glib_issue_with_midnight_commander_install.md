---
title: "glib issue with midnight commander install"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Musicality on 2011-04-29
I'm brand new to the forums and Linux, but I have done some searching around and can't find anything that seems directly related to my issue. I made an attempt to install midnight commander from source (tar.gz) and got to the ./configure command. I received the following error after running that command:

checking for GLIB - version >= 1.2.6... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Test for glib failed.
GNU Midnight Commander requires glib 1.2.6 or above.
 
I did the Ubuntu 10.04 LTS install probably less than a month ago via download to cd from the website, and a search of my system (for 'glib') reveals a good number of files with the "glib" label attached. My understanding is that is unlikely that I actually lack glib. Just to be clear, I'm more interested in learning about this install process and what glib is doing than I am about actually getting the program installed (so if there is an easier way to get the program, that'd be great to hear about, but I also want to deal with the issue with glib for learning purposes). 
   I have no idea what PREFIX is, so just some basic help would be wonderful! I don't mind working through the problem without a hand-holding, but at least a push in the right direction would be great. Thanks all!

---

### Post by oldos2er on 2011-04-29
I'm guessing you need to install libglib2.0-dev, a development library for Glib.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

