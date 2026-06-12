---
title: "Windows equivalent keyboard shortcuts"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by hariks0 on 2009-10-02
Many of us come from the windoze world to Linux through Ubuntu. I wondered whether there is a way to set up Windoze key board equivalents in ubuntu. After searching in the web and doing some experiments myself, I have set up the following in my ubuntu box. It could be configured in Compiz or some could be done by Ubuntu Tweak. 

So first things first. We all want the main menu to pop up when we press the Windoze/Super key. It is done by ```
System--> Preferences--> Keyboard Shortcuts--> 
```
Under the Desktop Section click on the shortcut for Show the panel's mail menu [Alt+F1]. Press Right Windoze/Super key so that the new shortcut displayed is SuperR. Now the Left Windows/Super key could be used for the combinations used in Windoze. [I am right handed you see.]

More than that I use

xvkbd -text "\[Alt_L]\[F1]"

as the command for starting the main menu without even touching my  keyboard.

For this, ```
goto System--> Preferences--> CompizConfig Settings--> General--> Commands--> Commands--> 
Run Command 0 and fill the text box with xvkbd -text "\[Alt_L]\[F1]"
``` [with the quotes and the command starts from xvkbd] Goto Edge binding and set the value against Run command 0 to Left.
You can set [Button Binding = <Shift>Button2] for the same command. It has the additional advantage of popping up the main menu at the mouse cursor if you do not have the main menu/main menu bar applet on your panels.

Note : To use this, you will have to install the xvkbd package . ```
 sudo apt-get install xvkbd
```

Now the Win+D
Change the shortcut for Show Desktop by merely moving mouse cursor to left bottom corner [where the show desktop icon is placed in windoze].
```
System--> Preferences--> CompizConfig Settings--> General--> General Options--> Key Bindings--> Show Desktop [with a monitor icon]. 
```
Click on it and select the edge or corner of the screen to activate show desktop.

THEN Win+E
Set value of Run Command 1 to "nautilus ~" [without quotes] to open your home folder with Super+e or "nautilus /" [without quotes] to open your root folder.

The other settings I use in compiz are

Win+R [Run Command 2] 
"gnome-terminal" with super+r [Its equivalent is actually Alt+F2]

Win+L [Run Command 3]
"gnome-session-save --logout-dialog" with super+l
[Button Binding = <Shift>Button2]

Task manager [Ctrl+Alt+Delete] [Run Command 4]
"gnome-system-monitor" Ctrl+Alt+Delete

End a non responsive program without using Ctrl+Alt+Delete [Run Command 5]
"xkill" with super+delete

Win+F [Run Command 6]
"gnome-search-tool" 

[Or use "gnome-search-tool --path=/" for setting the default search location to entire file system. Actually, I use former by a launcher [panel applet] and the latter in the key binding. So that I can choose the default search location.]

And that is not all. The edge bindings could be used for all these commands which enables us to do things even without any key press.

Hope this helps somebody move from Windoze to Ubuntu. Any other tips or list of commands like the above are welcome.

---

### Post by Cuco3 on 2009-10-02
Thanks man. Much appreciated.

---

### Post by hariks0 on 2010-01-15
You are welcome.:popcorn:

---

### Post by hariks0 on 2010-07-21
Bumped in case some body finds it useful.;)

---

### Post by BenginM on 2010-07-25
**This is very useful , thanks a bunch ;)**

---

### Post by BlazeFire247 on 2010-07-25
Thanks, this was very useful. I especially needed that Task Manager one :D

---

### Post by hariks0 on 2010-07-26
Those who are not able to use Ctrl+Alt+Delete for System Monitor should first release that key binding from the default key bindings and may use Super+L there.

:)

---

### Post by hariks0 on 2010-07-26
You are Welcome !

:)

---

### Post by karmila on 2010-07-28
Thanks hariks0!

I'm using Ctrl+Alt+Del for system monitor and Ctrl+Del for xkill now. :)

---

### Post by rockager on 2010-08-04
nice post. very helpful and informative.

---

