---
title: "Path for installed Applications"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by derbomber_redux on 2011-05-17
Hi All,

I've just started using Ubuntu recently.

I am just starting to get a grip of this, however I'd like to know if I could find a path in the directory for all the installed apps. Like in Windows you would have 'Program Files'

I am trying to install 64 bit flash player onto Ubuntu.

Please help.

CH33RS

---

### Post by NCLI on 2011-05-17
It's usually /usr/bin, but could you please explain what you're trying to do before you do it?

It's usually not a very good idea to mess with the files in there.

---

### Post by mcduck on 2011-05-17
> **derbomber_redux said:**
> Hi All,

I've just started using Ubuntu recently.

I am just starting to get a grip of this, however I'd like to know if I could find a path in the directory for all the installed apps. Like in Windows you would have 'Program Files'

I am trying to install 64 bit flash player onto Ubuntu.

Please help.

CH33RS
There's no such thing, actually.

In Linux, programs aren't installed into a single location like in Windows, instead each file goes to different place, based on that particular file's purpose. (so files are located based on what they do, not based on which program they came with).

For example all documentation, for all your programs, will be in /usr/share/doc, icons go to /usr/share/icons, system-wide config files to /etc, executable files to /usr/bin and so on. The files that have no specific place will usually end in /usr/share/*nameoftheprogram*.

---

### Post by webofunni on 2011-05-17
> **derbomber_redux said:**
> Hi All,

I've just started using Ubuntu recently.

I am just starting to get a grip of this, however I'd like to know if I could find a path in the directory for all the installed apps. Like in Windows you would have 'Program Files'

I am trying to install 64 bit flash player onto Ubuntu.

Please help.

CH33RS

Linux packages installs the files at different path. The binary files goes to /usr/bin, /bin etc and the library files goes to /lib, /usr/lib......

But you can always find the location of installed files from an application. As an example. I am going to find out the installed files of flash plugin 

```

unni@dell:~$ sudo dpkg -l | grep flash
ii  adobe-flashplugin                     10.2.159.1-0natty1                         Adobe Flash Player plugin version 10
unni@dell:~$ sudo dpkg -L adobe-flashplugin
/.
/usr
/usr/lib
/usr/lib/xulrunner
/usr/lib/xulrunner/plugins
/usr/lib/xulrunner-addons
/usr/lib/xulrunner-addons/plugins
/usr/lib/mozilla
/usr/lib/mozilla/plugins
/usr/lib/iceape
/usr/lib/iceape/plugins
/usr/lib/iceweasel
/usr/lib/iceweasel/plugins
/usr/lib/firefox
/usr/lib/firefox/plugins
/usr/lib/midbrowser
/usr/lib/midbrowser/plugins
/usr/lib/adobe-flashplugin
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/share
/usr/share/doc
/usr/share/doc/adobe-flashplugin
/usr/share/doc/adobe-flashplugin/copyright
/usr/share/doc/adobe-flashplugin/changelog.Debian.gz

```

You have to use 

```

sudo dpkg -l | grep name-of-the-package
sudo dpkg -L package-name-that-you-got-from-previous-command
```

Hope this helps

---

### Post by dcsoldschool53 on 2011-05-17
No ubuntu install programs in different place, but a good place to start is in /usr/share/applications and /usr/bin.

---

### Post by wojox on 2011-05-17
Install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by oldos2er on 2011-05-17
> sudo dpkg -L package-name-that-you-got-from-previous-command

Just FYI, there's no need to use 'sudo' when running 'dpkg -L foo'.

---

### Post by derbomber_redux on 2011-05-17
Thanks a lot. That really helped.

---

