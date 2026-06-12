---
title: "MCE Keyboard in Ubuntu"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by studiostustar on 2008-12-22
Hey guys.  I've recently converted to Ubuntu 8.10.  I'm completely new to this, been a Windows user all my life.  I have been trying for days to find a guide to getting my MCE keyboard to work with Ubuntu.  I've tried many, still no luck.  There are also a lot that I don't even know what they're talking about.  I really just need a good step by step guide to getting it to work.  I believe I've installed lirc, and I've downloaded a driver called lirc_mod-mce.  I'm just completely lost and frustrated, could someone please help?  :confused:  I would really appreciate it!

---

### Post by kebes on 2008-12-23
Can you provide some more details? Such as:
-What parts of the keyboard work or don't work? Do the "standard keys" (letters, spacebar, etc.) work? Do the "media keys" (volume, play, pause, etc.)?
-What is the exact make/model of the keyboard? 
-Is the keyboard connection USB or PS/2 (or a USB through a PS/2 converter)?
-Do other keyboards work on that computer? (In Ubuntu?)
-What are you trying to get working? Do you want the media keys to control your music application? (Which one?) Your movie-playing application? (Again, which application are you using?)


Here's some information that might help:
-There is a program called "[Gizmo Daemon]("http://gizmod.sourceforge.net/")" which is designed for getting various input-output devices working. It's [in the repositories]("http://packages.ubuntu.com/search?keywords=gizmod&searchon=names&suite=intrepid&section=all") under the name "gizmod", so you can install it easily. (If you're not yet comfortable with installing software in Ubuntu, check out [this]("http://www.psychocats.net/ubuntu/installingsoftware") and [this]("http://doc.ubuntu.com/ubuntu/switching/applications-installing.html") and [this]("https://help.ubuntu.com/community/InstallingSoftware").) Gizmo Daemon recognizes many media keyboards, so it might "just work" after installing.

-One thing that would help is to run a program called "xev" (Alt+F2 opens run dialog, type "xev" and run). This program will actively show codes for any keys pressed. So you can press the media keys on your keyboard and confirm that they are being registered by Ubuntu. You can also take note of the "key codes" which may help in configuring other programs...

-You can manually remap keys on your keyboard, which can be used to assign keys that are not being recognized. See [this post]("http://ubuntuforums.org/showpost.php?p=2115845&postcount=2") for some information.

-LIRC might be the solution you need, depending on the type of keyboard and what you are trying to do. But LIRC generally requires a decent amount of configuration to get it right.


If any of these instructions are too confusing, feel free to ask for clarification.

---

