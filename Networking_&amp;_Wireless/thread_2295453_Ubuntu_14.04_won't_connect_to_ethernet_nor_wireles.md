---
title: "Ubuntu 14.04 won't connect to ethernet nor wireless"
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by atesh_rampersaud on 2015-09-18
Hi there,

I'm new to Linux, and decided to start with Ubuntu.

I recently installed Ubuntu 14.04 on my new rig. However, i found I was not able to connect to the internet through ethernet, nor through wireless.  I'm not exactly sure where to go from here.  Any help would be great.

Thanks in advance!

---

### Post by slickymaster on 2015-09-18
Hi atesh_rampersaud, welcome to the forums.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Hadaka on 2015-09-18
hi, please open a terminal and enter these commands..

```
lspci -n | egrep '0200|0280'
rfkill list all | grep -i yes
```
thanks

---

### Post by atesh_rampersaud on 2015-09-18
Hi slickymaster,

I've attached the .txt file you asked for.

Thanks

---

### Post by atesh_rampersaud on 2015-09-18
Hello Hadaka,

lspci -n | egrep '0200|0280' command gave: 
> lspci -n | egrep '0200|0280'


the rfkill list all | grep -i yes did not give any returns when put into the terminal.

thanks

---

### Post by praseodym on 2015-09-19
Hi,

change the LAN driver according to:

[http://ubuntuforums.org/showthread.php?t=2294501&p=13354331#post13354331](http://ubuntuforums.org/showthread.php?t=2294501&p=13354331#post13354331)

Afterwards install the wireless driver according to:

[http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915](http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915)

---

### Post by atesh_rampersaud on 2015-09-19
Hi,

unfortunately that suggestion did not work. Thanks anyway.

---

### Post by praseodym on 2015-09-20
Did you add the login data of your ISP in your router?

---

