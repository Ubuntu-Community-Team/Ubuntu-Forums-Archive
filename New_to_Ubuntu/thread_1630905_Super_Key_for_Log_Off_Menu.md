---
title: "Super Key for Log Off Menu"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by rickcjmac on 2010-11-25
Hi all :) I am trying to find a way to use just the "windows" key to bring up the log off menu. I have looked all over and only found how to use this key to bring up the panel main menu. Any help is much appreciated :) thanks.

Richard
Ubuntu 10.10
HP Pavilion dv2000

---

### Post by libssd on 2010-11-25
> **rickcjmac said:**
> Hi all :) I am trying to find a way to use just the "windows" key to bring up the log off menu. I have looked all over and only found how to use this key to bring up the panel main menu. Any help is much appreciated :) thanks.


Does it have to be the "Windows" key that leads to the logoff/shutdown choices? Default is Ctrl-Alt-Del, which seems pretty intuitive (?) for people coming to Linux from Windows. 

I want to see the desktop far more often than I want to shutdown/restart, so I changed the behavior of the Windows key to hide all open windows and show the desktop:

gconf-editor

Default:
apps > metacity > global_keybindings > show_desktop <Control><Alt>d

Change to:
apps > metacity > global_keybindings > show_desktop Super_L

After making this change, Keyboard Shortcuts will show:
Hide all normal windows and set focus to the desktop		Super L

---

### Post by rickcjmac on 2010-11-27
Thank you for your quick response Libssd :)
I know it's a fairly odd thing to want the Windows key to bring up the Log Iff Menu, but as I am using a laptop and frequently running to and from school this would prove quite helpful. 
Your method of changing the use of the Windows key through the gconf-editor would work perfect. The only problem I have now is that I can't find the keybindings for the Log Off Menu. If anyone knows where that is located that would be great :)
Thanks again for your help Libssd

---

### Post by libssd on 2010-11-27
> **rickcjmac said:**
> Thank you for your quick response Libssd :)
The only problem I have now is that I can't find the keybindings for the Log Off Menu. If anyone knows where that is located that would be great :)
Thanks again for your help Libssd
That's why I didn't answer that particular question -- I couldn't find a keybinding either.;)

---

### Post by rickcjmac on 2010-12-26
Finally found a post that helped.

[http://ubuntuforums.org/showthread.php?t=1118861](http://ubuntuforums.org/showthread.php?t=1118861)

> - Open a terminal or press ALT+F2, run gconf-editor.
- Browse to apps > metacity > global_keybindings. Double-click on run_command_1 and change the value to Super_L (in the origional post this was <Control><Alt>Delete)
- Now go to keybinding_commands, double-click on command_1 and change the value to gnome-session-save --shutdown-dialog. You can close this window now and test out the new keybinding

This particular forum was changing the control+alt+delete purpose, but it worked out great for this too.

The right "super key" can be used too in the same manner with Super_R as its run-command value.

---

### Post by libssd on 2010-12-26
Congratulations. Persistence pays off.

---

