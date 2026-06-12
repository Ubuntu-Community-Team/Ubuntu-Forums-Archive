---
title: "Remove menu items"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by squrl on 2010-10-20
Is there a way to get rid of items from the applications menu in 10.04 other than in preferences. It wont remove half of the games using the preferences > main menu.

Thanks

---

### Post by cgroza on 2010-10-20
What do you mean? You should be able to remove anything with that from the menu.

---

### Post by squrl on 2010-10-21
Brilliant...

Well it doesn't

---

### Post by A_M_S on 2010-10-21
if you want help you have to be more specific.

How are you trying to remove the icons?

When the procedure fails do you obtain any error messages?

---

### Post by Frogs Hair on 2010-10-21
Right click and select edit menu , this does not remove the app only its icon from the menu.

---

### Post by squrl on 2010-10-21
First go to System > Preferences > Main menu > games then uncheck those I would like to get rid of. They're unchecked now but are still showing when you go to Applications > Games. I'm running 10.04  A reboot didn't change anything

Thanks

---

### Post by yetiman64 on 2010-10-21
> **squrl said:**
> Is there a way to get rid of items from the applications menu in 10.04 other than in preferences. It wont remove half of the games using the preferences > main menu.

Thanks

I think I know what you mean. I like to remove the icons in the games menu for games I don't use.

Firstly detick their entry in main menu as you have indicated you have already done. 

This should leave a <game-name>.desktop file in the folder /home/<user>/.local/share/applications (replace <game-name> & <user> with the appropriate name in your system).
Use CTRL + H to expose the hidden folder .local in your home folder.

For any game that won't disappear, use in terminal,
```
gedit ~/.local/share/applications/<game-name>.desktop
```add or alter (if it already exists) the line, so that it reads,
> NoDisplay=true on saving the <game-name>.desktop file the menu entry should disappear.

If you cannot find a <game-name>.desktop file in your home directory, then copy it to the folder mentioned above from /usr/share/applications and do the above procedure on it. Your home folder applications folder entries override the desktop config files in /usr/share/applications and will not be affected if the games are updated at a later stage (that is, your changes will stick).

Copying the config file from /usr/share/applications is as easy as, right click > copy, then go to your home folder applications folder, and right click > paste.

---

### Post by squrl on 2010-10-22
Thanks it worked like a charm

---

