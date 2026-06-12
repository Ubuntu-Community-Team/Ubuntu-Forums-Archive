---
title: "kubuntu karmic screensavers dont work... ..."
date: 2010-01-29
forum: New to Ubuntu
---

### Post by techno-mole on 2010-01-29
hello.

Ive been using kubuntu for a few days (felt like a change) and I cant for the life of me get the screensavers to work.

i can preview a screensaver, but i cant get them to activate after any length of time.

I dont have the power saving features on, and I have also tried xscreensavers but nothing seems to work, basically nothing happens when i set a time and wait for the screensaver to activate, I get no screensaver, the screen doesnt even go blank, nothing happens at all.

Ive been searching around and tried a few things, but nothing has worked as yet, so I though I would ask on here.
I would be grateful for any advice.

cheers

---

### Post by Psumi on 2010-01-29
So you solved it, what steps did you take?

---

### Post by techno-mole on 2010-01-29
basically i got rid of the kscreensaver stuff and installed the xscreensaver (i used synaptic) and then i followed these steps from here - ```
http://www.jwz.org/xscreensaver/man1.html
``` about halfway down the page theres a section for what to configure to get it to run with kde, its pretty simple, you just have to create a couple of files and put them in the right place.

these are the steps - ```
USING KDE
    KDE also has invented their own screen saver framework instead of simply using xscreensaver. To replace the KDE screen saver with xscreensaver, do the following:

        1: Turn off KDE's screen saver.
         	Open the ``Control Center'' and select the ``Appearance & Themes / Screensaver'' page. Un-check ``Start Automatically''.

        2: Find your Autostart directory.
         	Open the ``System Administration -> Paths'' page, and see what your ``Autostart path'' is set to: it will probably be ~/.kde/Autostart/ or something similar.

        3: Make xscreensaver be an Autostart program.
         	Create a .desktop file in your autostart directory called xscreensaver.desktop that contains the following five lines:

              [Desktop Entry]
              Exec=xscreensaver
              Name=XScreenSaver
              Type=Application
              X-KDE-StartupNotify=false

        4: Make the various "lock session" buttons call xscreensaver.
         	Replace the file kdesktop_lock or krunner_lock or kscreenlocker in /usr/bin/ (or possibly in /usr/kde/3.5/bin/ or possibly in /usr/lib/kde4/libexec/ or /usr/libexec/kde4/, depending on the distro and phase of the moon) with these two lines:

              #!/bin/sh
              xscreensaver-command -lock

        Make sure the file is executable (chmod a+x). 
```

and these are the packages i installed using synaptic - ```
xscreensaver,xscreensaver-gl,xscreensaver-data,xscreensaver-gl-extra,xscreensaver-data-extra,
```

---

