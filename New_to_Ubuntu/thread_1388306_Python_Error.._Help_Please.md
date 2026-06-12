---
title: "Python Error.. Help Please"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-01-22
I recently installed apache2 with the intention of running my own local web server, and after installing rapache any time i try to install anything from the terminal i get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
rapache is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python2.5-minimal (2.5.4-1ubuntu6.1) ...
Linking and byte-compiling packages for runtime python2.5...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1746, in run
    pkg = DebPackage('package', pkgname, oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing python2.5-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on python2.5-minimal (= 2.5.4-1ubuntu6.1); however:
  Package python2.5-minimal is not configured yet.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gda:
 python-gda depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing python-gda (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python-gda (= 2.25.3-3ubuntu1); however:
  Package python-gda is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rapNo apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                              No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              ache:
 rapache depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing rapache (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.5-minimal
 python2.5
 python-gda
 python-gnome2-extras
 rapache
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is after running sudo apt-get install rapache, even though it is already installed. I can't install or remove anything, it always gives me this error.

Edit: Now that I think about it... this has been happening after I got a notification about an application crashing. I submitted the bug report, but after clicking the "submit" i was greeted with a message saying something went wrong submitting it, my luck i guess...

---

### Post by adam814 on 2010-01-22
```
sudo dpkg --configure -a
```

You have packages that aren't fully installed.  This will attempt to install them.

---

### Post by Stigmata13 on 2010-01-22
> **adam814 said:**
> ```
sudo dpkg --configure -a
```You have packages that aren't fully installed.  This will attempt to install them.

Running that command gives me the following output:

Setting up python2.5-minimal (2.5.4-1ubuntu6.1) ...
Linking and byte-compiling packages for runtime python2.5...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1746, in run
    pkg = DebPackage('package', pkgname, oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing python2.5-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on python2.5-minimal (= 2.5.4-1ubuntu6.1); however:
  Package python2.5-minimal is not configured yet.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gda:
 python-gda depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing python-gda (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python-gda (= 2.25.3-3ubuntu1); however:
  Package python-gda is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rapache:
 rapache depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing rapache (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.5-minimal
 python2.5
 python-gda
 python-gnome2-extras
 rapache

---

### Post by adam814 on 2010-01-22
Try this:
```
sudo apt-get purge python2.5-minimal && sudo dpkg --configure -a && sudo apt-get install python2.5-minimal
```

---

### Post by Stigmata13 on 2010-01-22
I'm no expert... but I think it was python2.5-minimal that crashed and didn't install correctly (while updating), at least that's what I remember from the bug report

---

### Post by Stigmata13 on 2010-01-22
> **adam814 said:**
> Try this:
```
sudo apt-get purge python2.5-minimal && sudo dpkg --configure -a && sudo apt-get install python2.5-minimal
```

Thank You! :D You saved me one big headache and a great deal of time!

---

