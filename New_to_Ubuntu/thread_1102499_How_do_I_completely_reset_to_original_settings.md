---
title: "How do I completely reset to original settings?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by specialedster14 on 2009-03-21
As this is my first experience with any linux I messed around with some mouse/keyboard settings and I don't really like them and now I'd like to just restore to the original installed ubuntu (without any of my changes).  How do I do this?

---

### Post by InfectedWithDrew on 2009-03-21
Some menus, such as the themes, will let you revert to default.

But for the most part you'll have to set them back yourself or you'll have to reinstall.  To the extent of my knowledge there's no "reset" button.

----------------
Now playing: [Nonpoint - Get Inside](http://www.foxytunes.com/artist/nonpoint/track/get+inside)

---

### Post by AndyCooll on 2009-03-21
You can also delete the files in your home directory.

Places > Home Folder. Then Ctrl+H to show your hidden files. Then Ctrl+A to select all files. Hit the delete button. Now logout and back in again,and you should be back to default settings.

:cool:

---

### Post by coolaj86 on 2009-03-21
You can move all of your configuration files to another directory and restore the ones that you find you actually wanted - perhaps your mozilla firefox profile, for example.
```
Applications > Accessories > Terminal
mkdir -p ~/Desktop/Old_Settings
mv ~/.[a-zA-Z]* ~/Desktop/Old_Settings
```

the 'dot files' of Linux are similar to OS X's 'Library' files or Windows's 'Local Settings' - they hold all of the configuration data for your user.

Because you can never change a system-wide setting without entering in your administrator password, if you create a new account you will also get a 'clean slate'.

You can also restore some deeper configuration issues by re-installing the desktop.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by binbash on 2009-03-21
If you are talking about user settings not system, you can create a new username and delete old one.

---

