---
title: "Uninstall Virtual box"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by fanglore on 2009-07-09
I have Virtualbox running on my host kubuntu 9.04. the virtualbox is the open source version and im really getting tired of the downfalls of it such as no direct usb and no sound. i have the non-oes version. i need to know how to uninstall the one i have now. help please

---

### Post by philcamlin on 2009-07-09
sudo apt-get remove virtualbox(version)

---

### Post by fanglore on 2009-07-09
ty ill try it and see if it works

---

### Post by philcamlin on 2009-07-09
ok if its version 3.0 or whatever be like 

sudo apt-get remove virtualbox3.0

or find it in synaptic

---

### Post by fanglore on 2009-07-09
i just deletes the .Vmachine folder

---

### Post by fanglore on 2009-07-09
> **philcamlin said:**
> ok if its version 3.0 or whatever be like 

sudo apt-get remove virtualbox3.0

or find it in synaptic

where is the syna whatchamacallit

---

### Post by philcamlin on 2009-07-09
ok purge it then 

sudo apt-get purge virtualbox(version)

:)

see if that works

---

### Post by fanglore on 2009-07-09
it said it couldnt find the pakage

---

### Post by philcamlin on 2009-07-09
then its gone :D

---

### Post by fanglore on 2009-07-09
cool ty :D im a complete noob to ubunu XD

---

### Post by credobyte on 2009-07-09
How did you installed it ? By launching .deb downloaded from their website ( then this should help : [http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm) ) ?

---

### Post by jpeddicord on 2009-07-09
The OSE version is `virtualbox-ose`. If you want to get rid of it, `sudo apt-get remove virtualbox-ose` should do it or just search for virtualbox in System > Administration > Synaptic.

---

### Post by Elep.Repu on 2009-07-09
I like
```
sudo apt-get --purge remove
```

---

### Post by mystmaiden on 2009-07-10
I was wondering, do you need to uninstall Windows from it before uninstalling the virtual box?

myst

---

### Post by kpkeerthi on 2009-07-10
> **mystmaiden said:**
> I was wondering, do you need to uninstall Windows from it before uninstalling the virtual box?

myst

No. The virtual machines will be under ~/.VirtualBox by default unless you changed the location otherwise. If you don't need them you could just remove them
```
rm -rf ~/.VirtualBox
```

---

### Post by mystmaiden on 2009-07-10
Thanks kpkeerthi :) The other thing I've been trying to sort out today is how one would remove a guest os from virtualbox. So far google just keeps asking me if I really mean 'install' so not much luck yet. 

myst

---

### Post by theozzlives on 2009-07-10
> **mystmaiden said:**
> Thanks kpkeerthi :) The other thing I've been trying to sort out today is how one would remove a guest os from virtualbox. So far google just keeps asking me if I really mean 'install' so not much luck yet. 

myst

In VirtualBox, highlight the machine and right-click... Then delete.
In the File >> Virtual Disk Manager... hilight the disk and select remove.

---

### Post by lkraemer on 2009-07-11
If you didn't specify the proper package name it most likely did not
get removed.  Just because the message was displayed that said it couldn't
find the package does not mean it was removed.  Any typo could have
caused the message.

Try the following in a terminal window:
```

cd /
locate virtualbox

```

If virtualbox information scrolls on the screen you may want to use:

```

sudo apt-get remove virtualbox*

```

or

```

sudo apt-get purge virtualbox*

```

lkraemer

---

