---
title: "opera issue"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by tchoklat on 2009-07-27
I have  just upgraded to Jaunty and installed opera 10 thru the repos. When I attempt to run it I get:

tony@tony-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/tony/lib/opera/10.00/opera: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory

Any isdeas?

tchoklat

---

### Post by whitethorn on 2009-07-27
try running 

```

sudo apt-get install libqtgui4

```

See if that helps it run.

---

### Post by tchoklat on 2009-07-27
> **whitethorn said:**
> try running 

```

sudo apt-get install libqtgui4

```See if that helps it run.


tried that and terminal says:

tony@tony-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported
(experimental) ARGB visual detected: Use '-visual 0x23' to activate it
opera: Module initialization failure [9]. Generic failure (-1)


tony

---

### Post by Colonel Kilkenny on 2009-07-27
> **tchoklat said:**
> tried that and terminal says:

tony@tony-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported
(experimental) ARGB visual detected: Use '-visual 0x23' to activate it
opera: Module initialization failure [9]. Generic failure (-1)

tony

Update Opera to latest build: [http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)
And start Opera using new profile (rename ~/.opera to ~/.opera_old).

---

### Post by ktechkio on 2009-07-27
Download opera from site...

Your issue is due to wrong version of qt. Opera 10 is available in qt3 and 4. You need to have appropriate qt working.

---

### Post by tchoklat on 2009-07-27
FIXED

It was the ownership of files in .opera. I chowned them to me and all is fine. Thanks for the help ....

> **ktechkio said:**
> Download opera from site...

Your issue is due to wrong version of qt. Opera 10 is available in qt3 and 4. You need to have appropriate qt working.


I have installed the .debs from the opera site all three versions, and all return the same error ...

Do I have to install / uninstall qt3/4. Not sure what this is though! My Jaunty installation was brand new upgrade so don't know why it fails to run ...


Should not the repos have the right version as I have enabled the opera repos.

I need my existing .opera as it has my mail in it.


Tony

---

