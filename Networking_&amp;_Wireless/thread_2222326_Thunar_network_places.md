---
title: "Thunar network places"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by LastDino on 2014-05-06
After installing samba and adding user profile to it and sharing files between both my Xubu and friends W7 computer, they do not appear for either of us.

[ATTACH=CONFIG]252905[/ATTACH]


This is what I see. Am I suppose to install something else? I found some similar old thread here
[http://ubuntuforums.org/showthread.php?t=1891590](http://ubuntuforums.org/showthread.php?t=1891590)

But when I entered first command in OP.

> glen@Maxwell:~$ sudo apt-get install samba smbfs smbclient fusesmb gvfs-backends[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cifs-utils

E: Package 'smbfs' has no installation candidate


I got this error, just though it is better to ask around before I did anything beyond, so here I'm, how do I deal with this? :o

---

### Post by jbaerboc on 2014-05-06
Sounds like the package smbfs is missing. It does seem to say that cifs-utils is supposed to replace it and so it shouldn't matter but I would try "sudo apt-get install smbfs" in the terminal or use Synaptic Package Manager to install it. See if it tells you it's going to remove cifs-utils if you proceed or if it just installs. If it does just install I would say reboot and try it again. I don't use windows networking [samba] much myself so just throwing out thoughts ;-).

---

### Post by LastDino on 2014-05-06
> **jbaerboc said:**
> Sounds like the package smbfs is missing. It does seem to say that cifs-utils is supposed to replace it and so it shouldn't matter but I would try "sudo apt-get install smbfs" in the terminal or use Synaptic Package Manager to install it. See if it tells you it's going to remove cifs-utils if you proceed or if it just installs. If it does just install I would say reboot and try it again. I don't use windows networking [samba] much myself so just throwing out thoughts ;-).

I had already did that, but I did it again just to post the thing 

> 
glen@Maxwell:~$ sudo apt-get install smbfs
[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cifs-utils

E: Package 'smbfs' has no installation candidate

And there is nothing in synaptic by name of smbfs but when searched it shows smb4k which I've already installed...

---

### Post by LastDino on 2014-05-09
I dunno, I tried lot of things here and one of them was to install different FileManager and see what it did with Networkplaces. And the error remained same. Then I went ahead and tried connecting different Window PC and somehow it worked. I'm lost tbh. But I'll mark this as solved as it doesn't seem to be problem related to Thunar specifically.

---

