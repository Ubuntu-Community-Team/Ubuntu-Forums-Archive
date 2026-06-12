---
title: "upgrading to 9.04"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by quarkhirad on 2009-05-02
So i have 8.04 installed on my pc and i want to upgrade to 9.04. Hence i downloaded the alternate cd iso and then using the following command i mounted the iso image 

 ```
sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

```

now the upgrade started and then the following dialogue came up. It said 

Some of the third partie entries in your sources.list were disabled. You can re enable them after the upgrade. 

Does this mean that the sources that i have manually added will be disabled and consequently the programmes that where installed will get uninstalled in my upgrade? i want to know this as i have added a large no of sources to my list and installed a whole pile of softwares. If i have to install it all over again then it will mean a huge amount of effort.

---

### Post by drs305 on 2009-05-02
Removing entries from the repositories doesn't remove software. It removes the ability to contact the third-party repositories to try to find out what updates are available.

You could make a copy of your current sources.list and any list in /sources.list.d so you can copy the third-party lines back into your new sources.list file (s).

[COLOR="DarkRed"]However[/COLOR], if you are doing a clean install any apps you added will NOT be available until you reinstall them!  So yes, you WILL have to reinstall your additional apps.
You can make it easier by making a list of installed apps on your current system, copy it to a location that won't be formatted, and then reinstall them from the new setup.

You can make a list of installed apps with:
```

sudo dpkg --get-selections | grep -v "deinstall&#8221; >$HOME/Desktop/installed-packages

```
Just make sure you copy it from your Desktop to somewhere available after the install.

---

### Post by quarkhirad on 2009-05-02
Ok thanks. So that means that all my software as well as settings remain the same right???? after the upgrade.

---

### Post by drs305 on 2009-05-02
No. I added more to the first post since the repository issue was not going to be the main factor. Doing a clean install is going to be your problem with regard to third-party apps.

If you want to keep all your software and settings, your best option is to do a "network" upgrade online. This can only be done from 8.10.

---

### Post by quarkhirad on 2009-05-17
Ok now i updated and everything. Now just a couple of things

1) I installed blubuntu wallpapers using synaptic but i am not able to see where they are located and hence i cant change my default wall paper

2) I had used compiz settings maneger to add some shortcuts like ifu  i pressed the windows key + t it opened the terminal. Then windows key + s opened system monitor. Then ctrl+alt+a opens the applications menu. I remember there were some 10 or 12 such commands you could configure. I cant figure how to add some new ones. 

3) I installed screenlets. However the widgets are very few does anyone know where to get some of them .

---

### Post by drs305 on 2009-05-17
1) I downloaded the blubuntu-wallpapers and found just one in /usr/share/backgrounds. You can check where files are installed in several ways.

You can hightlight and right click the package in Synaptic and select Properties, Installed Files. It will show where the files of the package have been installed.

You can also look in /var/lib/dpkg/info/blubuntu-wallpapers.list to get the same information.

2) In compiz, you can set some keybindings via the General, Key bindings tab.  There are also keybindings available via gconf-editor's metacity settings. Open gconf-editor and go to the metacity settings. You might want to make changes to the global_keybindings, keybinding_commands, and windows_keybinding tab settings.
```

gconf-editor /apps/metacity/

```

---

