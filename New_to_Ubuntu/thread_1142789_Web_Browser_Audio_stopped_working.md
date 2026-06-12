---
title: "Web Browser Audio stopped working"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Baatti on 2009-04-29
Can I please have some assistance with an audio issue? Videos were playing fine on my web browser. I then installed Xine and Amarok 2, and now the audio on my web browser no longer works

I've tried using: sudo apt-get --reinstall install flashplugin-nonfree

I've also tried: sudo apt-get remove flashplugin-nonfree $$ sudo apt-get autoremove $$ sudo apt-get install flashplugin-nonfree

please help :(

PS, I'm running Jaunty.

---

### Post by kansasnoob on 2009-04-29
I would first go to Synaptic and click on Search, then type flash. the only two packages you should have installed are ubuntu-restricted-extras and adobe-flashplugin.

Check all other flash packages (ie: gnash, swfdec*, etc.) for complete removal! Then restart Firefox.

Still no sound? Go here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Note that it says, "Jaunty users: Follow Part A." ***only!***

Then some of the troubleshooting steps may help if you're still having trouble.

---

### Post by Baatti on 2009-04-30
thanks a ton... all better now :)

---

