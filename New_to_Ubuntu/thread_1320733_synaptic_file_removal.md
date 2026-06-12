---
title: "synaptic file removal"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-11-09
I did a complete removal of Opera, but alas some files remain. I need to remove them completely to do a fresh opera install. How can I delete the remaining files? File mgr will not allow it?

---

### Post by mikewhatever on 2009-11-09
It might have been useful if you had told us which files had remained and need removing, or else, why do you think something remain. As is, your post is rather vague.

---

### Post by rosswmcgee on 2009-11-09
There are left over files in the root that allow even after a complete removal for

Opera to remember your book marks, speed dial, etc. In other words I want to remove every thing that is Opera. To give you the exact files I would need to remove Opera again.

Here are the files left over:

Opera 10.1 var/cache/apt/archives
Opera var/apt/lists
3files like that.

In other words the Opera system is still there not removed although it shows it as removed in synaptic.

---

### Post by mikewhatever on 2009-11-09
Bookmarks and speed dial are user settings, they should never be outside your home folder, unless you are running as root. I don't quite understand the purpose of this, since user settings have nothing to do with the installation itself, as different users may have different settings on the same machine. To get rid of your settings, open Nautilus, hit ctrl+h and look for .opera or opera folder. Delete it if found.

---

### Post by rosswmcgee on 2009-11-09
Where is nautilus?

---

### Post by rosswmcgee on 2009-11-09
OK figured it out, never tried it that way before, please and thankyou!

For some reason the control h brings it up whereas the regular home folder did not show it.

---

### Post by rosswmcgee on 2009-11-09
Ok yes I did that but after the folder was removed those embedded files are still there.

---

### Post by rosswmcgee on 2009-11-09
Are there some delete commands in terminal that would do the job?

---

### Post by mikewhatever on 2009-11-09
> **rosswmcgee said:**
> Are there some delete commands in terminal that would do the job?

Not that I know. You could try completely removing Opera again and then look for leftovers with **locate opera** command.

---

### Post by rosswmcgee on 2009-11-09
locate opera showed a bunch of files in terminal---now how do I delete them?

---

### Post by mikewhatever on 2009-11-09
> **rosswmcgee said:**
> locate opera showed a bunch of files in terminal---now how do I delete them?

Use ** rm path_to _file** command. Posting the output of locate opera here first might be a good idea.

---

### Post by rosswmcgee on 2009-11-09
Ok this what comes up in terminal.


rosswmcgee@rosswmcgee-desktop:~$ locate opera
/etc/operaprefs_default.ini
/etc/operaprefs_fixed.ini
/etc/apt/sources.list.d/opera.list
/home/rosswmcgee/.opera
/home/rosswmcgee/.local/share/Trash/info/opera_10.01.4682.gcc4.qt3_i386.deb.trashinfo
/home/rosswmcgee/.local/share/Trash/info/opera_10.2.01.4682.gcc4.qt3_i386.deb.trashinfo
/lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-opera.ko
/usr/bin/opera
/usr/lib/opera
/usr/lib/evolution/2.28/plugins/liborg-gnome-exchange-operations.so
/usr/lib/evolution/2.28/plugins/org-gnome-exchange-operations.eplug
/usr/lib/python2.6/dist-packages/lazr/restfulclient/docs/operations.txt
/usr/lib/python2.6/dist-packages/twisted/test/test_cooperator.py
/usr/lib/python2.6/dist-packages/twisted/test/test_cooperator.pyc
/usr/share/opera
/usr/share/applications/opera.desktop
/usr/share/doc/opera
/usr/share/evolution/2.28/errors/org-gnome-exchange-operations.error
/usr/share/icons/hicolor/128x128/apps/opera.png
/usr/share/icons/hicolor/16x16/apps/opera.png
/usr/share/icons/hicolor/22x22/apps/opera.png
/usr/share/icons/hicolor/32x32/apps/opera.png
/usr/share/icons/hicolor/48x48/apps/opera.png
/usr/share/icons/hicolor/scalable/apps/opera.svg
/usr/share/icons/oxygen/16x16/actions/irc-operator.png
/usr/share/icons/oxygen/16x16/actions/irc-remove-operator.png
/usr/share/icons/oxygen/22x22/actions/irc-operator.png
/usr/share/icons/oxygen/22x22/actions/irc-remove-operator.png
/usr/share/icons/oxygen/32x32/actions/irc-operator.png
/usr/share/icons/oxygen/32x32/actions/irc-remove-operator.png
/usr/share/icons/oxygen/48x48/actions/irc-operator.png
/usr/share/icons/oxygen/48x48/actions/irc-remove-operator.png
/usr/share/man/man1/opera.1.gz
/usr/share/man/man7/operator.7.gz
/usr/share/menu/opera
/usr/share/pixmaps/opera.xpm
/usr/share/pyshared/lazr/restfulclient/docs/operations.txt
/usr/share/pyshared/twisted/test/test_cooperator.py
/usr/src/linux-headers-2.6.31-14-generic/include/config/dvb/usb/opera1.h
/var/cache/apt/archives/opera_10.01.4682.gcc4.qt3_i386.deb
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg
/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages
/var/lib/dpkg/info/opera.conffiles
/var/lib/dpkg/info/opera.list
/var/lib/dpkg/info/opera.md5sums
/var/lib/dpkg/info/opera.postinst
/var/lib/dpkg/info/opera.postrm
/var/lib/dpkg/info/opera.prerm
/var/lib/dpkg/info/opera.templates
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by mikewhatever on 2009-11-09
Well, some of them are unrelated to Opera, and others are unrelated to settings, but the following three:

```
/etc/operaprefs_default.ini
/etc/operaprefs_fixed.ini
/home/rosswmcgee/.opera

```

You personal settings, bookmarks etc should be in .opera. Run **rm -r .opera** to remove it.
To remove the other two, run:

sudo rm /etc/operaprefs_default.ini
sudo rm /etc/operaprefs_fixed.ini

---

### Post by rosswmcgee on 2009-11-09
Just when I thought we had it made I get this:

rosswmcgee@rosswmcgee-desktop:~$ sudo rm /etc/operaprefs_default.ini
rm: cannot remove `/etc/operaprefs_default.ini': No such file or directory
rosswmcgee@rosswmcgee-desktop:~$ sudo rm /etc/operaprefs_fixed.ini
rm: cannot remove `/etc/operaprefs_fixed.ini': No such file or directory
rosswmcgee@rosswmcgee-desktop:~$ rm -r .opera
rm: cannot remove `.opera': No such file or directory
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by rosswmcgee on 2009-11-09
Problem solved:

I took a chance and reinstalled Opera from the file system. It came in with the correct paths, so I was able to import my contacts and bookmarks. As a warning to others not to make the mistake I did, by downloading the Opera .adr files to the desktop. The correct destination is the home folder. Thans again for your help.

Ross

---

