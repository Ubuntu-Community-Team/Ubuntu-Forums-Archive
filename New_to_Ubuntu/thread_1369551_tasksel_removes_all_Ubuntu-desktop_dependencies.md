---
title: "tasksel removes all Ubuntu-desktop dependencies"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by rajeshkg on 2010-01-01
Hi,

I&#7743; Rajesh.  I&#7743; using Ubuntu Desktop 9.10 (Karmic).  I installed lamp server using tasksel.  

But when I removed the same using the command :  **[FONT=Courier New][SIZE=2]sudo tasksel remove lamp-server[/SIZE][/FONT]**, it removed desktop dependencies without any warning and this affects my desktop to stop working the next time I reboot.  

Also after removing lamp server, I got the success message when checked in the browser by typing localhost.

Can any one suggest a safer method to remove lamp server 

Thanks in advance, Rajesh

---

### Post by gsmanners on 2010-01-01
I've never used that command, but a safe way to handle removal would be to do this:

```
sudo apt-get remove libwrap0 apache2 libaprutil1-dbd-sqlite3 tcpd libapache2-mod-php5 apache2.2-common apache2-utils php5-common libaprutil1 libaprutil1-ldap php5-mysql mysql-server-core-5.1 libdbi-perl libplrpc-perl mysql-server apache2.2-bin libdbd-mysql-perl libhtml-template-perl libnet-daemon-perl libapr1 mysql-server-5.1 libmysqlclient16 ssl-cert apache2-mpm-prefork mysql-client-5.1 mysql-common
```

Or basically, remove all the AMP stuff in the LAMP stack.

---

### Post by cisco906 on 2010-02-06
Hy!

I use Ubuntu Karmic.
I also installed the lamp-server with the tasksel command, then I wanted to remove it.
I used the command ```
sudo tasksel remove lamp-server
```and this removed the half of my system. ](*,)
Fortunately, I have successfully restored the system in 2 hours with some C code, a lot of terminal using and the dpkg.log. (Thanks GOD [-o<)
I have to run this code:
```
sudo aptitude install amarok bluez-cups ubuntu-desktop splix pxljr openprinting-ppds hpijs hplip cups-driver-gutenprint ghostscript-cups foo2zjs indicator-applet-session indicator-session gdm-guest-session gdm gecko-mediaplayer gnome-applets gnome-session gnome-media gnome-mplayer gnome-orca gstreamer0.10-pulseaudio icedtea6-plugin kde-l10n-engb kde-l10n-hu khelpcenter4 kdemultimedia-kio-plugins libkcddb4 language-support-en language-support-writing-en openoffice.org-thesaurus-en-us pulseaudio-module-x11 pulseaudio-module-gconf pulseaudio-module-bluetooth pulseaudio-esound-compat libcanberra-pulse libgnome-speech7 redland-utils openoffice.org-emailmerge python-uno openoffice.org-hyphenation-en-us openoffice.org-writer openoffice.org-math openoffice.org-impress openoffice.org-gnome openoffice.org-gtk openoffice.org-draw openoffice.org-calc openoffice.org-base-core openoffice.org-core libqt4-sql-mysql pulseaudio-utils libpulse-browse0 mozilla-mplayer mplayer mplayer-nogui vlc-plugin-pulse openjdk-6-jre python-speechd speech-dispatcher libsnmp15 pulseaudio pulseaudio-module-udev libasound2-plugins foomatic-db indicator-messages kdebase-runtime kdebase-runtime-bin-kde4 libplasma3 libknotificationitem1 kdelibs5 libxine1 libxine1-misc-plugins foomatic-db-engine cups indicator-applet gnome-panel gnome-control-center gnome-settings-daemon kdelibs-bin libsoprano4 libpulse-mainloop-glib0 libpulse0 soprano-daemon librdf0
```The code [FONT=Courier New]tasksel remove lamp-server[/FONT] does what it says, it removes everything that the [FONT=Courier New]tasksel install lamp-server[/FONT] command installed, among others the
```
libmysqlclient16
libpq5
mysql-common
libwrap0
ssl-cert
```packages, and if you remove these packages, they remove amarok, openoffice, icedtea, openjdk, ubuntu-desktop and so on...

So dont use the tasksel command for removing lamp-server, use synaptic.

---

### Post by powersurge360 on 2010-04-28
Same problem, except I can't see the terminal (I am able to access it however because sudo reboot now + password works).

Anyone able to write me some blind instructions to reinstall ubuntu-desktop?

EDIT: Got in via recovery mode through the grub. I can't seem to get an internet connection to install ubuntu-desktop though. Any suggestions?

---

### Post by aysiu on 2010-04-28
> **powersurge360 said:**
> 
Anyone able to write me some blind instructions to reinstall ubuntu-desktop? ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo service gdm start
```

---

### Post by powersurge360 on 2010-04-28
Thanks for the help, installing ubuntu-desktop now hopefully it'll be easy to resolve from there. :>

EDIT: Aaaaand it worked. Awesome.

---

### Post by miki4242 on 2010-09-19
Had the same problem myself. It appears that at least the lamp-server task is not additive i.e. adds or removes packages without affecting already installed tasks.
It would be nice if tasksel would check if any of the packages it is about to remove belong to another task.

I also had another problem: trying to reinstall the ubuntu-desktop task (this time I tried with aptitude, thank goodness!) indicated that lots of other packages would be removed. I spent lots of time appending an ever growing list of packages to the aptitude command to minimize the damage.

Tasks need a bit of a makeover, to put it mildly.

---

### Post by oregonbob on 2010-09-29
Man I had this happen on a remote system and after I couldn't get in. There needs to be a BIG WARNING that tasksel should not be used if running desktop. I just tried to add dns-server to a desktop Mint 8 Karmic system. I did 

sudo tasksel, put a checkmark in box next to "DNS Server" then hit "OK".

Without any warning, no prompts, no nothing it removed all desktop and more! Making access impossible. This is as bad as a VIRUS and should be removed and fixed! I can't believe this program tasksel has been left in place as it is.

Is there any command to reverse packages that were removed?

---

### Post by cariboo on 2010-09-29
You could install the ubuntu-desktop meta-package or whatever the equivalent in Mint is, it should re-install all the defaults.

---

### Post by Mofef on 2011-09-20
Hello Folks,

Just had the same Problem (who the hell is the author of tasksel? oO) and solved it the following way:

```
sudo apt-get install $(for i in $(cat /var/log/dpkg.log |grep -oP "(?<=`date +%Y-%m-%d`\s\d\d\:\d\d:\d\d\sremove)\s\S*\s"); do echo -n "$i "; done;)
```

Which basically looks in the dpkg.log for packages removed today and reinstalls them by handing the package-names over to apt-get.
Imho this is the better solution, as it also restores other packages. Just in case there is something missing apart from ubuntu-desktop.

Bye

---

### Post by Jorge_C on 2012-04-26
> **Mofef said:**
> Hello Folks,

Just had the same Problem (who the hell is the author of tasksel? oO) and solved it the following way:

```
sudo apt-get install $(for i in $(cat /var/log/dpkg.log |grep -oP "(?<=`date +%Y-%m-%d`\s\d\d\:\d\d:\d\d\sremove)\s\S*\s"); do echo -n "$i "; done;)
```

Which basically looks in the dpkg.log for packages removed today and reinstalls them by handing the package-names over to apt-get.
Imho this is the better solution, as it also restores other packages. Just in case there is something missing apart from ubuntu-desktop.

Bye

Thanks for that!

A friend of mine using Lubuntu got most of his system removed with no warnings whatsoever when he thought he was simply *installing* a couple of packages (a LAMP server). Very annoying, to say the least.

---

### Post by simona75 on 2012-06-01
I just had exactly the same thing happen trying to install LAMP. Fortunately on a new Ubuntu install but still annoying as has cost me a couple of hours this morning figuring out what exactly happened.

There REALLY needs to be a warning about this. Users like me with a little knowledge - a dangerous thing - who will just run tasksel from the command line without any research are probably most at risk :|

---

### Post by oldos2er on 2012-06-01
Old thread closed.

---

