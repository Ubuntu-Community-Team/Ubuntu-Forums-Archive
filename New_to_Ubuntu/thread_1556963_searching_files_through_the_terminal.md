---
title: "searching files through the terminal"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-20
Hi I was wondering if I could do some sort of Desktop searching through the Gnome terminal. specifically I want to search all the files on my computer based on a keyword search.

---

### Post by vikas.sood on 2010-08-20
> **gaurish108 said:**
> Hi I was wondering if I could do some sort of Desktop searching through the Gnome terminal. specifically I want to search all the files on my computer based on a keyword search.

I think you are looking for "find".
find . -name "your searh key"

man find to get more on it.

---

### Post by beren.olvar on 2010-08-20
Also the "locate" command is useful. (man locate)

---

### Post by jtarin on 2010-08-20
First run the command ```
sudo updatedb
``` this will update your data base to current conditions. This will take several moments to run. Then you can use ```
locate <filename>
``` to find anything on your computer. Then use ["grep]("https://help.ubuntu.com/community/grep")" to find anything within a file or document.

---

### Post by nothingspecial on 2010-08-20
As was said before, use the find command, for example, if you want to find every file on your computer with the string "firefox" in its name then type


```

sudo find / -type f -name *firefox*
```

Which on my netbook returns

```
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox-branding.md5sums
/var/lib/dpkg/info/firefox-gnome-support.postinst
/var/lib/dpkg/info/firefox-gnome-support.list
/var/lib/dpkg/info/firefox.prerm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox-branding.list
/var/lib/dpkg/info/firefox-gnome-support.md5sums
/var/lib/dpkg/info/firefox-gnome-support.prerm
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/alternatives/firefox-homepage
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/cache/apt/archives/firefox-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb
/var/cache/apt/archives/firefox-gnome-support_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
/var/cache/apt/archives/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
/var/cache/apt/archives/firefox-branding_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
/var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb
/var/cache/apt/archives/firefox-gnome-support_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb
/usr/share/applications/firefox.desktop
/usr/share/apport/package-hooks/firefox.py
/usr/share/doc/firefox/firefox.cfg
/usr/share/menu/firefox
/usr/share/ubuntu-docs/common/prepare-firefox-startpage-translations
/usr/share/ubuntu-docs/libs/img/firefox-3.5.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-installer.png
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/ubuntu-artwork/home/firefox-index.html
/usr/lib/firefox-3.6.8/firefox
/usr/lib/firefox-3.6.8/defaults/pref/firefox-l10n.js
/usr/lib/firefox-3.6.8/defaults/pref/firefox.js
/usr/lib/firefox-3.6.8/defaults/pref/firefox-branding.js
/usr/lib/firefox-3.6.8/firefox.sh
/usr/lib/firefox-3.6.8/firefox-restart-required.update-notifier
/usr/lib/firefox-3.6.8/firefox-bin
/etc/firefox/pref/firefox.js
/etc/apparmor.d/usr.bin.firefox

```

/ means search the whole computer from / up (or down depending on how you look at it)

-type f means only search for files rather than directories

-name *firefox* means the name of the file must have the string firefox in it. The 2 *s mean any number of any characters can come before of after the string firefox

If you are unsure of the case (FIREFOX/firefox) use iname instead of name.

---

### Post by Vaphell on 2010-08-20
+1 for find
find command is a powerful tool, it can not only find stuff with very flexible set of criteria (recursive/with set depth, dirs/files only, names/regular expressions, time of file access/modification - you name it), but also perform an action on each found object right off the bat

for example find . -type f -iname *.mp3 -exec cp {} ~/my_music \;
will find any .mp3 file in a current directory (with all its subdirectories) and copy to ~/my_music

---

### Post by sharathcshekhar on 2010-08-20
+1 for find :)
Also you also use find . -regex [pattern] to useful to search some regular expressions

Sharath

---

### Post by ronnielsen1 on 2010-08-20
I like whereis

> ron@laptop:~$ whereis foobillard
foobillard: /usr/games/foobillard /usr/share/man/man6/foobillard.6.gz
ron@laptop:~$ 



---

