---
title: "virtualbox problems"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by patchido on 2010-02-12
well, i need this virtualbox machine because i dont want to mess up my music, ive got too much music going on in my ipod so i want to manage it through itunes, ive got 2 problems doing this, 1st- i cant get virtualbox to get the usb port, it tells "no available devices, and second, i cant get my music folder that is not inside the virtual machine to be shared with the windows vm..



PD: i was wondering, is it able and fully capable of hosting a mac os?

(for iphone apps programming)

---

### Post by bronquel on 2010-02-12
Ubuntu is your guest OS?  What is your Host OS?

this is probably a better question to ask google or virtualbox forums...

---

### Post by patchido on 2010-02-12
im running ubuntu karmic and in ubuntu i have a virtualbox with windows on it

---

### Post by QIII on 2010-02-12
VirtualBox OSE (which is the one in the repos) does not support USB.

You'll need the full version.  But I haven't even gotten that to work yet with Fedora 12.  Seems the latest Virtualbox and Fedora 12 don't get along, so you may have better luck.

You can go to Oracle/Sun's website and find instructions for downloading and installing the full version (personal use only) on Ubuntu.  At least I think that's where I found the instructions.


Edit:  I just checked.  I added "http:/download.virtualbox.org/virtualbox/debian karmic non-free" to my software sources and installed virtualbox-3.1 through Synaptic.

---

### Post by LOLbuntu on 2010-02-12
Uninstall OSE if you have not yet and download the full version
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

to share folders, click settings> shared folders

---

### Post by QIII on 2010-02-12
Thanks, LOL.

I was just about to post the URL.

---

### Post by patchido on 2010-02-12
about the mac os, is it possible???


my laptop is a dell inspiron 1420

---

### Post by QIII on 2010-02-12
I suspect the Mac option is possible, although I've never tried it.

At the URL provided, there is some documentation.  Try giving that a read.

---

