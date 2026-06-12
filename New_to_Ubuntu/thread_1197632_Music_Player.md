---
title: "Music Player"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by rusteland@yahoo.com on 2009-06-26
Okay folks, be gentle with me. 

I am poking around for a music player. Thought I would give Banshee a try. I now need to:

**Step 1:** On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: *1024/12345678*. Copy it, or make a note of, the portion after the slash, e.g: *12345678*.
    **Step 2:** Open your terminal and enter:
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

I do not know how to open my terminal... 

If you need it, the APT lines are as follows:
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main

Thanks,
PL

---

### Post by mcduck on 2009-06-26
Banshee is available in Ubuntu's default repositories, so you only need to use the PPA repository if you want the latest version instead of the one Ubuntu has.

Anyway, you'll find the terminal in Applications/Accessories/Terminal.

---

### Post by rusteland@yahoo.com on 2009-06-26
McDuck.... McTastic.

Too easy. Way 2 B.

Thanks

---

### Post by clive littlewood on 2009-06-26
Hi

Try and install programs from within Ubuntu until you get used to the system.

Go to System > Admin > synaptic or Apps > Add/Remove and put in a search term.

This will find your program install with any dependencies required and add the appropriate menu item in your apps menu.

Hope this helps      :D

Clive

---

