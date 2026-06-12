---
title: "Ubuntu Software Center: Package operation failed but installs anyway?"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by xpaperbackwriterx on 2011-01-22
So, when I try to install anything from the Ubuntu Software Center, it asks me to authorize it with my password, so I do, but when I hit authorize all that happens is that the password box goes away, and the window stays there, and the stupid thing wont install until you get rid of the window, so I hit the exit button (since now the authorize and cancel buttons magically don't work) and it seems to install fine.  But then towards the end I get this every time (this particular one was when I downloaded OpenShot Video Editor):


installArchives() failed: Selecting previously deselected package libgfortran3.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 148126 files and directories currently installed.)
Unpacking libgfortran3 (from .../libgfortran3_4.5.1-7ubuntu2_i386.deb) ...
Selecting previously deselected package libatlas3gf-base.
Unpacking libatlas3gf-base (from .../libatlas3gf-base_3.8.3-22ubuntu2_i386.deb) ...
Selecting previously deselected package libcv2.1.
Unpacking libcv2.1 (from .../libcv2.1_2.1.0-2_i386.deb) ...
Selecting previously deselected package libhighgui2.1.
Unpacking libhighgui2.1 (from .../libhighgui2.1_2.1.0-2_i386.deb) ...
Selecting previously deselected package libcvaux2.1.
Unpacking libcvaux2.1 (from .../libcvaux2.1_2.1.0-2_i386.deb) ...
Selecting previously deselected package libgavl1.
Unpacking libgavl1 (from .../libgavl1_1.1.2-3_i386.deb) ...
Selecting previously deselected package frei0r-plugins.
Unpacking frei0r-plugins (from .../frei0r-plugins_1.1.22git20091109-1.1_i386.deb) ...
Selecting previously deselected package libavdevice52.
Unpacking libavdevice52 (from .../libavdevice52_4%3a0.6-2ubuntu6_i386.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libmng1.
Unpacking libmng1 (from .../libmng1_1.0.10-1_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4%3a4.7.0-0ubuntu4.2_i386.deb) ...
Selecting previously deselected package liboil0.3.
Unpacking liboil0.3 (from .../liboil0.3_0.3.16-1ubuntu2_i386.deb) ...
Selecting previously deselected package libquicktime1.
Unpacking libquicktime1 (from .../libquicktime1_2%3a1.1.5-1_i386.deb) ...
Selecting previously deselected package libsox1b.
Unpacking libsox1b (from .../libsox1b_14.3.1-1build1_i386.deb) ...
Selecting previously deselected package libmlt2.
Unpacking libmlt2 (from .../libmlt2_0.5.6+git20100727-1_i386.deb) ...
Selecting previously deselected package libmlt++3.
Unpacking libmlt++3 (from .../libmlt++3_0.5.6+git20100727-1_i386.deb) ...
Selecting previously deselected package libmlt-data.
Unpacking libmlt-data (from .../libmlt-data_0.5.6+git20100727-1_all.deb) ...
Selecting previously deselected package libsox-fmt-alsa.
Unpacking libsox-fmt-alsa (from .../libsox-fmt-alsa_14.3.1-1build1_i386.deb) ...
Selecting previously deselected package libsox-fmt-base.
Unpacking libsox-fmt-base (from .../libsox-fmt-base_14.3.1-1build1_i386.deb) ...
Selecting previously deselected package melt.
Unpacking melt (from .../melt_0.5.6+git20100727-1_i386.deb) ...
Selecting previously deselected package python-mlt2.
Unpacking python-mlt2 (from .../python-mlt2_0.5.6+git20100727-1_i386.deb) ...
Selecting previously deselected package openshot.
Unpacking openshot (from .../openshot_1.2.2-1_all.deb) ...
Selecting previously deselected package openshot-doc.
Unpacking openshot-doc (from .../openshot-doc_1.2.2-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for shared-mime-info ...
Processing triggers for python-support ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up libgfortran3 (4.5.1-7ubuntu2) ...
Setting up libatlas3gf-base (3.8.3-22ubuntu2) ...
update-alternatives: using /usr/lib/atlas-base/atlas/libblas.so.3gf to provide /usr/lib/libblas.so.3gf (libblas.so.3gf) in auto mode.
update-alternatives: using /usr/lib/atlas-base/atlas/liblapack.so.3gf to provide /usr/lib/liblapack.so.3gf (liblapack.so.3gf) in auto mode.
Setting up libcv2.1 (2.1.0-2) ...
Setting up libhighgui2.1 (2.1.0-2) ...
Setting up libcvaux2.1 (2.1.0-2) ...
Setting up libgavl1 (1.1.2-3) ...
Setting up frei0r-plugins (1.1.22git20091109-1.1) ...
Setting up libavdevice52 (4:0.6-2ubuntu6) ...
Setting up libqtcore4 (4:4.7.0-0ubuntu4.2) ...
Setting up libmng1 (1.0.10-1) ...
Setting up libqt4-xml (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-dbus (4:4.7.0-0ubuntu4.2) ...
Setting up libqtgui4 (4:4.7.0-0ubuntu4.2) ...
Setting up libqt4-svg (4:4.7.0-0ubuntu4.2) ...
Setting up liboil0.3 (0.3.16-1ubuntu2) ...
Setting up libquicktime1 (2:1.1.5-1) ...
Setting up libsox1b (14.3.1-1build1) ...
Setting up libmlt2 (0.5.6+git20100727-1) ...
Setting up libmlt++3 (0.5.6+git20100727-1) ...
Setting up libmlt-data (0.5.6+git20100727-1) ...
Setting up libsox-fmt-alsa (14.3.1-1build1) ...
Setting up libsox-fmt-base (14.3.1-1build1) ...
Setting up melt (0.5.6+git20100727-1) ...
Setting up python-mlt2 (0.5.6+git20100727-1) ...
Setting up openshot (1.2.2-1) ...
Setting up openshot-doc (1.2.2-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 firmware-b43-installer
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1


And I have NO Idea what it means, but when I get out of that window that package finishes installing and then works fine.  So.....what?  It said it failed! Why is it working?  SO confused.  


And fyi, I have little in-depth knowledge of Ubuntu because when a smart computer guy was cleaning up my laptop and examining it as to why it used to shut down at random, he heard that I hated windows and so he made it so I can dual boot Vista (BLEGH) and Ubuntu 11.04 on my laptop.  Sometime last year I'd been actively learning the command line, but I've forgotten it all.  So my knowledge is pretty sparse (hopefully not for long);)

---

### Post by Layvian on 2011-01-22
There is a couple of things to keep in mind first.


[LIST]
[*]Make sure everything is up-to-date software wise, there are a lot of dependencies that each application needs. (Example: Directx for 3D gaming)
[LIST]
[*]To do this: System > Administration > Update Manager [Located on the top bar]
[/LIST]
 
[*]Try uninstalling it. Then Reinstall it.
[/LIST]
The password it asks for is your superuser or /root password.  Once you put this in it will stay there for a period of time unless your ask it to instantly forget in options.  Also make sure your drivers are up-to-date.

[LIST]
[*]System > Administration > Additional Drivers
[/LIST]
Let me know if the methods I've given do not work.

---

### Post by xpaperbackwriterx on 2011-01-22
> **Layvian said:**
> There is a couple of things to keep in mind first.


[LIST]
[*]Make sure everything is up-to-date software wise, there are a lot of dependencies that each application needs. (Example: Directx for 3D gaming)
[LIST]
[*]To do this: System > Administration > Update Manager [Located on the top bar]
[/LIST]
 
[*]Try uninstalling it. Then Reinstall it.
[/LIST]
The password it asks for is your superuser or /root password.  Once you put this in it will stay there for a period of time unless your ask it to instantly forget in options.  Also make sure your drivers are up-to-date.

[LIST]
[*]System > Administration > Additional Drivers
[/LIST]
Let me know if the methods I've given do not work.

Er....I've done everything except uninstalling and reinstalling.  Nothing else has worked. Are you saying uninstall the package I installed, or uninstall/reinstall the Software Center? How do you do that?:tongue:

---

### Post by Layvian on 2011-01-22
> **xpaperbackwriterx said:**
> Er....I've done everything except uninstalling and reinstalling.  Nothing else has worked. Are you saying uninstall the package I installed, or uninstall/reinstall the Software Center? How do you do that?:tongue:


Oh my apology I should have been more specific.  The software you installed uninstall that.  It might work by doing that.  Worse come to worse, depending on how much time and effort you have invested it might be wise to reinstall the OS itself, you should have all if not most of the dependences you need to install that application right after you have installed Ubuntu on your System.  Ubuntu itself takes no time to install.  

I hope reinstalling works for you through, I know what a pain it is to install a OS again.  Please let me know if the reinstall after uninstalling works.

Good Luck.

---

### Post by xpaperbackwriterx on 2011-01-22
Gah! Okay.  I just got settled in too! I'll have to figure out how to do that :|  It might all be because the smart computer guy put natty narwhal alpha 1 on it (probably because he's a developer and he had the disk around, as my guess would be).  I could just deal with it I suppose.  I mean, it's installing the packages anyway, even though it says they failed.  I don't know what it might be doing to glitch things up, but meh.  I'm used to VISTA, baby glitches don't bother me! :P

---

### Post by Layvian on 2011-01-23
Lol sounds, good.  If you do have issues just continue to ask around I am sure You will get your answer.

---

