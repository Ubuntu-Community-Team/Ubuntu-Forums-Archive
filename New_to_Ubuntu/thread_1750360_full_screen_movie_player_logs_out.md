---
title: "full screen movie player logs out"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by fixtrot on 2011-05-05
ubuntu newguy here, cannot for the life of me play movies in full screen, any touch of the mouse anywhere logs me out, have searched the forums cannot find a reply that works
please help.

---

### Post by pvnkmrksk on 2011-06-25
[SIZE=3]After upgrading to Ubuntu 11.04, a strange behaviour i am getting on  video playing full screen in Totem, vlc, smplayer, xine player. The  system logs out every time i play a video, almost all video formats i  have tried. [/SIZE]
[SIZE=3]I have resolved this problem, changing video drivers of the said player to x11,[/SIZE]

[LIST=1]
[*][SIZE=3]smplayer: Options --> Preferances--> Video --> Output Driver --> x11(slow)[/SIZE]
[*][SIZE=3]vlc: Tools --> Preferences --> Video --> UNCHECKED Accelerated Video Output[/SIZE]
[/LIST]
[SIZE=3]Now the Videos are playing on FULL-SCREEN without logging off.[/SIZE]
[SIZE=3]As of totem movie player, couldn't find this option, how to change.[/SIZE]
[SIZE=3]However, this seems odd, that i have not noticed this thing in previous versions of Ubuntu i have used. [/SIZE]
[SIZE=3]  
[/SIZE][SIZE=3]     0     down vote[/SIZE]  
                                [SIZE=3]I did not find a way to configure Totem movie player but you can disable the default output that is causing the problem as a workaround by doing the following.[/SIZE]
  
[LIST=1]
[*][SIZE=3]Right click "Applications) on the top panel.[/SIZE]
[*][SIZE=3]Select "Edit Menus"[/SIZE]
[*][SIZE=3]Select "Preferences" under the Menu section on the left side.[/SIZE]
[*][SIZE=3]Select "Multimedia Systems Selector" on the right side.[/SIZE]
[*][SIZE=3]Click close.[/SIZE]
[*][SIZE=3]On the panel, click "System", "Preferences" and then "Multimedia Systems Selector".[/SIZE]
[*][SIZE=3]Click the "Video" tab.[/SIZE]
[*][SIZE=3]From the "Plugin" dropdown, select "X Window System (No XV)"[/SIZE]
[*][SIZE=3]Click close.[/SIZE]
[*][SIZE=3]Logoff and then login.[/SIZE]
[*][SIZE=3]Enjoy Fullscreen video in Totem and Firefox. :-)[/SIZE]
[/LIST]
 
[SIZE=3]SOURCE : 
[http://askubuntu.com/questions/43790/system-logs-out-on-video-playing-in-full-screen](http://askubuntu.com/questions/43790/system-logs-out-on-video-playing-in-full-screen)

P.S. I actually copy pasted it. Had the same problem here. I'm also an absolute beginner!! 
[/SIZE]

---

