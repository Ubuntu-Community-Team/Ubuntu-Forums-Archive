---
title: "Where is VirtualBox?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by corncob on 2009-11-19
I recently made a clean install of 9.10.  Yesterday I installed VirtualBox from [http://www.virtualbox.com](http://www.virtualbox.com) and it said I was successful but I can't find the launcher for it.  In 9.04 it was in System Tools under the Applications menu.  I did save my 9.04 home folder to an external hard drive thinking, among other things, how nice it would be if I didn't have to reinstall XP but I'm wondering if XP is even there.

---

### Post by philinux on 2009-11-19
Right click ubuntu logo top left. Edit Menus. You may have to tick system tools to activate that menu.

---

### Post by tony1212 on 2009-11-19
Hi 

I also had this problem recently when I did a fresh install, but I logged off and back on again and System Tools then showed in the Applications menu, a system restart will achieve the same end.

---

### Post by a94060 on 2009-11-19
You may need to recreate the shortcut. You can always verify if its there by running "virtualbox" in the terminal. If you restored your home folder, press CTRL+H on the keyboard to see hidden folders and go to the .VirtualBox folder and check if your xp harddisk exists

---

### Post by corncob on 2009-11-19
> **philinux said:**
> Right click ubuntu logo top left. Edit Menus. You may have to tick system tools to activate that menu.

This I did and VirtualBox is there and checked along with BOINC Manager which does show up in the System Tools under the Applications menu.  Trying to figure out how to get the virtualbox launcher over there or on the menu bar or something.
I have rebooted but no joy.
.VirtualBox/HardDisks/WindowsXP.vdi (size 9.5 GB) does exist so it looks like I have saved my XP installation maybe.
Running virtualbox in Terminal gave the following:
> corncob@eeebox:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt
virtualbox: command not found
I'm thinking of doing what it says
```
sudo apt-get install virtualbox-ose-qt
```
unless you-all have a better idea.

---

### Post by Shpongle on 2009-11-19
you wont have to install xp your hdi will still work , try remove vb and reinstall , also run the compile kernel option when asked

i had the same prob but i just restarted and it was there

---

### Post by NoaHall on 2009-11-19
Hm. Try "locate vitualbox". See what it shows.

---

### Post by corncob on 2009-11-19
> **NoaHall said:**
> Hm. Try "locate vitualbox". See what it shows.

It shows a lot.  Seems like the top part scrolled off the Terminal window.

> lib/virtualbox/sdk/bindings/xpcom/python/xpcom/nsError.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/primitives.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/primitives.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/vboxxpcom.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/vboxxpcom.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/xpcom_consts.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/xpcom_consts.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/xpt.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/xpt.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/client/__init__.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/client/__init__.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/__init__.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/__init__.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/enumerator.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/enumerator.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/factory.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/factory.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/loader.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/loader.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/module.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/module.pyc
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/policy.py
/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/server/policy.pyc
/usr/share/virtualbox
/usr/share/app-install/desktop/virtualbox-ose.desktop
/usr/share/applications/virtualbox.desktop
/usr/share/doc/virtualbox-3.0
/usr/share/doc/virtualbox-3.0/LICENSE
/usr/share/doc/virtualbox-3.0/License-7.html
/usr/share/doc/virtualbox-3.0/UserManual.pdf
/usr/share/doc/virtualbox-3.0/VirtualBox.chm
/usr/share/doc/virtualbox-3.0/changelog.Debian.gz
/usr/share/doc/virtualbox-3.0/copyright
/usr/share/lintian/overrides/virtualbox-3.0
/usr/share/pyshared-data/virtualbox-3.0
/usr/share/virtualbox/VBoxGuestAdditions.iso
/usr/share/virtualbox/VBoxSysInfo.sh
/usr/share/virtualbox/nls
/usr/share/virtualbox/rdesktop-vrdp-keymaps


---

### Post by NoaHall on 2009-11-19
That's why! It's virtualbox-3.0 :D If virtualbox-3.0 doesn't work, try typing virtualbox and then use tab to see the correct code to run it :)

---

### Post by corncob on 2009-11-19
> **DillByrne said:**
> you wont have to install xp your hdi will still work , try remove vb and reinstall , also run the compile kernel option when asked

i had the same prob but i just restarted and it was there

I should be able to remove and reinstall vb.  Synaptic Package Manager says its installed so I'll go from there.  My XP is safe on the external drive (I hope).  Gonna turn the computer off for the night.  Maybe when I turn it on in the morning everything will be fixed lol.

---

### Post by corncob on 2009-11-19
> **NoaHall said:**
> That's why! It's virtualbox-3.0 :D If virtualbox-3.0 doesn't work, try typing virtualbox and then use tab to see the correct code to run it :)

```
corncob@eeebox:~$ virtualbox-3.0
virtualbox-3.0: command not found
```

pressing [TAB] gives nothing.

---

### Post by NoaHall on 2009-11-19
> **corncob said:**
> ```
corncob@eeebox:~$ virtualbox-3.0
virtualbox-3.0: command not found
```

pressing [TAB] gives nothing.

Oh wait! Try again with "vbox" or maybe "VirtualBox" with the same case I've used._

---

### Post by Gresley on 2009-11-19
The command to start virtualbox in terminal is case sensitive.

Try typing VirtualBox at the command prompt.

I have a properly installed working virtualbox. If I get the capitalisation wrong at the command prompt I get exactly the same message you did

---

### Post by themusicalduck on 2009-11-19
I've had this problem quite a few times with virtualbox. Never any other programs, only VBox.

I just uninstall it and re-install it until it eventually appears in the menu.

---

### Post by corncob on 2009-11-20
> **Gresley said:**
> The command to start virtualbox in terminal is case sensitive.

Try typing VirtualBox at the command prompt.

I have a properly installed working virtualbox. If I get the capitalisation wrong at the command prompt I get exactly the same message you did

VirtualBox did work!  Also, after having the computer shutdown all night it is appearing in the menu.  Maybe its best to turn the computer off for a while rather than just clicking on 'restart', which I did a couple times to no avail.  I usually leave the computer on all the time as its running several projects on BOINC.
Thanks everyone.  I'll mark the thread as solved.

---

### Post by a94060 on 2009-11-20
Glad to hear it worked

---

