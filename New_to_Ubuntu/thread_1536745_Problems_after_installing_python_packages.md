---
title: "Problems after installing python packages"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by CaptainMark on 2010-07-22
Ive installed python 3 packages and now the package python-ubuntuone-client is throwing out an error message, it wont update, synaptic gives me ```
E: /var/cache/apt/archives/python-ubuntuone-client_1.2.2-0ubuntu2_all.deb: subprocess new pre-removal script returned error exit status 1


```
and sudo apt-get upgrade gives me ```
mark@mark-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-ubuntuone-client
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/152kB of archives.
After this operation, 8,192B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 155047 files and directories currently installed.)
Preparing to replace python-ubuntuone-client 1.2.1-0ubuntu3 (using .../python-ubuntuone-client_1.2.2-0ubuntu2_all.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/python-ubuntuone-client_1.2.2-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-ubuntuone-client_1.2.2-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@mark-desktop:~$ 

```Any thoughts?

---

### Post by Paqman on 2010-07-22
Which actual Python packages did you install? You should be able to have Python 3 co-exist quite happily on the same machine as earlier versions.

---

### Post by CaptainMark on 2010-07-22
i installed python3, python3-minimal, and python3-dev. I left python 2 packages as they were and then through the software centre i installed IDLE3.

---

### Post by Paqman on 2010-07-22
Do you actually need the dev package? I've got all those packages except the dev on my machine and it's working fine? If that's not the problem then it's a bug with that Ubuntu One package.

---

### Post by CaptainMark on 2010-07-22
i dont know what the dev package does, pythons website recommended adding it, the situation is worsening now ive got a load of errors with packages ```
mark@mark-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-ubuntuone-client (1.2.2-0ubuntu2) ...
/var/lib/dpkg/info/python-ubuntuone-client.postinst: 10: pycentral: not found
dpkg: error processing python-ubuntuone-client (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-ubuntuone-client (= 1.2.2-0ubuntu2); however:
  Package python-ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.2.2-0ubuntu2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libubuntuone-1.0-1:
 libubuntuone-1.0-1 depends on ubuntuone-client-gnome (>= 1.1.2); however:
  Package ubuntuone-client-No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                       No apport report written because the error message indicates it's a follow-up error from a previous failure.
   No apport report written because MaxReports has already been reached
                                                                       gnome is not configured yet.
dpkg: error processing libubuntuone-1.0-1 (--configure):
 dependency problems - leaving unconfigured
Setting up music-applet (2.5.1-0ubuntu1) ...
/var/lib/dpkg/info/music-applet.postinst: 6: gconf-schemas: not found
dpkg: error processing music-applet (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gmenu (2.30.0-0ubuntu4) ...
No apport report written because MaxReports has already been reached
                                                                    Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
/var/lib/dpkg/info/python-gmenu.postinst: 1: /usr/share/gnome-menus/update-gnome-menus-cache: not found
/var/lib/dpkg/info/python-gmenu.postinst: 25: update-python-modules: not found
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python-ubuntuone:
 python-ubuntuone depends on libubuntuone-1.0-1 (= 0.3.1-0ubuntu1); however:
  Package libubuntuone-1.0-1 is not configured yet.
dpkg: error processing python-ubuntuone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-ubuntuone-music-store:
 rhythmbox-ubuntuone-music-store depends on libubuntuone-1.0-1 (>= 0.2.100); however:
  Package libubuntuone-1.0-1 is not configured yet.
 rhythmbox-ubuntuone-music-store depends on python-ubuntuone (>= 0.2.100); however:
  Package python-ubuntuone is noNo apport report written because MaxReports has already been reached
                    No apport report written because MaxReports has already been reached
        No apport report written because MaxReports has already been reached
                                                                            t configured yet.
 rhythmbox-ubuntuone-music-store depends on ubuntuone-client (>= 1.1.2); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing rhythmbox-ubuntuone-music-store (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-ubuntuone-client
 ubuntuone-client
 ubuntuone-client-gnome
 libubuntuone-1.0-1
 music-applet
 python-gmenu
 python-ubuntuone
 rhythmbox-ubuntuone-music-store
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Psrj on 2011-06-22
I have been having the same problem but worse.  I used sudo apt-get -f and it told me to uninstall a ton of packages.  I did... and this ended in disaster...

To fix things up I have been compiling Python 2.7.1 and other packages that were lost because Apt isn't working.  This has sort of been working but I don't have all of Python compiled because pythonobject (or something like that) wouldn't compile

Gnome is among one of the things that isn't working either.  Unity works but I don't understand why it does.  Doesn't Unity use Gnome for stuff?

Anyway, even though I'm late on a reply to this thread does anyone know how to fix this problem?

**Edit: Also I can't reinstall because the only CD I have... I don't have anymore (lol) and I can't buy another one. **

---

