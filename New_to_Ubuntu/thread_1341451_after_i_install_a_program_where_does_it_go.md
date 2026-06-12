---
title: "after i install a program where does it go?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by expxe on 2009-11-29
where the program folder? and how to do add the program to the start menu? how do i run the program?

this should be a default feature in linux..... take a hint from the great windows

---

### Post by Cheesemill on 2009-11-29
Which program and how did you install it?

---

### Post by BenAshton24 on 2009-11-29
urgh I rly don't like how you phrase your posts, they all seem like subtle jabs at Ubuntu for not being like windows... It's not supposed to be and lets hope that it never tries to be!

As for your question, programs go to many places...

/usr/bin/
/usr/share/
/usr/local/share
/user/local/sbin
/home/$USER/.program

etc etc etc

It depends on the developer

---

### Post by Garyhans on 2009-11-29
It goes to never never land..  Been there many times.. someone writes a program..  and doesn't have the time.. to make the link inserted in the menu.. I don't get that..  myself.

---

### Post by SunnyRabbiera on 2009-11-29
Usually the apps install to /usr/bin.
Keep in mind not all apps create menu entries, some are command line based or sometimes the menu entries are incorrect.
And this issue is on your so called "great" windows too, if a app in windows does not have a installer .exe it does not create menu entries.

---

### Post by expxe on 2009-11-29
> **Cheesemill said:**
> Which program and how did you install it?

i had to install wicd from tar (normally if i installed it from double click it would show up in the start menu). so now i am looking for it after i needed to install it the hard aka needlessly-complicated-linux way. the programmer who wrote wicd was probably a smart guy but he just needs to get up and use a windows machine once in a while. it will blow his mind, it will show him how easy things can be. we arn't computing in the 80's anymore he needs to get up to speed, dinosaurs like him are holding the big L back.

i would like to access all the rest of the default installed programs that arn't in the start menu but i know are installed, how do i do that? and how do i add it to them start menu?

---

### Post by Garyhans on 2009-11-29
Ubuntu's Goal.. is not to require command line base..  and it will invite more users. Let's get with it eh.

---

### Post by ciaran2013 on 2009-11-29
im new to ubuntu i've just installed the 9.10 version onto my laptop but im having alot of trouble its constantly stalling when going threw folders and when i try to load a cd it tells me it cannot find zipfile directory can anyone help me plz

---

### Post by Alex Libman on 2009-11-29
Run:

```
dpkg -L package-name
```

-or-

```
dpkg --contents package-file.deb
```


Or, alternatively, you can launch [synaptic]("http://en.wikipedia.org/wiki/Synaptic_%28software%29"), find the program you've just installed, highlight it, and select the "Installed files" tab above the bottom-right portion of the window.  (If you don't see tabs there go to the Settings menu -> Preferences -> General -> Appearance, and make sure "show package properties in the main window" is checked.)

The use of the this [filesystem hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") predates the invention of fire, but the standard stuck.  There are a few distros that are trying to reform it to store each package in a separate folder, however: [GoboLinux]("http://en.wikipedia.org/wiki/GoboLinux"), [PC-BSD]("http://en.wikipedia.org/wiki/PC-BSD"), and possibly some others.

---

### Post by Cheesemill on 2009-11-29
> **expxe said:**
> i had to install wicd from tar (normally if i installed it from double click it would show up in the start menu). so now i am looking for it after i needed to install it the hard aka needlessly-complicated-linux way. the programmer who wrote wicd was probably a smart guy but he just needs to get up and use a windows machine once in a while. it will blow his mind, it will show him how easy things can be. we arn't computing in the 80's anymore he needs to get up to speed, dinosaurs like him are holding the big L back.

i would like to access all the rest of the default installed programs that arn't in the start menu but i know are installed, how do i do that? and how do i add it to them start menu?

If you installed it from source then it will be wherever you installed it, for programs installed from the Software Centre you can use the which command to find out, for example:
```
which firefox
```
returns
```
/usr/bin/firefox
```

---

### Post by BenAshton24 on 2009-11-29
just create an item in your menu with the command: wicd-client

I'm sorry but this is all in the installation instructions.... [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by SunnyRabbiera on 2009-11-29
> **expxe said:**
> i had to install wicd from tar (normally if i installed it from double click it would show up in the start menu). so now i am looking for it after i needed to install it the hard aka needlessly-complicated-linux way. the programmer who wrote wicd was probably a smart guy but he just needs to get up and use a windows machine once in a while. it will blow his mind, it will show him how easy things can be. we arn't computing in the 80's anymore he needs to get up to speed, dinosaurs like him are holding the big L back.

i would like to access all the rest of the default installed programs that arn't in the start menu but i know are installed, how do i do that? and how do i add it to them start menu?

You sir are asking for trouble...
Look pal not everything has binary, even in windows you might have to compile software.
All you had to do to install wicd is install it from here:
[http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)
No compiling, none of that.
Look the reason why source code is given is because not all linuxes use the same installer or sometimes they dont have the same libraries.
This is because linux is open source and people code it in any fashion they desire.
There is no one huge greedy company behind it, linux is INDEPENDENTLY developed and the coders do all this great work for NO PAY and no help from anyone.
You are oblivious to these things and need to learn that the only OS that is like 100% like windows is windows, and by your sig you are a hypocrite.
If windows is so bloody perfect for you go use it, have fun with the viruses, the malware, the security flaws all handled by a company that cares more about money then the customers who use their OS...

---

### Post by howefield on 2009-11-29
> **SunnyRabbiera said:**
> You sir are asking for trouble..... ( ect, ect , ect)

He is on a wind up, and you are falling for it.

---

### Post by BenAshton24 on 2009-11-29
> **SunnyRabbiera said:**
> You sir are asking for trouble...
Look pal not everything has binary, even in windows you might have to compile software.
All you had to do to install wicd is install it from here:
[http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)
No compiling, none of that.
Look the reason why source code is given is because not all linuxes use the same installer or sometimes they dont have the same libraries.
This is because linux is open source and people code it in any fashion they desire.
There is no one huge greedy company behind it, linux is INDEPENDENTLY developed and the coders do all this great work for NO PAY.
You are oblivious, and by your sig you are a hypocrite.
If windows is so bloody perfect for you go use it, have fun with the viruses, the malware, the security flaws all handled by a company t5hat cares more about money then the customers who use their OS...

+1

Also, if we're talking about ease of use then you can just install wicd by clicking this link below... that's all you have to do...

[apt:wicd]("apt:wicd")

Wasn't that just the hardest thing that you've ever had to do?

-.-

---

### Post by SunnyRabbiera on 2009-11-29
> **howefield said:**
> He is on a wind up, and you are falling for it.

Yes but the OP is being a total <snip>, he seems not to care about how things work or why... but one needs to in the computer world, you dont have to be a mechanic to drive a car, but it does help to know how the parts work.

---

### Post by cariboo on 2009-11-29
Please keep it respectful.

---

### Post by SunnyRabbiera on 2009-11-29
Yeh but the OP is really making it tough

---

### Post by expxe on 2009-11-29
> **Garyhans said:**
> Ubuntu's Goal.. is not to require command line base..  and it will invite more users. Let's get with it eh.

maybe in version ubuntu 12.10, but then ubuntu will be competing with windows 8, what a beast that OS will be :shock:

> **Alex Libman said:**
> Run:

```
dpkg -L package-name
```

i got: ```
/etc
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/wicd.conf
/etc/wicd
/etc/wicd/encryption
/etc/wicd/encryption/templates
/etc/wicd/encryption/templates/eap
/etc/wicd/encryption/templates/wep-shared
/etc/wicd/encryption/templates/wpa-psk
/etc/wicd/encryption/templates/wep-passphrase
/etc/wicd/encryption/templates/ttls
/etc/wicd/encryption/templates/eap-tls
/etc/wicd/encryption/templates/wep-hex
/etc/wicd/encryption/templates/peap
/etc/wicd/encryption/templates/peap-tkip
/etc/wicd/encryption/templates/wpa
/etc/wicd/encryption/templates/active
/etc/wicd/encryption/templates/leap
/etc/xdg
/etc/xdg/autostart
/etc/xdg/autostart/wicd-tray.desktop
/etc/init.d
/etc/init.d/wicd
/etc/default
/etc/default/wicd
/var/log/wicd

``````
dpkg --contents package-file.deb
```above code didn't work, i replaced it with wicd.deb and still nothing

> **Alex Libman said:**
> 
Or, alternatively, you can launch [synaptic]("http://en.wikipedia.org/wiki/Synaptic_%28software%29"), find the program you've just installed, highlight it, and select the "Installed files" tab above the bottom-right portion of the window.  (If you don't see tabs there go to the Settings menu -> Preferences -> General -> Appearance, and make sure "show package properties in the main window" is checked.)


i see the files, now what? 

> **Alex Libman said:**
> 
The use of the this [filesystem hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") predates the invention of fire, but the standard stuck.  There are a few distros that are trying to reform it to store each package in a separate folder, however: [GoboLinux]("http://en.wikipedia.org/wiki/GoboLinux"), [PC-BSD]("http://en.wikipedia.org/wiki/PC-BSD"), and possibly some others.




as long as there is progress i am ok with that. linux can improve, we all need to have faith. remember the old days when MS had a terrible rep with their operating systems and linux was running circles around MS? and now what? look at windows 7, a masterpiece. and ubuntu is still in the gutter. someday ubuntu will make itself out to be something too. i hope.




> **Cheesemill said:**
> If you installed it from source then it will be wherever you installed it, for programs installed from the Software Centre you can use the which command to find out, for example:
```
which firefox
```returns
```
/usr/bin/firefox
```

i got :
```
$ which wicd
/usr/sbin/wicd

```> **BenAshton24 said:**
> just create an item in your menu with the command: wicd-client

I'm sorry but this is all in the installation instructions.... [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

i got: ```
$ wicd-client
Has notifications support True
Loading...
Connecting to daemon...
Connected.
Done loading.
^CTraceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 827, in <module>
    main(sys.argv)
  File "/usr/lib/wicd/wicd-client.py", line 88, in wrapper
    return func(*args, **kwargs)
  File "/usr/lib/wicd/wicd-client.py", line 823, in main
    mainloop.run()
KeyboardInterrupt
$ wicd-client
Has notifications support True
Loading...
Connecting to daemon...
Connected.
Done loading.

```now i see the link in the start menu. (i will admit that i do not know which of the above commands/instructions did it). and look at all the work above what had to be done....for a simple shortcut. even the most hardcore linux fanboy would agree with me that linux is NEEDLESSLY complicated.

mark shuttleworth would be sad if he had to witness this thread. this is not linux for human beings.

---

### Post by overdrank on 2009-11-29
Ok to the op and all that reply. As cariboo907 has pointed out keep the COC in mind when posting or the thread will be closed.

---

### Post by Alex Libman on 2009-11-29
The `dpkg --contents` is for when you have the actual .deb file in the local directory (as opposed to having installed the package through APT).


Hmm, I'm surprised installing that package didn't update your menus automatically.

I don't have the [wicd]("http://en.wikipedia.org/wiki/Wicd_%28Linux_Network_Manager%29") package installed, but I can use `apt-file show wicd` to get the list of files it contains:

```
wicd: /etc/dbus-1/system.d/wicd.conf
wicd: /etc/default/wicd
wicd: /etc/init.d/wicd
wicd: /etc/wicd/encryption/templates/active
wicd: /etc/wicd/encryption/templates/eap
wicd: /etc/wicd/encryption/templates/eap-tls
wicd: /etc/wicd/encryption/templates/leap
wicd: /etc/wicd/encryption/templates/peap
wicd: /etc/wicd/encryption/templates/peap-tkip
wicd: /etc/wicd/encryption/templates/ttls
wicd: /etc/wicd/encryption/templates/wep-hex
wicd: /etc/wicd/encryption/templates/wep-passphrase
wicd: /etc/wicd/encryption/templates/wep-shared
wicd: /etc/wicd/encryption/templates/wpa
wicd: /etc/wicd/encryption/templates/wpa-psk
wicd: /etc/xdg/autostart/wicd-tray.desktop
wicd: /usr/bin/wicd-client
wicd: /usr/bin/wicd-curses
wicd: /usr/lib/pm-utils/sleep.d/55wicd
wicd: /usr/lib/wicd/backends/be-external.py
wicd: /usr/lib/wicd/backends/be-ioctl.py
wicd: /usr/sbin/wicd
wicd: /usr/share/applications/wicd.desktop
wicd: /usr/share/doc/wicd/NEWS.Debian.gz
wicd: /usr/share/doc/wicd/README.Debian
wicd: /usr/share/doc/wicd/changelog.Debian.gz
wicd: /usr/share/doc/wicd/changelog.gz
wicd: /usr/share/doc/wicd/copyright
wicd: /usr/share/icons/hicolor/128x128/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/16x16/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/192x192/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/22x22/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/24x24/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/32x32/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/36x36/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/48x48/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/64x64/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/72x72/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/96x96/apps/wicd-client.png
wicd: /usr/share/icons/hicolor/scalable/apps/wicd-client.svg
wicd: /usr/share/locale/ar_EG/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/bg/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ca/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/cs/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/da/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/de/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/de_DE/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/el/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/eo/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es_CL/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es_ES/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es_GT/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es_MX/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es_NI/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/es_VE/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/et/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/eu/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/fa/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/fi/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/fr/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/gl/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/he/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/hu/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/id/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/it/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/it_IT/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ja/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ka/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/kk/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ko/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/lt/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/lv/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ml/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/nl/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/nl_NL/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/pl/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/pt/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/pt_BR/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ro/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ru/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/ru_RU/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/sk/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/sl/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/sr/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/sv/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/te/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/tr/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/uk/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/vi/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/zh_CN/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/zh_HK/LC_MESSAGES/wicd.mo
wicd: /usr/share/locale/zh_TW/LC_MESSAGES/wicd.mo
wicd: /usr/share/man/man1/wicd-client.1.gz
wicd: /usr/share/man/man5/wicd-manager-settings.conf.5.gz
wicd: /usr/share/man/man5/wicd-wired-settings.conf.5.gz
wicd: /usr/share/man/man5/wicd-wireless-settings.conf.5.gz
wicd: /usr/share/man/man8/wicd-client.8.gz
wicd: /usr/share/man/man8/wicd-curses.8.gz
wicd: /usr/share/man/man8/wicd.8.gz
wicd: /usr/share/menu/wicd
wicd: /usr/share/pixmaps/wicd.xpm
wicd: /usr/share/pixmaps/wicd/bad-signal-lock.png
wicd: /usr/share/pixmaps/wicd/bad-signal.png
wicd: /usr/share/pixmaps/wicd/both-bad-signal-lock.png
wicd: /usr/share/pixmaps/wicd/both-bad-signal.png
wicd: /usr/share/pixmaps/wicd/both-good-signal-lock.png
wicd: /usr/share/pixmaps/wicd/both-good-signal.png
wicd: /usr/share/pixmaps/wicd/both-high-signal-lock.png
wicd: /usr/share/pixmaps/wicd/both-high-signal.png
wicd: /usr/share/pixmaps/wicd/both-low-signal-lock.png
wicd: /usr/share/pixmaps/wicd/both-low-signal.png
wicd: /usr/share/pixmaps/wicd/good-signal-lock.png
wicd: /usr/share/pixmaps/wicd/good-signal.png
wicd: /usr/share/pixmaps/wicd/high-signal-lock.png
wicd: /usr/share/pixmaps/wicd/high-signal.png
wicd: /usr/share/pixmaps/wicd/idle-bad-signal-lock.png
wicd: /usr/share/pixmaps/wicd/idle-bad-signal.png
wicd: /usr/share/pixmaps/wicd/idle-good-signal-lock.png
wicd: /usr/share/pixmaps/wicd/idle-good-signal.png
wicd: /usr/share/pixmaps/wicd/idle-high-signal-lock.png
wicd: /usr/share/pixmaps/wicd/idle-high-signal.png
wicd: /usr/share/pixmaps/wicd/idle-low-signal-lock.png
wicd: /usr/share/pixmaps/wicd/idle-low-signal.png
wicd: /usr/share/pixmaps/wicd/low-signal-lock.png
wicd: /usr/share/pixmaps/wicd/low-signal.png
wicd: /usr/share/pixmaps/wicd/no-signal.png
wicd: /usr/share/pixmaps/wicd/receiving-bad-signal-lock.png
wicd: /usr/share/pixmaps/wicd/receiving-bad-signal.png
wicd: /usr/share/pixmaps/wicd/receiving-good-signal-lock.png
wicd: /usr/share/pixmaps/wicd/receiving-good-signal.png
wicd: /usr/share/pixmaps/wicd/receiving-high-signal-lock.png
wicd: /usr/share/pixmaps/wicd/receiving-high-signal.png
wicd: /usr/share/pixmaps/wicd/receiving-low-signal-lock.png
wicd: /usr/share/pixmaps/wicd/receiving-low-signal.png
wicd: /usr/share/pixmaps/wicd/signal-100.png
wicd: /usr/share/pixmaps/wicd/signal-25.png
wicd: /usr/share/pixmaps/wicd/signal-50.png
wicd: /usr/share/pixmaps/wicd/signal-75.png
wicd: /usr/share/pixmaps/wicd/transmitting-bad-signal-lock.png
wicd: /usr/share/pixmaps/wicd/transmitting-bad-signal.png
wicd: /usr/share/pixmaps/wicd/transmitting-good-signal-lock.png
wicd: /usr/share/pixmaps/wicd/transmitting-good-signal.png
wicd: /usr/share/pixmaps/wicd/transmitting-high-signal-lock.png
wicd: /usr/share/pixmaps/wicd/transmitting-high-signal.png
wicd: /usr/share/pixmaps/wicd/transmitting-low-signal-lock.png
wicd: /usr/share/pixmaps/wicd/transmitting-low-signal.png
wicd: /usr/share/pixmaps/wicd/wired-gui.svg
wicd: /usr/share/pixmaps/wicd/wired.png
wicd: /usr/share/python-support/wicd.private
wicd: /usr/share/wicd/Wicd-1.6.1.egg-info
wicd: /usr/share/wicd/autoconnect.py
wicd: /usr/share/wicd/configscript.py
wicd: /usr/share/wicd/configscript_curses.py
wicd: /usr/share/wicd/curses_misc.py
wicd: /usr/share/wicd/monitor.py
wicd: /usr/share/wicd/netentry_curses.py
wicd: /usr/share/wicd/prefs_curses.py
wicd: /usr/share/wicd/suspend.py
wicd: /usr/share/wicd/wicd-client.py
wicd: /usr/share/wicd/wicd-curses.py
wicd: /usr/share/wicd/wicd-daemon.py
wicd: /usr/share/wicd/wicd.glade
wicd: /usr/share/wicd/wicd/__init__.py
wicd: /usr/share/wicd/wicd/backend.py
wicd: /usr/share/wicd/wicd/configmanager.py
wicd: /usr/share/wicd/wicd/dbusmanager.py
wicd: /usr/share/wicd/wicd/gui.py
wicd: /usr/share/wicd/wicd/guiutil.py
wicd: /usr/share/wicd/wicd/logfile.py
wicd: /usr/share/wicd/wicd/misc.py
wicd: /usr/share/wicd/wicd/netentry.py
wicd: /usr/share/wicd/wicd/networking.py
wicd: /usr/share/wicd/wicd/prefs.py
wicd: /usr/share/wicd/wicd/translations.py
wicd: /usr/share/wicd/wicd/wnettools.py
wicd: /usr/share/wicd/wicd/wpath.py
```That means you should be able to execute:

```
sudo /etc/init.d/wicd start
```... to start the [daemon]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29") (UNIX equivalent of [Windows service]("http://en.wikipedia.org/wiki/Windows_service")) - which actually should be started by default.  The /usr/sbin/wicd is probably used by that service.  You can then run:

```
wicd-client
```... to launch the client interface (are you sure it didn't create a menu shortcut for this?)


**[COLOR=DarkRed](EDIT:   I didn't see your last post, [/COLOR]****[COLOR=DarkRed]never mind[/COLOR]****[COLOR=DarkRed].)[/COLOR]**

---

