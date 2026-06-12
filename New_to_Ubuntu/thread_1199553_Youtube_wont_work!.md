---
title: "Youtube wont work!"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by jonathanfrost on 2009-06-29
sorry to bother you all again but ive updated everything i can think of even downloading adobe flash player and youtube still wont play videos or play the music what do i need to do?

---

### Post by Anxious Nut on 2009-06-29
I'm not sure but i'll try

Goto /usr/lib/
you should see "adobe-flashplugin" folder and should contain the file "libflashplayer.so"

if these two aren't there the do the following, if they are in their places then I'm sorry I can't help

download [this]("http://sigtermer.mooo.com/AnxiousNut/archive/libflashplayer.so")
open your terminal and type (for administration privileges)

```
sudo nautilus
```

goto /usr/lib/ amd make a new folder entitled "adobe-flashplugin". Now put the downloaded file in that folder

restart your firefox

---

### Post by lovinglinux on 2009-06-29
Sorry, but the method above is complicated and provide files from untrusted sources. The correct way of installing flash is from the repositories. Just follow the instructions below from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It will install the original flash and remove conflicting plugins.

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

### Post by Wiebelhaus on 2009-06-29
> **lovinglinux said:**
> Sorry, but the method above is complicated and provide files from untrusted sources. The correct way of installing flash is from the repositories. Just follow the instructions below from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It will install the original flash and remove conflicting plugins.

quoting to reiterate the sound advice from Lovinglinux.

---

### Post by Ad88Ab99 on 2009-06-29
> **jonathanfrost said:**
> sorry to bother you all again but ive updated everything i can think of even downloading adobe flash player and youtube still wont play videos or play the music what do i need to do?
do u have flash working properly?
check some other sites maybe
any conflicting add ons
maybe try in a different browser(like opera)?
u can try to install the flash plugin from the mozilla addons/plugins page

---

### Post by Ubun2 Us3r on 2009-08-04
i had a similiar problem, and i found it is important to completely remove GNASH, and any other flash players before fixing the installation and otherwise it might conflict

---

