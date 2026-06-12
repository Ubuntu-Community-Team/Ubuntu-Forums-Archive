---
title: "python 2.6, 3.1 installed - uninstall 2.6? scipy path?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by tbeals31 on 2011-01-12
Hi all,

In 9.10 I've got python2.4 and a few related packages; python2.6 and a few packages, and python3 and a lot of packages.  IDLE's shell has 
    Python 3.1.1+ (r311:74480, Nov  2 2009, 15:45:00)
as its top line.

I installed scipy and it is in 
/usr/lib/python2.6/dist-packages/scipy.  
As my system is configured, (code) 
    from scipy import ...
results in
    ImportError: No module named scipy

How can I use scipy with Python 3.1?  Would it be as simple a matter as adding/changing paths?  Would it be a bad idea to uninstall older pythons (2.x) or are some system functions likely to depend on the older python versions?

Thanks,

twb

---

### Post by Cheesehead on 2011-01-12
It would be very unwise to uninstall older Python versions until you know why they were installed in the first place, and what still depends on them. Your system tracks these dependencies, and will be happy to tell you.
```

apt-cache depends python-scipy     #The packages scipy needs
apt-cache rdepends python2.6       #The packages that depend on python 2.6
```

A great deal of your system, for example, depends on Python 2.6.

For scipy and Python 3.x, see the scipy faq:
[http://new.scipy.org/faq.html#does-numpy-currently-work-with-python-3-x-what-about-scipy]("http://new.scipy.org/faq.html#does-numpy-currently-work-with-python-3-x-what-about-scipy")
(Short answer: Won't work)

---

### Post by cgroza on 2011-01-12
Your scipy module is only available in python2.6. 
To test this, open a python2.6 shell and try to import it.

To open python2.6 do:
```
python2.6
```
 
Check if scipy is compatible with 3.1 and then you can copy it in the python installation directory.

---

### Post by tbeals31 on 2011-01-13
Thanks Cheesehead and cgroza.  It would have been a disaster if I had uninstalled python2.6 - following your suggestion I saw lots of dependencies.

I started python2.6 from the command line and can import module scipy.  So now I can move ahead.

Thanks again,

twb

---

