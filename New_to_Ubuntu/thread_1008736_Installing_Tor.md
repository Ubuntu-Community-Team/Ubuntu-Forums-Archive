---
title: "Installing Tor"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by zapree on 2008-12-11
Ok so i did go to the page telling me how to install Tor but when i put in the command that it gives me into terminal 
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) hardy main
it tells me that deb-src isnt a command.....
same thing when i just put in deb w/o src
any ideas?

---

### Post by zapree on 2008-12-11
oh btw the tor guide was this
[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by bodhi.zazen on 2008-12-11
See here :

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

That is not a command to enter, that line is something you add to /etc/apt/sources.list

You can edit this file with :

```
gksu gedit /etc/apt/sources.list
```

---

### Post by Hospadar on 2008-12-11
that isn't actually a command, you're supposed to add those lines to your /etc/apt/sources.list file.  This is the file that tells apt (the package manager) where to look for packages.  I don't think you actually need to do that stuff though.  Those instructions show how to set things up to install tor from the tor project's repositories.  The standard ubuntu repositories have copies of to as well though.

All you should really need to do is "sudo apt-get install tor" at a command line.

If for some reason you need the absolute latest version of tor, you can do those instructions in the guide.  Open your /etc/apt/sources file as root in a text editor "gksu gedit /etc/apt/sources.list" and add the two deb and deb-src lines to the end of that file.

Good luck!

Also, if you plan on using tor in firefox, I'd suggest getting either the torbutton or foxyproxy addons from the firefox addon website.

---

