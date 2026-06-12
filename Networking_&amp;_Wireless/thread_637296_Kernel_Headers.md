---
title: "Kernel Headers????"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by rightmind on 2007-12-10
I was following the directions form this post found at: [http://ubuntuforums.org/showthread.php?t=192588&highlight=dapper+drake+wusb54g](http://ubuntuforums.org/showthread.php?t=192588&highlight=dapper+drake+wusb54g)

However, when I loaded my cd I found and installed the build essentials, but could not find the "kernel headers".

I have dapper drake and I am trying to connect my linksys wusb54g ver.4.
I have ndiswrapper-1.8 but cannot get the make command to work. PLease help, and ask me question that might help you....and yes I am new.
Thank you.

---

### Post by kevdog on 2007-12-10
sudo aptitude install linux-headers-`uname -r`

Cut and paste that command into the terminal

---

### Post by rightmind on 2007-12-14
ok, I tried that and it read that that it couldn't find the packages???

I used synaptic to load the build essentials and that came with headers it needed...i think?

I have kernel 2.6.15-29-386 in the modules folder.

I am lost here.... please give some detail on to how I can get the make command to work for me so I can install ndiswrapper -1.8.

Thank you ;)

---

### Post by wescrow on 2007-12-21
I think what you need here is gcc-3.4.  Go to synaptic and install this and make should work.

---

