---
title: "pidgin 2.5.7"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by ejlal on 2009-06-24
hey guys
i want upgrade to pidgin 2.5.7 so far i downloaded 
pidgin_2.5.7-1~getdeb1_i386.dep
pidgin-data_2.5.7-1~getdeb1_all.deb
libpurple0_2.5.7-1~getdeb1_i386.deb
libpurple-bin_2.5.7-1~getdeb1_all.deb

i got no clue what to do next,ofcoz no need to tell u am new to ubuntu/linux.
first how to remove the older version? 
 wana do this throu command line & yes i know where to find the terminal:D!!
& about the 32/64 bit thing :confused: i cannt  figure which one is mine so here :
Linux TOSHIBA 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux

many thanks

---

### Post by t0p on 2009-06-24
If I wanted to do this, I'd right-click on pidgin_2.5.7-1~getdeb1_i386.deb and select the .deb package installer.  That will tell you what you need to do, methinks.

---

### Post by ejlal on 2009-06-24
i did as u said, and got error about dependency, libdbus-glib-1..2 is needed,so where to get it?!
i deleted pidgin using 
sudo apt-get autoremove pidgin
 do need to do anything more about the removing thing?

---

### Post by eamon63 on 2009-06-24
this is much easier, i think... [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by k3lt01 on 2009-06-24
Open Synaptic, search for Pidgin and uninstall Pidgin and its associated programs (dependencies). after you have done that close Synaptic.

Open the location where you downloaded the GetDeb files, double right click libpurplebin and let it install, you will need to type in your password. After it has installed, close the package installer.
Now double right click libpurple and let it install.
Double right click PidginData and let it install.
Double right click Pidgin and let it install.

I may have the order wrong but it is easy to tell what you need to install if the order is wrong as the package installer tells you what dependency it needs so you install that.

---

### Post by k3lt01 on 2009-06-24
> **eamon63 said:**
> this is much easier, i think... [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)I did that yesterday and it didn't work.

---

### Post by Arup on 2009-06-24
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

If you know how to add repos, this is direct from Pidgin developers and you will always have updated Pidgin on your system.

---

### Post by ejlal on 2009-06-24
> **Arup said:**
> [https://launchpad.net/~pidgin-developers/+archive/ppa]("https://launchpad.net/%7Epidgin-developers/+archive/ppa")

If you know how to add repos, this is direct from Pidgin developers and you will always have updated Pidgin on your system.
this would be mush easier way but i have already removed the older version of pidgin i want to install it again but there is some dependency issues,how can i resolve these??

---

### Post by chrone on 2009-06-24
> **ejlal said:**
> this would be mush easier way but i have already removed the older version of pidgin i want to install it again but there is some dependency issues,how can i resolve these??

try this: sudo apt-get -f install

that should fix your dependencies problem. then try to install pidgin 2.5.7 from [www.pidgin.im](www.pidgin.im) instruction. already tested with lots of hardy and jaunty machines in office, and they worked just fine today. hope there won't be anymore hiccups from pidgin since gaim on 6.06 and 7.04, also kopete on 8.04 still work like a charm to the test.

---

### Post by lazyart on 2009-06-24
Use the PPA instructions and Pidgin will stay updated.  Copy and paste each line into the terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

Then go to System>Administration>Update Manager and it will pull in the new version.

---

### Post by Sef on 2009-06-24
Locked.[ Duplicate Post]("http://ubuntuforums.org/showthread.php?t=1195854").

---

