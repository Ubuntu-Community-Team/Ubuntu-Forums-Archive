---
title: "&quot;kdesu dolphin&quot; doesn't always work?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Gotaro on 2009-01-28
I don't know when it does or doesn't, but sometimes when I alt+f2, "kdesu dolphin" I get this message at the bottom of the dolphin window: "Could not start process Cannot talk to klauncher: The name org.kde.launcher was not provided by any .service files."  All "places" then appear blank.  I just tried alt+f2, "kdesudo dolphin" and received the same message.

Here is the terminal output:
```
gotaro@gotaro-linux:~$ kdesudo dolphin
"/usr/bin/dolphin(7073)" Error in thread 140686352090864 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(7073)" Error in thread 140686352090864 : "QLocalSocket::connectToServer: Invalid name"
dolphin(7073) <unnamed>::GlobalModelContainer::init: Failed to connect to Nepomuk server via local socket "/root/.kde/share/apps/nepomuk/socket"
dolphin(7073): Attempt to use QAction "close_tab" with KXMLGUIFactory!
dolphin(7073): Attempt to use QAction "show_info_panel" with KXMLGUIFactory!
dolphin(7073): Attempt to use QAction "show_folders_panel" with KXMLGUIFactory!
dolphin(7073): Attempt to use QAction "show_terminal_panel" with KXMLGUIFactory!
dolphin(7073): Attempt to use QAction "show_places_panel" with KXMLGUIFactory!
```

Any suggestions?

---

### Post by Gotaro on 2009-01-29
Any help is appreciated!  Now I can't get it to work at all..  But I want to make changes to the root folder! :(

---

### Post by Monkeybells on 2009-01-29
Sorry, not sure how to fix the problem. I have it too and I think it's fairly common.
First, I think the command kdesudo is now prefered over kdesu when opening programs with root permission.
Second, I've found that opening Konqueror straight after encountering the problem you described makes Dolphin work. You have to keep Dolphin open when you open Konqueror and then keep Konqueror open for the duration of the time you work with Dolphin.

Hope this helps.

---

### Post by Gotaro on 2009-01-29
> **Monkeybells said:**
> Sorry, not sure how to fix the problem. I have it too and I think it's fairly common.
First, I think the command kdesudo is now prefered over kdesu when opening programs with root permission.
Second, I've found that opening Konqueror straight after encountering the problem you described makes Dolphin work. You have to keep Dolphin open when you open Konqueror and then keep Konqueror open for the duration of the time you work with Dolphin.

Hope this helps.
Thanks!  It did work.  I had to open Konqueror with kdesudo, though.  Just clicking the icon didn't work.  But if this is the fix, then I should probably just use Konqueror in the first place lol!

---

### Post by Angelos72 on 2009-06-03
Try running Dolphin using this line:

```
kdesudo dbus-launch dolphin
```

You could create an item in the menu and name "Dolphin-Root" (or whatever suits you), so you can start it easily.

This is a known kde bug

[https://bugs.kde.org/show_bug.cgi?id=165268](https://bugs.kde.org/show_bug.cgi?id=165268)

---

