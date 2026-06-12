---
title: "Can't install flash in ubuntu 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by mosmoss on 2009-11-02
Hello,

I just recently installed ubuntu 9.10.  I am new to the linux environment and am just getting used to the change in OS.  

I have been trying to install Adobe flash player but I have run in to a number of problems.

I went to the Software Center and under Adobe Flash plugin it says "Not available for your hardware architecture".

I also tried installing the Ubunutu Restricted Codecs but it said "Not available in the current data".


PLEASE HELP!!!

---

### Post by sledge73 on 2009-11-02
open a terminal & type: sudo apt-get install flashplugin-nonfree
enter your root password & after a minute you'll have flash

---

### Post by wilee-nilee on 2009-11-02
You can get a deb type file from adobe. You should go to software sources in administrative and tick on the extra repositories then either do a sudo apt-get update in a terminal or open synaptic and hit reload then install as suggested the restricted extras and there are several flash players that are native to Linux that people suggest, personally adobe has always worked for me so I use it. You might also install vlc and smplayer which is attached to Mplayer to get more codecs, gxine is another good media player. Here is the link to a debi adobe flash just download it and double click on it and let gdebi install it. [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

---

### Post by kansasnoob on 2009-11-02
> **mosmoss said:**
> Hello,

I just recently installed ubuntu 9.10.  I am new to the linux environment and am just getting used to the change in OS.  

I have been trying to install Adobe flash player but I have run in to a number of problems.

I went to the Software Center and under Adobe Flash plugin it says "Not available for your hardware architecture".

I also tried installing the Ubunutu Restricted Codecs but it said "Not available in the current data".


PLEASE HELP!!!

[B]First make sure the Partner Repo is checked as shown in the next post and then:
[/B]
Run this command:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

```
Then for 32 bit (i386):

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

Or for 64 bit:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w64codecs
```

Be sure to restart Firefox afterwards!

If you encounter any errors copy and paste them here.

---

### Post by kansasnoob on 2009-11-02
Oops I left out something!

Go to System > Administration > Software Sources and click on the Other Software tab. Be sure the partner repo is checked:

[ATTACH]134292[/ATTACH]

---

### Post by mosmoss on 2009-11-02
Thanks alot everyone! The checking of the repo software in the software center was the key.

---

