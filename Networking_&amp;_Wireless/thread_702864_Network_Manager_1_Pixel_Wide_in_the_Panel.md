---
title: "Network Manager: 1 Pixel Wide in the Panel"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Enigmahack on 2008-02-20
So I have an issue, but I do have 2 clues on where to go with it. I just wanted to get some advice to see if anyone else had this same issue:

  Network Manager is only 1 pixel wide. I can still click on it, and it's actually quite elusive as my g/f is like "How do I get the internet if there's no network icons?" and then I'll click on it... it's just funny. 

  Anyway, so here's where my 2 clues come in: 

  In Terminal, when I run nm-applet --sm-disable, here's the output:

Code:
/home/enigma/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/enigma/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/enigma/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/Code. 

  *Sorry, I don't know what the vB code is to make it show code pretty lol*

  Anyway, so I get the distinct impression that my "Darker" theme is to blame. Sometimes it works, and sometimes it doesn't. If I run it through console, it works just fine, shows up properly, but when I run it through my Session startup using the same code, no luck. 
  
  Now, when I run it here via the terminal, there's 2 versions running. The "working" one, and then I have my 1 pixel wide one. They both show the same data, so it's not really an issue, but still. 

  Anyway, when I exit the terminal, even if I run the command with & at the end, it disappears again. 

  This is where I'm stuck. I don't really want to change my theme, as I've got it all pretty... but I suppose as a troubleshooting step I probably should. 

  At this point though, I'm definitely open to suggestions as to where I might consider looking next, or if anyone's had a similar issue. 

  Thanks in advance, I've gotten SO much help through this forum and have already convinced *after 1 week* at least 10 people to at least dual-boot to ubuntu. *I have to help them set it up, but it's all good ;-)*

---

