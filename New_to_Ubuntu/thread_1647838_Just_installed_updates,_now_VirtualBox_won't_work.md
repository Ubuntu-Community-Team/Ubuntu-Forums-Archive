---
title: "Just installed updates, now VirtualBox won't work"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-17
Hi, I just installed the updates for Ubuntu  a few hours ago and now VirtualBox will not run. I get this error when I try to run it:

Failed to open a session for the virtual machine Windows XP
PIIX cannot attach drive to the Secondary Master (VERR_TIMEOUT)
Unknown error creating VM (VERR_TIMEOUT)

Anybody have a clue?

-----------------------------------
I have Ubuntu 10.10 32 bit on a AMD 64

---

### Post by lmarmisa on 2010-12-17
Maybe this problem is due to an update of the kernel program. 

I recommend to reinstall VirtualBox using Synaptic (select "Mark for Reinstallation" and Apply).

This alternative command will reinstall the package too:

```

sudo apt-get install --reinstall package-name (for example, virtualbox-3.2)

```

---

### Post by waynefoutz on 2010-12-18
If you add the Virtualbox repository, it will update itself. That way you'll never run into this problem again. What happens is, a kernel update forces you to reinstall Virtualbox, because it has code in the kernel. If you add the repository, Virtualbox will update itself when the kernel does. 

put these in the terminal:

```
sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian lucid non-free"
```


```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

```

---

### Post by s1baker on 2010-12-18
thanks guys, but for some reason, now it loads, don't know why though. maybe I needed to wait on it to load a bit more or reboot Ubuntu, like I did. Don't know, mysterious...sometimes like "twilight zone" stuff.

I will keep "plugging" .... thanks again guys. I will note this as resolved.

---

