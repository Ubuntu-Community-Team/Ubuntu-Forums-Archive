---
title: "[SOLVED] Refusing updates and terminal size"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by nefigah on 2008-12-07
Hi all! I just installed ubuntu, my first linux, yesterday. I like it a lot but there's a couple things I can't figure out.

1) The update manager is showing packages I don't want (namely, emacs21, when I already have emacs22 installed). Sure, I can uncheck them, but then they just show up again and thus that notification icon is always up top. How can I tell it "never bug me about this package again"?

2) After a long time of scouring the internet, I still can't figure out how to make the terminal launch with the size I want. I know about the --geometry switch, and indeed when I issue the command from the terminal, a new window opens with the proper size. But I can't make it launch at that size from the Applications menu or Go. I've tried the usual suggestion, going into System > Prefs > Preferred Programs and changing the terminal command from gnome-terminal to gnome-terminal --geometry fooxbar, but it doesn't seem to affect anything. 

All help appreciated!
-Jordan

---

### Post by Patrick793 on 2008-12-07
> **nefigah said:**
> Hi all! I just installed ubuntu, my first linux, yesterday. I like it a lot but there's a couple things I can't figure out.

1) The update manager is showing packages I don't want (namely, emacs21, when I already have emacs22 installed). Sure, I can uncheck them, but then they just show up again and thus that notification icon is always up top. How can I tell it "never bug me about this package again"?
Well, if they are appearing in Update Manager they are already installed. Just go ahead and update them. They probably won't bother you again.

> 2) After a long time of scouring the internet, I still can't figure out how to make the terminal launch with the size I want. I know about the --geometry switch, and indeed when I issue the command from the terminal, a new window opens with the proper size. But I can't make it launch at that size from the Applications menu or Go. I've tried the usual suggestion, going into System > Prefs > Preferred Programs and changing the terminal command from gnome-terminal to gnome-terminal --geometry fooxbar, but it doesn't seem to affect anything. 

All help appreciated!
-Jordan
Don't know about that one. Hopefully someone else does.

---

### Post by drs305 on 2008-12-07
To get the Applications Terminal command to open the way you want it to, just edit the menu and then edit the open command: 
Right click on the Main Menu icon, Edit. Select Accessories, Terminal, Properties. Then put in your command with the --geometry switch. 

Mine is:
```

gnome-terminal  --geometry=146x25+30+50

```

If emacs22 is listed in synaptic, you can lock the version via Package, Lock Version. There is also an option to use the 'hold' feature with 'aptitude' which you can read about in the man page. One of these may prevent the messages but since it is referencing an earlier version I am not sure.

---

### Post by nefigah on 2008-12-07
Thanks for the help.

Well, that worked for my menu shortcut, but Gnome Do still uses default geometry. Alas :(

---

### Post by drs305 on 2008-12-07
> **nefigah said:**
> Thanks for the help.

Well, that worked for my menu shortcut, but Gnome Do still uses default geometry. Alas :(

I spent some time looking for a solution and found one at the following site. It will not provide offsets as my shortcut command does, but it will set the terminal height and width, anchored at the top left. 

I installed Gnome-Do and can testify that changing the settings in the manner described *will* change the terminal layout when invoked via gnome-do. My own shortcut specs still work as they did previously. 

The disclaimer is that I can make no assurance this will not effect other apps **so please make a backup of the xterm file before proceeding**. 

I rebooted before it took effect but it is possible I had other terminals open at the time.

[http://www.codealpha.net/tips/gnome/45-how-to-change-gnome-terminal-default-size-ubuntu]("http://www.codealpha.net/tips/gnome/45-how-to-change-gnome-terminal-default-size-ubuntu")

---

### Post by nefigah on 2008-12-07
Thanks! That worked!

---

