---
title: "Gnome Commander, Mass Uninstall, Partitions and other things."
date: 2009-11-06
forum: New to Ubuntu
---

### Post by kooboo on 2009-11-06
Hello everyone ):P

I've just crossed the Patience-For-Windows threshold and decided to try something new :)

1) Since I've always been working with Norton Commander like programs (Windows Commander and Total Commander later) and I'm very used to it. All the My Documents, Desktop, My Pictures folder structures are arch-enemies to what I call "tidy HDD". I want to install Gnome Commander... and I don't know how :cry:

There's installation instructions down there in the folder, but using them in Terminal won't work (or I'm doing something wrong). No .exe or .bat files makes former Windows user (me) confused.

2) I'd like to uninstall all games *en masse*. I've uninstalled some one by one, but it's annoying to do so in such way. Is there a way to remove more than one application at once?

3) Partitions. I used to divide my hard drive to three partitions. C: being the system one and allowing safe format in any moment I'd like to have fresh system, while D: and E: being storage (and other hard drives F, G, H...)
I hope I will be clear in this one, I've read up something about partitions under Linux, but I'm not sure if I get it right.
I've partitioned my HDD according to that logic (at least I hope so. Will know better after Gnome Commander is installed and I will see what I've done). This is how I made it, but I'm not sure if it's correct and if it does have sense.
[[IMG]http://img97.imageshack.us/img97/7637/hdda.th.jpg[/IMG]](http://img97.imageshack.us/i/hdda.jpg/)

Since the system is very fresh, I'm ready to format everything once again and set it up correctly. All my data is storaged on outside disks anyway.
Side question - is there a way to somehow save all the options, preferences etc. I've already set up to a file, so I can quickly personalize fresh installation?

4) Alert sound while going up the directory tree (Backspace key). How to disable that? It drives me crazy :).

5) How to enable numeric keyboard by default (so I don't have to press Num Lock every time I restart the system)?

These are few things that came to my head so far. I bet there will be more anyway :)
Also - sorry for such a long read, I just want everything be crystal clear.

---

### Post by friv_livs on 2009-11-06
For uninstalling many packages (programs) at once, just use synaptic from System->Administation menu.

---

### Post by hal10000 on 2009-11-06
> 1) Since I've always been working with Norton Commander like programs (Windows Commander and Total Commander later) and I'm very used to it. All the My Documents, Desktop, My Pictures folder structures are arch-enemies to what I call "tidy HDD". I want to install Gnome Commander... and I don't know how

Nothing is easier than installing software under linux. The easiest way is to open aterminal window and perform
```
 sudo apt-get install gnome-commander
```


> 2) I'd like to uninstall all games en masse. I've uninstalled some one by one, but it's annoying to do so in such way. Is there a way to remove more than one application at once?

Use synaptic (or another package manager)


> 3) Partitions. I used to divide my hard drive to three partitions. C: being the system one and allowing safe format in any moment I'd like to have fresh system, while D: and E: being storage (and other hard drives F, G, H...)
I hope I will be clear in this one, I've read up something about partitions under Linux, but I'm not sure if I get it right.
I've partitioned my HDD according to that logic (at least I hope so. Will know better after Gnome Commander is installed and I will see what I've done). This is how I made it, but I'm not sure if it's correct and if it does have sense.

You will never need a 10GB /boot partition, this is too large and wasting of harddrive space. If you use your computer as a desktop system, there is no need for a  separate boot partition at all. If you insist on having a separate /boot pertition, then 100MB (this is MegaByte, not Gigabyte) is enough.

Also, your swap is too big, unless you have more than 8GB RAM, you will not need more swap than the amount of your RAM size.

On the other hand, your root partition ( / ) might be a little bit too small. If you install a bunch of software here and there, or if you want to burn DVD images, you will soon run out of space. You should use about 15-20GB for your root partition.


> 4) Alert sound while going up the directory tree (Backspace key). How to disable that? It drives me crazy .

5) How to enable numeric keyboard by default (so I don't have to press Num Lock every time I restart the system)?

i don't use gnome, but i'm sure you can find those settings in your gnome-system configurations.

---

### Post by twisted_steel on 2009-11-06
> **kooboo said:**
> 
5) How to enable numeric keyboard by default (so I don't have to press Num Lock every time I restart the system)?

Supposedly it is found here:
System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn on "Default numeric keypad keys" 



I found it on this page: [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by kooboo on 2009-11-07
Much appreciated :grin:

---

