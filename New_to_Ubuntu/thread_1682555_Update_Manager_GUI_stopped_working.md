---
title: "Update Manager GUI stopped working"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by connells on 2011-02-06
I'm using 10.10 and rely on the Update Manager app to keep up to date etc. About a week ago the Update Manager AND the Ubuntu Software Centre stopped working. That is, when I launch them either nothing happens (Update) or the inital launch occurs then disappears (Software Centre).
If I run it from a terminal I get this
```
user@blah:~$ update-manager
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: No module named gi
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 32, in <module>
    import gconf
ImportError: No module named gconf

```

Most of the threads I have read deal with a pre-release version of ubuntu and multiple versions of python etc. 
I want to know where I can start looking for solutions as to how to un-break this issue. I reckon solving a problem is a great way to learn but I need a few pointers. Why do I get the No module error messages and should I be looking at config files or re-installing packages.

---

### Post by corncob on 2011-02-06
Can you open System > Administration > Synaptic Package Manager?  If so, I'd mark update-manager, update-manager-core, and software-center for reinstallation and apply.

---

### Post by leviathan8 on 2011-02-06
You could just use [FONT="Courier New"]sudo apt-get update && sudo apt-get upgrade[/FONT] instead. It does the same thing.

---

### Post by corncob on 2011-02-06
> **leviathan8 said:**
> You could just use [FONT="Courier New"]sudo apt-get update && sudo apt-get upgrade[/FONT] instead. It does the same thing.

That will get you upgraded but what I was trying to do was to fix your Update Manager and Software Center.  If Synaptic isn't working (I wouldn't be surprised as it is tied into the Software Center) you could reinstall UM and SC via the terminal.  First remove them:
```
sudo dpkg -r update-manager software-center
```
Then reinstall them
```
sudo apt-get install update-manager software-center
```

---

### Post by connells on 2011-02-06
I'm at work now so will try the suggestion later on.

I have been using ```
sudo apt-get update && sudo apt-get upgrade 
``` but it just feels incomplete to have to resort to the terminal.

Synaptic does work (which surprises me) so I will give the uninstall / reinstall suggestion a go and see what happens.

---

### Post by Nigec on 2011-02-07
I'm having the same problem but different error:
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid-backports_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by connells on 2011-02-07
Well I just tried to re-install first using Synaptic without success, and then using the terminal commands without success.
In fact, a pattern emerged when running the installation; the "ImportError: No module named gi" message appeared again.

What else could it be?

```
The following NEW packages will be installed:
  software-center update-manager update-notifier
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 79.9kB/1,326kB of archives.
After this operation, 4,071kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com/ubuntu/ maverick/main update-notifier i386 0.105ubuntu1 [79.9kB]
Fetched 79.9kB in 6s (12.4kB/s)                                                                                                                                                    
Selecting previously deselected package software-center.
(Reading database ... 156229 files and directories currently installed.)
Unpacking software-center (from .../software-center_3.0.7_all.deb) ...
Selecting previously deselected package update-manager.
Unpacking update-manager (from .../update-manager_1%3a0.142.22_all.deb) ...
Selecting previously deselected package update-notifier.
Unpacking update-notifier (from .../update-notifier_0.105ubuntu1_i386.deb) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up software-center (3.0.7) ...
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: No module named gi
Setting up update-manager (1:0.142.22) ...
Processing triggers for python-central ...
Setting up update-notifier (0.105ubuntu1) ...

```

This is what happens when running update-manager in the terminal. No change as far as I can see.

```
user@blah:~$ update-manager
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: No module named gi
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 32, in <module>
    import gconf
ImportError: No module named gconf
```

---

