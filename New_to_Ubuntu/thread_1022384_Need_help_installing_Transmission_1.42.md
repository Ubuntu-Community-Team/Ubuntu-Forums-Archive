---
title: "Need help installing Transmission 1.42"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-12-26
I'm needing help installing Transmission 1.42 for a tar. I have already extracted it to my home folder, and cd'd it and ./configured it.

Now I when I enter the make command, I get some kind of error.

So does anyone know of some commands that can help me install it(and yes, I've read the Install and Readme files in the folder, but I'm still having problems)?

Thank you for any help.

EDIT: Or if anyone has a .deb of 1.42 that would really help me out.

---

### Post by Sef on 2008-12-26
1) Have you installed build-essential?   Applications > Accessories > Terminal

then type or paste in this command:

```
sudo apt-get update && sudo apt-get install build-essential
```

2) If you have then check [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by Stalker72 on 2008-12-26
> **h8uthemost said:**
> I'm needing help installing Transmission 1.42 for a tar. I have already extracted it to my home folder, and cd'd it and ./configured it.

Now I when I enter the make command, I get some kind of error.

So does anyone know of some commands that can help me install it(and yes, I've read the Install and Readme files in the folder, but I'm still having problems)?

Thank you for any help.

EDIT: Or if anyone has a .deb of 1.42 that would really help me out.
[http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

Stalker72

---

### Post by h8uthemost on 2008-12-26
Yep, I have build essentials installed. 

It's when I type Make, I get this error, the same error I always get whenever I try to install something, Linux can be so difficult to install simple programs:

**** No targets specified and no makefile found.  Stop.*

Isn't there some way to get the Repos to update Transmission to version 1.42?

---

### Post by taurus on 2008-12-26
You're supposed to run ./configure first before you run the make.  And to build it, you also need to install openssl first besides build-essential package.

Otherwise, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and add these two lines at the end of it, assuming you are running **intrepid**.

```

deb http://ppa.launchpad.net/transmissionbt/ubuntu **intrepid** main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu **intrepid** main

```
Save it and close gedit window.  Then run

```
sudo apt-get update
sudo apt-get install transmission
```

---

### Post by h8uthemost on 2008-12-26
Ha! That did it taurus! I'm now running 1.42. Thank you so much, you have no idea how much a I appreciate that.

EDIT: And just to let you know, I did do ./configure before I ran make. But perhaps I didn't install openssl is the reason why I it wouldn't make for me.

Thanks again.

---

