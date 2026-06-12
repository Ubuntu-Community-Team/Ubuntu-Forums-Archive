---
title: "gcompris will not start"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by earthpigg on 2009-06-23
when i run from terminal, this is the output:

```
ep@ep-9:~$ gcompris
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:4781): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/ep/.config/gcompris'
   Users dir '/home/ep/My GCompris'
   Database '/home/ep/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted

```

Ubuntu 9.04 amd64, with edubuntu metapackage installed.

ideas?

---

### Post by billgoldberg on 2009-06-23
> **earthpigg said:**
> when i run from terminal, this is the output:

```
ep@ep-9:~$ gcompris
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, [B]try the -x option to disable XF86VidMode.
[/B]
** (process:4781): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/ep/.config/gcompris'
   Users dir '/home/ep/My GCompris'
   Database '/home/ep/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted

```

Ubuntu 9.04 amd64, with edubuntu metapackage installed.

ideas?

Did you try the -x option?

Did you try removing (completely) the application and manually installing the newest one?

You can also report this on launchpad if you are up to it.

---

### Post by earthpigg on 2009-06-23
same error when i use the -x option

synaptic is telling me it is up-to-date -- are you suggesting i find a deb from getdeb or sourceforge?

---

### Post by billgoldberg on 2009-06-23
> **earthpigg said:**
> same error when i use the -x option

synaptic is telling me it is up-to-date -- are you suggesting i find a deb from getdeb or sourceforge?

No, from here:

[http://gcompris.net/](http://gcompris.net/)

Just make sure you remove the application completely before installing that one. Including hidden files in /home

---

### Post by earthpigg on 2009-06-23
> **billgoldberg said:**
> No, from here:

[http://gcompris.net/](http://gcompris.net/)

Just make sure you remove the application completely before installing that one. Including hidden files in /home

[http://gcompris.net/-Download-](http://gcompris.net/-Download-) tells me to use ubuntu's repos, and points to an 'unofficial' repository here: [http://thomas.enix.org/DebianRepository](http://thomas.enix.org/DebianRepository)

it has ubuntu deb's up to gutsy -- but nothing beyond that.

---

### Post by billgoldberg on 2009-06-23
> **earthpigg said:**
> [http://gcompris.net/-Download-](http://gcompris.net/-Download-) tells me to use ubuntu's repos, and points to an 'unofficial' repository here: [http://thomas.enix.org/DebianRepository](http://thomas.enix.org/DebianRepository)

it has ubuntu deb's up to gutsy -- but nothing beyond that.

They have the source code up.

Try compiling that.

---

### Post by earthpigg on 2009-06-23
reported to launchpad here: [https://bugs.launchpad.net/ubuntu/+source/edubuntu-meta/+bug/391385](https://bugs.launchpad.net/ubuntu/+source/edubuntu-meta/+bug/391385)

---

### Post by soliac on 2009-07-03
Hey, if you're still having trouble, the solution is easy. You need to install the python-numeric package - the gcompris in the repository is an older version that requires this library, and it wasn't packaged properly with this dependency. From [http://ubuntuforums.org/showthread.php?t=1123781]("http://ubuntuforums.org/showthread.php?t=1123781")

---

