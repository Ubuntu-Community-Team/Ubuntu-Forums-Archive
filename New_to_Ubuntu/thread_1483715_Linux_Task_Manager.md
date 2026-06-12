---
title: "Linux Task Manager"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by orphanlast on 2010-05-14
I know that you can go  System -> Administration -> System Monitor in order to access something similar (and in many ways, superior) to the Windows Task Manager. But here's the thing.

Realistically speaking, people press CTRL+ALT+DELETE when their computer is behaving like crap. So, by the time that I need this, it's not like the computer's going to be cooperating well enough for me to access all three of these in time.

Is there any keyboard shortcuts to bring this up? And if not? Is there a way that I can MAKE a keyboard shortcut for they sexy beast?

---

### Post by I8NY on 2010-05-14
could make a keyboard short cut in System>Preferences>Keyboard Shortcuts

---

### Post by ubunterooster on 2010-05-14
System>preferences>keyboard shortcuts. Click add; enter the commands as seen in attachments. (you can substitute what you want for alt+0)

---

### Post by orphanlast on 2010-05-14
Oh my dear lord... Thanks... stupid *** question...

---

### Post by ubunterooster on 2010-05-14
better a stupid question than a stupid mistake :D Just remember to mark the thread as solved

---

### Post by orphanlast on 2010-05-14
Well... It looks as though this is getting more complicated. That Keyboard Shortcut program is really limited in its options. I've looked through the list and System Monitor isn't on it. So I click ***. Type System Monitor in the "name" field. Then I decided the shortcut would be Ctrl+Mod4+Alt+Delete. I'm surprised it doesn't give me a chance to give it a path.

So now when I press those keys, the following error pops up: Error while trying to run (Ctrl+Alt+Mod4+Delete) which is linked to the key (<Control><Alt><Mod4>Delete)

So I've googled this sucker. There's a way to press Alt+F2 and do a gconfig thing. and mess around there. But it required me to type the entire path down.... I have no idea where this program is located in my computer.

And there's this other one where I can work with the terminal and get xbindkey. I've been able to open it up but it seems to have more options than the Keyboard Shortcut package, but it doesn't seem to be much help either. Am I missing something? Should there be something that I should be doing that I'm just not?

---

### Post by pastalavista on 2010-05-14
You can add a Sysmonitor Applet/Shortcut to the panel too (right-click->"Add to Panel")

---

### Post by BoneKracker on 2010-05-14
If it's really acting up, you also ctrl+alt+F1 to a terminal that doesn't depend on the graphical environment, and then type "top".  From there, it's easy to kill any misbehaving application by typing "kill" and the number shown next to it (it's process id).

---

### Post by ubunterooster on 2010-05-14
It looks like you made a mistake and entered the command wrong; see the screenshots and follow them.

---

### Post by Ozymandias_117 on 2010-05-14
> **orphanlast said:**
> Well... It looks as though this is getting more complicated. That Keyboard Shortcut program is really limited in its options. I've looked through the list and System Monitor isn't on it. So I click ***. Type System Monitor in the "name" field. Then I decided the shortcut would be Ctrl+Mod4+Alt+Delete. I'm surprised it doesn't give me a chance to give it a path.

The correct command for that application is ```
gnome-system-monitor
``` (And remember, Linux is case-sensitive.)

---

### Post by orphanlast on 2010-05-15
> **ubunterooster said:**
> It looks like you made a mistake and entered the command wrong; see the screenshots and follow them.

It's usually the simplest answers that we have the most difficulty with.

---

### Post by Roger Bailey on 2010-10-08
The Force Quit panel applet is very neat. Kills an application with a couple of clicks.

---

