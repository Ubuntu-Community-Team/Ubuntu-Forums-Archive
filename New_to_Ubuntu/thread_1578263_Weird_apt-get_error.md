---
title: "Weird apt-get error"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Mazehero55 on 2010-09-20
I'm having a weird error when I try to upgrade or install packages. Here is the terminal log:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils firefox firefox-3.5 firefox-3.5-branding
  firefox-3.5-gnome-support firefox-branding firefox-gnome-support
  google-chrome-beta gzip hpijs hplip hplip-data libhpmud0
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
  linux-image-2.6.32-24-generic linux-libc-dev sreadahead ureadahead
  winetricks xulrunner-1.9.2 xulrunner-1.9.2-dev xulrunner-dev
25 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/105MB of archives.
After this operation, 12.3kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: export: `/home/jonsul/.r6rs': not a valid identifier
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried to uninstall install-info but it says it will break emacs which I use for lisp programming. I've heard some things about how some programs install the wrong one in the wrong place but non of the fixes have helped. 
By the way thanks in advance. If it wasn't for people here to help me I would still be in windows land.:D

---

### Post by Mazehero55 on 2010-09-20
Something weird to note when I run sudo dpkg --configure -a

```
$ sudo dpkg --configure -a
[sudo] password for jonsul: 
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: export: `/home/jonsul/.r6rs': not a valid identifier
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info

```

Oddly I've already corrected this issue with the path. So why is it referencing something old when the newer /etc/environment file has '$HOME/.r6rs' now not `/home/jonsul/.r6rs'???

[edit]I hope I can figure this out soon. I need irb for a class soon and I can't install/update/remove till I can figure this out.
Thanks

---

### Post by Mazehero55 on 2010-09-21
Anyone have any ideas? I seriously can't install or update anything at all.
Update does anyone know what this means?
```
$ install-info --configure
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
ginstall-info: unrecognized option '--configure'
	Try `install-info --help' for a complete list of options.

```

---

### Post by drs305 on 2010-09-21
I would consider this a last-resort effort, as it bypasses APT by renaming the install-info post-installation script. Normally errors cease when the package script is removed, but I can't say this is an approved procedure. With that, we are not deleting anything, just renaming a file. It can be renamed to the original to restore things.

```
sudo mv /var/lib/dpkg/info/install-info.postinst /var/lib/dpkg/info/install-info.postinst.bad
```

To restore if necessary:
```
sudo mv /var/lib/dpkg/info/install-info.postinst.bad /var/lib/dpkg/info/install-info.postinst
```

I can tell you I ran the command and then did an update and upgrade successfully, but 1) my install-info package was already installed and 2) I have no experience with the message in your last post.

---

### Post by sandyd on 2010-09-21
> **Mazehero55 said:**
> I'm having a weird error when I try to upgrade or install packages. Here is the terminal log:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils firefox firefox-3.5 firefox-3.5-branding
  firefox-3.5-gnome-support firefox-branding firefox-gnome-support
  google-chrome-beta gzip hpijs hplip hplip-data libhpmud0
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
  linux-image-2.6.32-24-generic linux-libc-dev sreadahead ureadahead
  winetricks xulrunner-1.9.2 xulrunner-1.9.2-dev xulrunner-dev
25 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/105MB of archives.
After this operation, 12.3kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: export: `/home/jonsul/.r6rs': not a valid identifier
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I tried to uninstall install-info but it says it will break emacs which I use for lisp programming. I've heard some things about how some programs install the wrong one in the wrong place but non of the fixes have helped. 
By the way thanks in advance. If it wasn't for people here to help me I would still be in windows land.:D
post output of
```

sudo cat 
/etc/environment

```

---

### Post by pastalavista on 2010-09-21
Is there a '.r6rs' in your home/jonsul folder? if not, make one there. Also try and make one in /home and if you've done all that, try 'sudo apt-get install -f' and 'sudo dpkg-reconfigure install-info ginstall-info' and then 'sudo dpkg --configure -a' again. 

It was a kernel update and will probably be fixed soon. Have you rebooted yet?

---

### Post by Mazehero55 on 2010-09-21
@drs305
I'll try that in a sec, I'll post back in a sec

@pastalavista
sudo apt-get install -f returns the same error as when I try to install something
```
$ sudo dpkg-reconfigure install-info ginstall-info
/usr/sbin/dpkg-reconfigure: install-info is broken or not fully installed

```

@sandyd
Here you go, the others entries are scheme paths to my libraries.
```
$ sudo cat /etc/environment
PATH="/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games"

IKARUS_LIBRARY_PATH=$HOME/.r6rs
export $IKARUS_LIBRARY_PATH

YPSILON_SITELIB=$HOME/.r6rs
export $YPSILON_SITELIB

SCHEMEHEAPDIRS=".:../boot/%m:"
export SCHEMEHEAPDIRS


```

[edit]
Wow! Drs305 things are working now :D. But is this a permanent fix, or will this have complications in the future? Either way I can get some things for class installed at least for now^^

---

### Post by sandyd on 2010-09-21
> **Mazehero55 said:**
> @drs305
I'll try that in a sec, I'll post back in a sec

@pastalavista
sudo apt-get install -f returns the same error as when I try to install something
```
$ sudo dpkg-reconfigure install-info ginstall-info
/usr/sbin/dpkg-reconfigure: install-info is broken or not fully installed

```@sandyd
Here you go, the others entries are scheme paths to my libraries.
```
$ sudo cat /etc/environment
PATH="/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games"

IKARUS_LIBRARY_PATH=$HOME/.r6rs
export $IKARUS_LIBRARY_PATH

YPSILON_SITELIB=$HOME/.r6rs
export $YPSILON_SITELIB

SCHEMEHEAPDIRS=".:../boot/%m:"
export SCHEMEHEAPDIRS


```[edit]
Wow! Drs305 things are working now :D. But is this a permanent fix, or will this have complications in the future? Either way I can get some things for class installed at least for now^^
```

PATH="/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games"

#IKARUS_LIBRARY_PATH=$HOME/.r6rs
#export $IKARUS_LIBRARY_PATH

#YPSILON_SITELIB=$HOME/.r6rs
#export $YPSILON_SITELIB

SCHEMEHEAPDIRS=".:../boot/%m:"
export SCHEMEHEAPDIRS

```should work.
if your wondering what ypsilon is... -> [http://code.google.com/p/ypsilon/](http://code.google.com/p/ypsilon/)

and ikarus -> [http://linux.softpedia.com/get/Programming/Compilers/Ikarus-44233.shtml](http://linux.softpedia.com/get/Programming/Compilers/Ikarus-44233.shtml)
unless you use R6RS compiler, its not needed.

and I don't know if the envvars accepts the pound commenting out sign.
If it doesn't, give it a backup, and erase the lines completely

---

### Post by drs305 on 2010-09-21
> **Mazehero55 said:**
> 
Wow! Drs305 things are working now :D. But is this a permanent fix, or will this have complications in the future? Either way I can get some things for class installed at least for now^^

The intent of my post was to get things working if nothing else worked. The post-installation script was never completed via the method I gave you.

*sandyd*'s approach with the cat environment method is an approach to fix the problem without bypassing APT. I'd keep my 'fix' available but attempt to restore things in the normal manner first if possible.

---

### Post by Bachstelze on 2010-09-21
> **sandyd said:**
> ```

PATH="/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games"

#IKARUS_LIBRARY_PATH=$HOME/.r6rs
#export $IKARUS_LIBRARY_PATH

#YPSILON_SITELIB=$HOME/.r6rs
#export $YPSILON_SITELIB

SCHEMEHEAPDIRS=".:../boot/%m:"
export SCHEMEHEAPDIRS

```
should work.
if your wondering what ypsilon is... -> [http://code.google.com/p/ypsilon/](http://code.google.com/p/ypsilon/)

and ikarus -> [http://linux.softpedia.com/get/Programming/Compilers/Ikarus-44233.shtml](http://linux.softpedia.com/get/Programming/Compilers/Ikarus-44233.shtml)
unless you use R6RS compiler, its not needed.

Those lines didn't add themselves, they are probbly there for a reason. How about fixing them instead of disabling them?

```

PATH="/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games"

IKARUS_LIBRARY_PATH=$HOME/.r6rs
export IKARUS_LIBRARY_PATH

YPSILON_SITELIB=$HOME/.r6rs
export YPSILON_SITELIB

SCHEMEHEAPDIRS=".:../boot/%m:"
export SCHEMEHEAPDIRS

```

---

### Post by Mazehero55 on 2010-09-22
They're the environment variables to ikarus and ypsilon for the path to my libraries. They don't seem to work though because both say they can't find the path. But when I enter the path in my terminal it finds it fine :/
Do you think it could be them?

I guess I could remove them, I mostly use racket for scheme programming. I only installed them to experiment with pure r6rs implementations.

---

