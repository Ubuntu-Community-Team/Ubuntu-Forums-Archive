---
title: "Task Manager for Ubuntu?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by CommuneOfLoon on 2010-11-07
Is there some kind of Task Manager equivalent for Ubuntu, to force quit programs and check the processes (and their CPU usage) that are running?

---

### Post by uRock on 2010-11-07
Go in the menus to System> Administration> System Monitor.

---

### Post by AngusH on 2010-11-07
If your having problems where the system is no longer responding when you click on the menus (rare but occasionally happens), an easy way to close down frozen apps is to press "Alt+F2" then type in xkill and click on the app you want to kill. That's only for when your having serious problems though, for the most part the above is a better choice.
Angus

---

### Post by Jetso on 2010-11-07
The all powerful "killall" command ;P . If you wanted to kill all GIMP running you would type ```
killall gimp
``` Or if it was terminal you wanted to end ```
killall gnome-terminal
``` That should do the trick.

---

### Post by HotShotDJ on 2010-11-07
> **CommuneOfLoon said:**
> Is there some kind of Task Manager equivalent for Ubuntu, to force quit programs and check the processes (and their CPU usage) that are running?
As you can see from the replies here, there are multiple ways to accomplish your goal.  You can even configure your system to call the System Monitor in the same way that you are used to in Windows.

Go to System -> Preferences -> Keyboard Shortcuts and then click the "Add" button.  A "Custom Shortcut" dialog will appear.  In the "Name" text box, type "System Monitor" and in the "Command" text box, type "gnome-system-monitor" (without quotes for both, of course) then click "Apply"

Finally, scroll down to the very bottom of the shortcuts list to find your newly added shortcut.  Click where it says "Disabled" and then press "Ctrl+Alt+Del" keys together.  You'll get a warning that the key combination is in use by Logout... go ahead and accept the change.  You'll now see the new shortcut listed next to System Monitor.

Good luck and have fun!

---

### Post by HermanAB on 2010-11-07
htop

---

### Post by uRock on 2010-11-07
> **HermanAB said:**
> htop

That's my favorite. Colorful and powerful.

---

### Post by Rubi1200 on 2010-11-07
> **HermanAB said:**
> htop
+1; htop can track all your processes and give you a lot of power over them too.

---

### Post by uRock on 2010-11-07
OP, If you'd like to try htop, which is a CLI style system monitor, then you will have to install it. You can do so by running **sudo apt-get install htop** in a terminal or by using Ubuntu Software Center.

Once installed, simply open a terminal and type **htop**, then hit enter.

In order for htop to stop a root process, you will have to start htop with **sudo htop** so that it has root permissions for killing root processes.

Here is a screenshot of htop in action.

---

### Post by CommuneOfLoon on 2010-11-08
Thanks for the replies, everybody. Good to know about the kill commands and the System Monitor. Looking at that screen shot of the htop, I feel I may need to do a little research before getting into that :)

---

