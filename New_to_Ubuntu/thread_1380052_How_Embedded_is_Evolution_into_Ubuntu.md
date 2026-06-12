---
title: "How Embedded is Evolution into Ubuntu?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-13
I use Thunderbird as my preferred email client. I've still got Evolution installed as it is put there by default, but I was wondering whether there's a hidden or background aspect of Evolution that means uninstalling/removing it would cause a pain in the butt?

---

### Post by audiomick on 2010-01-13
Short answer:
if you remove it, you will kill gnome. The desktop and evolution are interwoven.

---

### Post by Roger Allott on 2010-01-13
And another related question I've got regards Empathy and Pidgin. For IMs, although I rarely use it, I think I prefer Pidgin. Would uninstalling Empathy cause me any distress? Is there something that Empathy does that Pidgin doesn't?

---

### Post by mcduck on 2010-01-13
Basically you can remove the evolution, but not all of it's related files (as some desktop components that integrate with Evolution require those components).

Anyway, uninstalling Evolution won't gain you any noticeable amount of disk space, and if you don't use it it's not using your CPU time either so uninstalling it really just isn't worth the trouble.

---

### Post by philinux on 2010-01-13
> **Roger Allott said:**
> I use Thunderbird as my preferred email client. I've still got Evolution installed as it is put there by default, but I was wondering whether there's a hidden or background aspect of Evolution that means uninstalling/removing it would cause a pain in the butt?

It used to remove ubuntu-desktop among other but right now as you can see it can be reomved. 12.8 meg though, hardly worth it.

```
 sudo apt-get purge evolution
[sudo] password for philinux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  evolution* evolution-couchdb* evolution-exchange* evolution-indicator*
  evolution-plugins*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 12.8MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by Soul-Sing on 2010-01-13
PlEASE before someone kills his system:
When you remove evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let [COLOR="Red"]evolution-data-server(-common)[/COLOR] untouched.

---

### Post by philinux on 2010-01-13
> **leoquant said:**
> PlEASE before someone kills his system:
When you remove evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let [COLOR="Red"]evolution-data-server(-common)[/COLOR] untouched.

As you can see above purging evo does not remove evolution-data-server in Karmic or lucid.

It may have done in previous releases 

I use evo as my one and only email client. I actually love its calendar, ubuntu-one contact sync and gnome integration i.e notifications etc. It syncs with google calendar and there to my palm pre. Magic. 

Even if someone uses an alternative to evo I cant see the point of removing it to save 12meg.

---

### Post by slakkie on 2010-01-13
> **leoquant said:**
> PlEASE before someone kills his system:
When you remove evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let [COLOR="Red"]evolution-data-server(-common)[/COLOR] untouched.

That is not true. The ubuntu-desktop package is just a meta-package. You can safely remove it. But don't expect that it will install new packages if you do a release upgrade. Since the meta package cannot install dependencies if it is not installed. But other then that it is perfectly fine and will not break your machine.

---

### Post by 3rdalbum on 2010-01-13
In short, if you go to remove a package and it brings up a massive list of other packages that would be removed too, and the list includes things like "gnome-panel", then it's probably NOT what you want to do.

---

### Post by oldos2er on 2010-01-13
> **leoquant said:**
> PlEASE before someone kills his system:
When you remove evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let [COLOR="Red"]evolution-data-server(-common)[/COLOR] untouched.

I've never been left with a broken system after removing evolution and ubuntu-desktop.

---

### Post by marshmallow1304 on 2010-01-13
> **Roger Allott said:**
> Would uninstalling Empathy cause me any distress?

Nope

---

### Post by corncob on 2010-01-13
> **Roger Allott said:**
> I use Thunderbird as my preferred email client. I've still got Evolution installed as it is put there by default, but I was wondering whether there's a hidden or background aspect of Evolution that means uninstalling/removing it would cause a pain in the butt?

I was interested in this thread as I too use Thunderbird and Pidgin and Evolution and Empathy are just sitting there.  Something nobody mentioned is that you could remove the launcher from the panel by right-clicking it and selecting 'remove'.  Also, by right-clicking the Ubuntu symbol in the upper left of the screen (or typing 'alacarte' into the terminal) you could edit them out of the Applications menu.

---

### Post by DestructionsRightHand on 2010-01-13
I would say no, i use the same client

:~$ aptitude show evolution
Package: evolution
State: installed
Automatically installed: no
Version: 2.28.1-0ubuntu2
Priority: optional
Section: gnome
Maintainer: Debian Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 8,098k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbluetooth3 (>=
         4.40), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>=
         2.7), libcairo2 (>= 1.2.4), libcamel1.2-14 (>= 2.27), libdbus-1-3 (>=
         1.0.2), libdbus-glib-1-2 (>= 0.78), libebackend1.2-0 (>= 2.28.1),
         libebook1.2-9 (>= 2.28.1), libecal1.2-7 (>= 2.28.1),
         libedataserver1.2-11 (>= 2.28.1), libedataserverui1.2-8 (>= 2.28.1),
         libegroupwise1.2-13 (>= 2.28.1), libenchant1c2a (>= 1.5),
         libexchange-storage1.2-3 (>= 2.28.1), libfontconfig1 (>= 2.4.0),
         libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.23.2), libgdata-google1.2-1
         (>= 2.28.1), libgdata1.2-1 (>= 2.28.1), libglade2-0 (>= 1:2.6.1),
         libglib2.0-0 (>= 2.22.0), libgnome-desktop-2-11 (>= 1:2.27.3),
         libgnome-pilot2 (>= 2.0.2), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0
         (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0 (>= 1:2.17.90),
         libgtk2.0-0 (>= 2.18.0), libgtkhtml-editor0, libgtkhtml3.14-19 (>=
         3.28.1), libgweather1 (>= 2.28.0), libhal1 (>= 0.5.8.1), libical0 (>=
         0.42), libice6 (>= 1:1.0.0), liblaunchpad-integration1 (>= 0.1.17),
         libldap-2.4-2 (>= 2.4.7), liblpint-bonobo0, libnotify1 (>= 0.4.5),
         libnotify1-gtk2.10, libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>=
         3.12.2~rc1), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.20.0),
         libpisock9, libpisync1, libpopt0 (>= 1.14), libpython2.6 (>= 2.6),
         libsm6, libsoup2.4-1 (>= 2.27.92), libsqlite3-0 (>= 3.6.16),
         libstartup-notification0 (>= 0.10), libusb-0.1-4 (>= 2:0.1.12),
         libx11-6, libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4), gconf2 (>=
         2.12.1-1), evolution-common (= 2.28.1-0ubuntu2), evolution-data-server
         (>= 2.28), evolution-data-server (< 2.29), gnome-icon-theme (>=
         2.19.91), dbus
Recommends: gnome-pilot-conduits (>= 2.0.9), gnome-desktop-data,
            evolution-plugins, evolution-webcal, evolution-documentation (=
            2.28.1-0ubuntu2) | evolution-documentation-en (= 2.28.1-0ubuntu2),
            bogofilter | spamassassin
Suggests: bug-buddy, gnupg, network-manager, evolution-exchange, evolution-dbg,
          evolution-plugins-experimental
Conflicts: evolution-exchange (< 2.21.90), evolution-plugins (< 2.21.90),
           evolution-plugins-experimental (< 2.21.90)
Replaces: evolution-common (< 2.6.2-3), evolution-plugins (<= 2.22.2-1)
Provides: imap-client, mail-reader
Description: groupware suite with mail client and organizer
 Evolution is a groupware suite which integrates mail, calendar, address book,
 to-do list and memo tools. 
 
 Additional features include integration with Exchange and Groupwise servers,
 newsgroup client, LDAP support, web calendars and synchronization with Palm
 devices. 
 
 Evolution is a graphical application that is part of GNOME, and is distributed
 by Novell, Inc. 
 
 See [http://www.novell.com/products/evolution/](http://www.novell.com/products/evolution/) for more information. 
 
 The following plugins belonging to the "base" set are included. 
 * calendar-file 
 * calendar-http 
 * calendar-weather 
 * itip-formatter 
 * plugin-manager 
 * python 
 * default-source 
 * addressbook-file 
 * startup-wizard 
 * mark-all-read 
 * groupwise-features 
 * groupwise-account-setup 
 * webdav-account-setup 
 * mail-account-disable 
 * publish-calendar 
 * caldav 
 * imap-features 
 * google-account-setup 
 * sa-junk-plugin 
 * bogo-junk-plugin 
 * exchange-operations 
 * mono
Homepage: [http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)

---

