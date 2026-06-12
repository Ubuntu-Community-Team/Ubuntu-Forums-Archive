---
title: "ctrl-alt-del shudown question"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by mvalviar on 2009-04-07
I'm using intrepid. Is there a way to re-assign ctrl-alt-del so that it brings up the shutdown dialog instead of the log-off dialog? I want to be able to do shutdown my computer using ctrl-alt-del-enter combination instead of grabbing the mouse and clicking the fusa. I used to be able to do that in hardy (ctrl-alt-del-up-enter).

---

### Post by HermanAB on 2009-04-07
Yes, I'm sure there is a way.  However, figuring out how will likely take about a week of Googling and reading, because there are several mechanisms that may be at work handling this, so most of the stuff you end up reading will be wrong or outdated.

Sooo, good luck with your project...
:)

---

### Post by duanedesign on 2009-04-07
if you edit /etc/event.d/control-alt-delete to read 

```
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -h now "Control-Alt-Delete pressed"
```


then you would be able to use Ctrl-Alt-F1 to open the text window, next hitting Ctrl-Alt-Del would shutdown



---
-

---

### Post by kanikilu on 2009-04-07
This isn't pretty, but it works.

Step 1: Remove current Ctrl+Alt+Del keybinding

- Go to System > Preferences > Keyboard Shortcuts (or run gnome-keybinding-properties from the command line).
- Expand the Desktop section, click on Log out, and then press the backspace key. This will change it to Disabled. Close this window.

Step 2: Add a new key binding to bring up the shutdown dialog

- Open a terminal or press ALT+F2, run gconf-editor.
- Browse to apps > metacity > global_keybindings. Double-click on run_command_1 and change the value to <Control><Alt>Delete.
- Now go to keybinding_commands, double-click on command_1 and change the value to gnome-session-save --shutdown-dialog. You can close this window now and test out the new keybinding.

---

### Post by mvalviar on 2009-04-07
> **kanikilu said:**
> This isn't pretty, but it works.

Step 1: Remove current Ctrl+Alt+Del keybinding

- Go to System > Preferences > Keyboard Shortcuts (or run gnome-keybinding-properties from the command line).
- Expand the Desktop section, click on Log out, and then press the backspace key. This will change it to Disabled. Close this window.

Step 2: Add a new key binding to bring up the shutdown dialog

- Open a terminal or press ALT+F2, run gconf-editor.
- Browse to apps > metacity > global_keybindings. Double-click on run_command_1 and change the value to <Control><Alt>Delete.
- Now go to keybinding_commands, double-click on command_1 and change the value to gnome-session-save --shutdown-dialog. You can close this window now and test out the new keybinding.

Thanks this works however. If I have other open windows it doesn't have focus and I still need to Alt-tab to it or Grab the mouse and click it from the window list. 

Can anyone tell me if Ctrl-Alt-Del in Jaunty is as convenient as in Hardy or does it bring up the useless logout dialog like in Intrepid. 

Doesn't ubuntu developers realize that people rarely log-off? They usually shut-down when they're done using the pc or lockscreen if they are gonna afk.

---

### Post by thewolfman on 2009-04-07
Hi,

ctrl-alt-del works fine with jaunty, I am testing myself and don't have a problem with it.

Have fun amigo.

---

### Post by mvalviar on 2009-04-07
> **thewolfman said:**
> Hi,

ctrl-alt-del works fine with jaunty, I am testing myself and don't have a problem with it.

Have fun amigo.

Thats a relief! Hurray!

---

### Post by kanikilu on 2009-04-07
> **mvalviar said:**
> Thanks this works however. If I have other open windows it doesn't have focus and I still need to Alt-tab to it or Grab the mouse and click it from the window list. I'm not sure why, but you're right, it doesn't give the window focus for some reason.

Although, if you just want to shutdown, can't you just leave after pressing CTRL+ALT+DEL? It should shutdown automatically in 60 seconds. If you need to restart, suspend, etc., then you'll need to get focus of the window first...

---

### Post by theozzlives on 2009-04-07
Just use the Fast User Switcher

---

