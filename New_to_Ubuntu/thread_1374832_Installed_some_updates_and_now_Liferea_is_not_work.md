---
title: "Installed some updates and now Liferea is not working anymore"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by legolas_w on 2010-01-07
Hi
I have just installed some updates which was including the webkit and its related libraries. Now my liferea is not working and when I run it in the console it returns the following error:

liferea: symbol lookup error: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type


Any idea what should I do?


Thanks

---

### Post by Takmadeus on 2010-01-07
Affects me too, also software center does not work anymore due to a webkit problem.

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type
takmadeus@takmadeus-desktop:~$ software-center 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type

```

---

### Post by soro2005 on 2010-01-07
I think you guys are using the webkit-team ppa? Seems like there's a major upgrade going on, should come back once everything's up to date I assume.

Or rather: Perhaps there was some hiccup that has installed a wrong version of libsoup2.4 and libsoup-gnome2.4. I, in any case, have fixed this by manually installing (i.e. downgrading) the two packages from the webkit-team ppa. To do so, head over to: [https://launchpad.net/~webkit-team/+archive/ppa/+packages](https://launchpad.net/~webkit-team/+archive/ppa/+packages) and expand libsoup2.4 - 2.28.2-1~kkwkt1. Or go directly to [https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra](https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra). Then find the two deb packages libsoup-gnome2.4-1_2.28.2-1~kkwkt1 and libsoup2.4-1_2.28.2-1~kkwkt1 that correspond with your architecture (i386 or amd64), download them to a location which you can find in a terminal window, and type
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_i386.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_i386.deb
``` or
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
``` (depending on your architecture). If something goes wrong, you might end up uninstalling a lot of programs, so watch out and double check before you confirm any choices.

---

### Post by mimetist on 2010-01-07
I had the same problem and it was caused by a new version of libwebkit.

The solution is to go back to the previous version (from synaptic) or deactivate the "unofficial" repositories for Libwebkit.

Assuming that this is for beginners (like me), this issue is caused (also can be solved) with some kind of app like Ubuntu Tweak... if you have it installed, then you need to launch it and deactivate the repositories for liferea and libwebkit there.

---

### Post by legolas_w on 2010-01-07
> **soro2005 said:**
> I think you guys are using the webkit-team ppa? Seems like there's a major upgrade going on, should come back once everything's up to date I assume.

Or rather: Perhaps there was some hiccup that has installed a wrong version of libsoup2.4 and libsoup-gnome2.4. I, in any case, have fixed this by manually installing (i.e. downgrading) the two packages from the webkit-team ppa. To do so, head over to: [https://launchpad.net/~webkit-team/+archive/ppa/+packages](https://launchpad.net/~webkit-team/+archive/ppa/+packages) and expand libsoup2.4 - 2.28.2-1~kkwkt1. Or go directly to [https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra](https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra). Then find the two deb packages libsoup-gnome2.4-1_2.28.2-1~kkwkt1 and libsoup2.4-1_2.28.2-1~kkwkt1 that correspond with your architecture (i386 or amd64), download them to a location which you can find in a terminal window, and type
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_i386.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_i386.deb
``` or
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
``` (depending on your architecture). If something goes wrong, you might end up uninstalling a lot of programs, so watch out and double check before you confirm any choices.


Thanks, it worked.

---

### Post by MastroPino on 2010-01-07
Thx it works! =)

---

### Post by DJ_Peng on 2010-01-08
> **soro2005 said:**
> I think you guys are using the webkit-team ppa? Seems like there's a major upgrade going on, should come back once everything's up to date I assume.

Or rather: Perhaps there was some hiccup that has installed a wrong version of libsoup2.4 and libsoup-gnome2.4. I, in any case, have fixed this by manually installing (i.e. downgrading) the two packages from the webkit-team ppa. To do so, head over to: [https://launchpad.net/~webkit-team/+archive/ppa/+packages](https://launchpad.net/~webkit-team/+archive/ppa/+packages) and expand libsoup2.4 - 2.28.2-1~kkwkt1. Or go directly to [https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra](https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra). Then find the two deb packages libsoup-gnome2.4-1_2.28.2-1~kkwkt1 and libsoup2.4-1_2.28.2-1~kkwkt1 that correspond with your architecture (i386 or amd64), download them to a location which you can find in a terminal window, and type
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_i386.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_i386.deb
``` or
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
``` (depending on your architecture). If something goes wrong, you might end up uninstalling a lot of programs, so watch out and double check before you confirm any choices.

You're a lifesaver. This has been bugging the hell out of me with evolution-rss the last few days and I finally have it fixed. Now I have both my evo and my [Chromium]("http://code.google.com/p/chromium/issues/detail?id=31809") fixed. Now I just have to get these two fixes blogged in hopes of helping others find them.

---

### Post by Stemp on 2010-01-08
Ooops sorry for the mess /o\

WebkitGtk 1.1.18 is incompatible with libsoup 2.29.3, so we had to downgrade to version 2.28.2 in order to provide it.

---

### Post by jaapz on 2010-01-09
> **soro2005 said:**
> I think you guys are using the webkit-team ppa? Seems like there's a major upgrade going on, should come back once everything's up to date I assume.

Or rather: Perhaps there was some hiccup that has installed a wrong version of libsoup2.4 and libsoup-gnome2.4. I, in any case, have fixed this by manually installing (i.e. downgrading) the two packages from the webkit-team ppa. To do so, head over to: [https://launchpad.net/~webkit-team/+archive/ppa/+packages](https://launchpad.net/~webkit-team/+archive/ppa/+packages) and expand libsoup2.4 - 2.28.2-1~kkwkt1. Or go directly to [https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra](https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra). Then find the two deb packages libsoup-gnome2.4-1_2.28.2-1~kkwkt1 and libsoup2.4-1_2.28.2-1~kkwkt1 that correspond with your architecture (i386 or amd64), download them to a location which you can find in a terminal window, and type
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_i386.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_i386.deb
``` or
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
``` (depending on your architecture). If something goes wrong, you might end up uninstalling a lot of programs, so watch out and double check before you confirm any choices.
You're AWESOME! Now i can use pino and midori again :D
Thanks!

---

### Post by wesswei on 2010-01-11
kudos and thanks! gotta love a quick fix. alternatively, this can be done the graphical way within synaptic... 

package > force version > downgrade libsoup-gnome, then libsoup

---

### Post by darkxman on 2010-01-13
> **soro2005 said:**
> I think you guys are using the webkit-team ppa? Seems like there's a major upgrade going on, should come back once everything's up to date I assume.

Or rather: Perhaps there was some hiccup that has installed a wrong version of libsoup2.4 and libsoup-gnome2.4. I, in any case, have fixed this by manually installing (i.e. downgrading) the two packages from the webkit-team ppa. To do so, head over to: [https://launchpad.net/~webkit-team/+archive/ppa/+packages](https://launchpad.net/~webkit-team/+archive/ppa/+packages) and expand libsoup2.4 - 2.28.2-1~kkwkt1. Or go directly to [https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra](https://launchpad.net/~webkit-team/+archive/ppa/+sourcepub/922643/+listing-archive-extra). Then find the two deb packages libsoup-gnome2.4-1_2.28.2-1~kkwkt1 and libsoup2.4-1_2.28.2-1~kkwkt1 that correspond with your architecture (i386 or amd64), download them to a location which you can find in a terminal window, and type
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_i386.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_i386.deb
``` or
```
sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
``` (depending on your architecture). If something goes wrong, you might end up uninstalling a lot of programs, so watch out and double check before you confirm any choices.

Thank you very much!

---

### Post by Prominence on 2010-01-14
grayson@Providence:~$ sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
[sudo] password for grayson: 
dpkg: error processing libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb
 libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
grayson@Providence:~$ 





That's what I get, what's going wrong?

---

### Post by soro2005 on 2010-01-14
> **Prominence said:**
> grayson@Providence:~$ sudo dpkg -i libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
[sudo] password for grayson: 
dpkg: error processing libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libsoup2.4-1_2.28.2-1~kkwkt1_amd64.deb
 libsoup-gnome2.4-1_2.28.2-1~kkwkt1_amd64.deb
grayson@Providence:~$ 





That's what I get, what's going wrong?
I believe the instructions are obsolete now. You might be able to solve the issue by simply updating your system with (command line)
```
sudo apt-get update && sudo apt-get upgrade
```
or your preferred graphical way of doing it. In any case, you get the error most likely b/c you have downloaded newer versions of the files from the ppa, and they have a different file name. To make the command above work, you would have to adapt it accordingly.

---

### Post by Prominence on 2010-01-14
> **soro2005 said:**
> I believe the instructions are obsolete now. You might be able to solve the issue by simply updating your system with (command line)
```
sudo apt-get update && sudo apt-get upgrade
```
or your preferred graphical way of doing it. In any case, you get the error most likely b/c you have downloaded newer versions of the files from the ppa, and they have a different file name. To make the command above work, you would have to adapt it accordingly.

do I need that one PPA enabled?

---

