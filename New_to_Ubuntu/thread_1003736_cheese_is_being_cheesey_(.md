---
title: "cheese is being cheesey :("
date: 2008-12-06
forum: New to Ubuntu
---

### Post by ColeJayStooks on 2008-12-06
It's weird, I've finally gotten my Logitech QuickCam e3560 working with Cheese by installing [these Linux UVC drivers](http://linux-uvc.berlios.de/). The cam worked with Skype, aMSN, and VLC before those drivers were installed but Cheese would freak out about the camera and freeze. The drivers fix that, so now almost all apps work (VLC, aMSN, Skype, and Cheese so far, Camorama still doesn't work with it).

But now Cheese is being stupid.

You see, I had the "Extra" Visual Effects on. I took a picture with Cheese, not pressing the space bar and clicking "Take a picture...", and the camera effect would take place but wouldn't go off the screen. So, this means, that it would "flash" but keep the screen white. Alt-F4 couldn't help here, so I had to do a CTRL-ALT-Backspace to force my way out.

I thought it was the Visual Effects, so I turned them off, rebooted, and tried Cheese again; it still stuck with the white "flash" on the screen.

It's weird. *Sometimes* when I press the space bar in Cheese it will do the flash effect and let me have my desktop back, but regardless, this seems to be a bug.

Is there a way to turn that "flash" effect off or keep it on without forcing me to log out?

---

### Post by ColeJayStooks on 2008-12-06
bump ya'll

---

### Post by russo.mic on 2008-12-23
same Problem,  but I'll give you a general linux tip, switch to a terminal with ctrl+alt+F1, logon, then

ps x | grep cheese

ps gives you a list of processes running, the pipe directs it the output into grep, which gives you list of entries matching "cheese"

From there, you can see the process number and do a 

kill "number" 

to kill cheese and get rid of the flash. 


No more need to restart X!  I hope this bump has been educational.

---

### Post by sam_delta on 2008-12-23
same problem here, white screen, ,, what i do is i just change to another workspace (using the keyboard shurtcut, contl+alt+right arrow)  , open a terminal and type: "sudo killall cheese", then i can get my workspace back

not a solution tho, i would like to hear if anyone has fixed this?
thanks
sam

---

