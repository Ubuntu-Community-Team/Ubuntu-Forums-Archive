---
title: "How to remove a corrupt application?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-06-24
I installed empathy from synaptic but my system hanged while installing and i restarted the system to find that the installation was corrupt i got crash reports too.When i try to remove it from synatic or terminal i get this error report
E: /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb: subprocess new pre-removal script returned error exit status 1

So how to completely remove this application

---

### Post by llamabr on 2009-06-24
Post the entire output, and the command you're using.  Try:

```
sudo apt-get remove empathy
```

---

### Post by ravi_buz on 2009-06-24
[HTML]ravi@ravi-desktop:~$ sudo apt-get remove empathy
[sudo] password for ravi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgupnp-av-1.0-1 libgssdp-1.0-1 libcurl3 libsdl-ttf2.0-0 libsdl-mixer1.2
  libgupnp-1.0-2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  empathy telepathy-gnome
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.7kB of archives.
After this operation, 1262kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 166266 files and directories currently installed.)
Preparing to replace telepathy-butterfly 0.3.3-1 (using .../telepathy-butterfly_0.3.3-1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1475, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

---

### Post by tomthumb99 on 2009-07-14
Folks, I am also looking for a forceful way of removing two corrupt packages (metacity-common, epiphany-browser-data).  Both the apt-get and dpkg terminal commands do not work, I have tried multiple times with the correct parameters.  I get the same "E: Sub-process /usr/bin/dpkg returned an error code (1)".   Pls kindly advise the error log location to check the dpkg error code.  Also Synaptic has error here in the re-install of these two packages.  

I will re-install the packages correctly via synaptic,  once the corruption is removed.  I can live without epiphany, but need metacity.

---

### Post by colau on 2009-08-16
> **tomthumb99 said:**
> Folks, I am also looking for a forceful way of removing two corrupt packages (metacity-common, epiphany-browser-data).  Both the apt-get and dpkg terminal commands do not work, I have tried multiple times with the correct parameters.  I get the same "E: Sub-process /usr/bin/dpkg returned an error code (1)".   Pls kindly advise the error log location to check the dpkg error code.  Also Synaptic has error here in the re-install of these two packages.  

I will re-install the packages correctly via synaptic,  once the corruption is removed.  I can live without epiphany, but need metacity.
Run these and report:
```

sudo dpkg --configure -a
sudo apt-get --purge remove empathy

```

---

### Post by ravi_buz on 2009-08-16
Still Didnt work 
[PHP]ravi@ravi-desktop:~$ sudo dpkg --configure -a
dpkg: error processing telepathy-butterfly (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 telepathy-butterfly
ravi@ravi-desktop:~$ sudo apt-get --purge remove empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  telepathy-sofiasip libgupnp-av-1.0-1 libgssdp-1.0-1 libcurl3 telepathy-idle
  libgupnp-1.0-2 libsofia-sip-ua-glib3 libsofia-sip-ua0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  empathy*
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.7kB of archives.
After this operation, 1225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 238650 files and directories currently installed.)
Preparing to replace telepathy-butterfly 0.3.3-1 (using .../telepathy-butterfly_0.3.3-1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1475, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

---

### Post by colau on 2009-08-16
Did you try this too?
```

sudo apt-get autoremove empathy

```

---

### Post by ravi_buz on 2009-08-17
Didnt do it either 
[PHP]ravi@ravi-desktop:~$ sudo apt-get autoremove empathy
[sudo] password for ravi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  telepathy-sofiasip libgupnp-av-1.0-1 libgssdp-1.0-1 libcurl3 telepathy-idle
  libgupnp-1.0-2 libsofia-sip-ua-glib3 libsofia-sip-ua0
The following packages will be REMOVED:
  empathy libcurl3 libgssdp-1.0-1 libgupnp-1.0-2 libgupnp-av-1.0-1
  libsofia-sip-ua-glib3 libsofia-sip-ua0 telepathy-idle telepathy-sofiasip
0 upgraded, 0 newly installed, 9 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.7kB of archives.
After this operation, 4051kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 240180 files and directories currently installed.)
Preparing to replace telepathy-butterfly 0.3.3-1 (using .../telepathy-butterfly_0.3.3-1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1475, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/telepathy-butterfly_0.3.3-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

---

