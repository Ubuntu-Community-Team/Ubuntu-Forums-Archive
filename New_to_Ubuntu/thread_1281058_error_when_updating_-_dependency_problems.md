---
title: "error when updating - dependency problems"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by boogey on 2009-10-02
I get this following message after doing updates:

> E: network-manager: subprocess post-installation script returned error exit status 127
E: network-manager-gnome: dependency problems - leaving unconfigured

or more detailed:
> 
Setting up openoffice.org (1:2.4.1-1ubuntu2.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
 * Reloading system message bus config...
   ...done.
 * Restarting network connection manager NetworkManager
/usr/sbin/NetworkManager: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured 

seems like the update manager itself is missing some library files. so far I doesn't seem to affect my updates (all files seem to go through) but I still would like what's missing or how to fix the dependency problem.

---

### Post by halitech on 2009-10-02
not completely sure it will work but you could try
```
sudo apt-get install -f
``` and see if it resolves the issue

---

### Post by inobe on 2009-10-02
in synaptic you can fix broken packages, the feature is under "edit"

report back with any errors

---

### Post by boogey on 2009-10-02
> **halitech said:**
> not completely sure it will work but you could try
```
sudo apt-get install -f
``` and see if it resolves the issue

tried that already - same result as above.

---

### Post by boogey on 2009-10-02
> **inobe said:**
> in synaptic you can fix broken packages, the feature is under "edit"

report back with any errors

no errors while fixing broke packages (synaptic couldn't find any broken packages to start with when I searched with the filter)

after that I tried the:

```
sudo apt-get install -f
``` again -same initial error message

---

### Post by kansasnoob on 2009-10-02
Due to the release of Karmic Beta the servers are overloaded so I suspect this will resolve itself within the next 24 to 48 hours.

---

### Post by boogey on 2009-10-02
> **kansasnoob said:**
> Due to the release of Karmic Beta the servers are overloaded so I suspect this will resolve itself within the next 24 to 48 hours.

thing is, I have received this message at least for the past 2-3 weeks... I was hoping that it would just be a server overload, but would guess that that would have been solved by now.

---

### Post by halitech on 2009-10-02
I wonder if running
```
sudo dpkg-reconfigure network-manager-gnome
```
will work

---

### Post by boogey on 2009-10-02
> **halitech said:**
> I wonder if running
```
sudo dpkg-reconfigure network-manager-gnome
```
will work

Interesting, after trying this, I get:

> /usr/sbin/dpkg-reconfigure: network-manager-gnome is broken or not fully installed

but I dont find any broken files with synaptic manager nor can I force the install....

---

### Post by JC Cheloven on 2009-10-02
Let's join the orgy of commands :-) What about: ```
sudo dpkg --configure -a
```
(perhaps there is a wider problem than network manager, and that should fix it)

---

### Post by inobe on 2009-10-03
> **boogey said:**
> no errors while fixing broke packages (synaptic couldn't find any broken packages to start with when I searched with the filter)

after that I tried the:

```
sudo apt-get install -f
``` again -same initial error message

are you getting access to the internet ?

i never tried accessing files from the install cd but it may be possible.

search for network-manager and try to run it.

---

### Post by boogey on 2009-10-04
> **JC Cheloven said:**
> Let's join the orgy of commands :-) What about: ```
sudo dpkg --configure -a
```
(perhaps there is a wider problem than network manager, and that should fix it)

sorry for the late response,
 I tried that, however I still get the error message:

> Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Restarting network connection manager NetworkManager                         /usr/sbin/NetworkManager: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager
 network-manager-gnome


other than that, my internet connection is great I don't think the problem has to do with that.

---

### Post by boogey on 2009-10-05
anyone any idea?

---

### Post by mikechant on 2009-10-06
OK, I think this is the important bit:

> error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

Somehow your packages have got out of step, so the dbus package doesn't match the Network Manager package.

You could see if the workaround
```
sudo ln -s /usr/lib/libdbus-1.so.3 /usr/lib/libdbus-1.so.2
```
allows
```
sudo dpkg --configure -a
```
to run - if it does, then you apply all updates and that works properly, that may solve the underlying problem (i.e. your packages may end up at the correct compatable levels).

Note that I got this info from googling the exact part of the error message above (in quotes). Quite a few posts suggested the above.

---

### Post by gdonwallace on 2009-10-06
Something else that may help:

**sudo apt-cache unmet **
     This will display any programs that have unmet dependencies.  You can  use this list to install specific files that are not already on your computer.

OR

**sudo apt-get check**
     This will check for any "broken" installed programs.  

Although Synaptic should find any install that is considered broken.  So the second may not be as helpful, but you may want to run this one as it looks at the database of installed packages that apt keeps on your system.

A third option is to reinstall gnome-network manager.  However; this will cause problems with internet connectivity.  If you don't have a LiveCD of Ubuntu, then I would not attempt this option.  If you do, then set it as one of your repositores in system > Administration > software sources.  That way it will attempt to install gnome-network manager from the CD instead of the other repositories.

---

### Post by halitech on 2009-10-06
third option is a good idea however they would need the alt install cd as the live cd will not work as a cd repo as the files are in the squashfs and not actual deb files so synaptic (or apt) would not be able to find any files to install.

---

### Post by boogey on 2009-10-06
thanks for the help everyone!
I followed mikechant suggestions and ran an update and this time the correct compatibilities were found - no error message! I also accept the criticism about not checking google first - simply didn't think of it. I will in the future! thanks again for the help!

---

### Post by mikechant on 2009-10-07
Glad it worked.

> I also accept the criticism about not checking google first 

Not intended as a criticism - it's not always easy to work out exactly what to google for anyhow. :)

---

### Post by gdonwallace on 2009-10-07
Glad you were able to get everything working.

---

### Post by kuttan on 2009-10-11
Hi firends, I have a similar issue.  sudo dpkg --configure -a gives the following:
------------------
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
 * Reloading system message bus config...                                                    [ OK ] 
 * Restarting network connection manager NetworkManager                                             start-stop-daemon: unrecognized option `--signal9--retry'
Try `start-stop-daemon --help' for more information.
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager
 network-manager-gnome
----------
Any idea? I don't understand where this thing coming from "unrecognized option `--signal9--retry'"
Pl help

---

