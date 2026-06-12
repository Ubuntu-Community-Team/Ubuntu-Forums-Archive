---
title: "[SOLVED] Force &amp;quot;close window/program&amp;quot;"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-06
Is there a key combination that will force an application to close.
I was working with a program and the program froze, couldn't do anything with it. Admittedly, it was a program in WINE. In the end, I eventually had to Ctrl+Alt+Backspace to get out of the situation, which then rebooted me. Is there a way to do it without rebooting?
Thanks in advance.
Now 2 weeks trying to get things running correctly.

---

### Post by s.fox on 2008-12-06
right click on your top panel, select 'add to panel', then select 'force quit'. that will add the 'force quit' applet on your panel.

click it whenever you want to close an application.  Then click on the application you want to close.

Simple as that.


hope this helps

EDIT:  you could also do ctrl + alt + esc

---

### Post by drs305 on 2008-12-06
Here are several ways to kill an unresponsive program. None involve simple keystrokes although you could easily create a launcher to do so:

GUI:
1. Applications, System Tools, System Monitor > Processes. Right click on the app, Kill Process
2. Force Quit (Right click on a panel, Add to Panel, Force Quit): Click on Force Quit icon, then click on the app's window to kill it.

Command Line (and potential launcher commands or keybindings):
3. **xkill ** in the terminal. When you hit enter, the cursor becomes a cross or X. Position it on a non-root window and click and the app will be terminated. 
4. **killall appname**  # example  "killall gimp"

To Find PID of an app: 
**ps aux | grep app**  or **ps -u yourusername**

5. **sudo kill -9 PID.number**  # example  sudo kill -9 8876

---

### Post by Solaris3k1 on 2008-12-06
Another option is to hit Alt-F2 and then type in xkill to turn your cursor into an X which you then can click on the offending program to make it quit.

OR

Hit Alt-F2 and then type "killall program" where program is the offending program's name.  

Granted... conky comes in handy for this, but that might be over your head for a bit.  For info on conky, just do a bit of google, or look around the forums.

Good luck and enjoy your ubuntu.

Edit:  Ah... drs... beat me to it.  ^_^

I forgot about the PID method.

Oh, one other thing, I have on occasion been unable to access a terminal or launch dialog.  If that happens, just hit Alt-Ctrl-F1 or F2, or really any function key up to F7 and then login, do the Command line stuff, and then hit Super(Or Windows key)-F7 to get back to your X session.  Hope that saves you any trouble.

---

### Post by Joeb454 on 2008-12-06
To follow from drs305's post. The "-9" option for the kill command also works with killall.

I had amarok completely freeze once, I had to run ```
killall -9 amarokapp
``` to close it, because killall wouldn't work :p

---

### Post by thadacto on 2008-12-06
Having used Windows for about the last 20 years, I like the idea of the icon on the panel, which I have now installed. I'm too old to be remembering all the different codes to be used in the Terminal. May of the codes don't seem to have any logical meaning as they did in the old DOS days!
Many thanks to everyone for such quick and clear replies

---

