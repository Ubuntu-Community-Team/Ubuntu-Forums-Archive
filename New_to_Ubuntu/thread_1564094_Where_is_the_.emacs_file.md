---
title: "Where is the .emacs file???"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by knutendre on 2010-08-30
ABSOLUTE BEGINNER!!!!
I have a HUGE problem, and thats my learning curve, -its not steep enough. I have just started to use Ubuntu, since I was told that Python was "easier" to use from this platform. OK, I am now an Ubuntu user, and have learned to open the TERMINAL WINDOW :( Scary! Well, I have also downladed a software called R (statistical software) and I managed to install this software as well...good! BUT, I need a text editor to help me using this, so GNUEMACS is what I have. I do also need a some addition to this EMACS editor. It is  reccomended to get R and EMACS to shake hands, and I have downloaded that as well. Evereything seems OK, but this little "additive" to EMACS called ESS (Emacs Speaking Statistics) is a bit of a trick for a stupid guy like me. In the ESS instructions it says...
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3] 
[LEFT][COLOR=red]Then, add the line[/COLOR][/LEFT]
[/SIZE][/FONT][/SIZE][/FONT][FONT=CMTT10][SIZE=3][FONT=CMTT10][SIZE=3][COLOR=red][LEFT](require ’ess-site)[/LEFT]
[/COLOR][/SIZE][/FONT][/SIZE][/FONT][FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][COLOR=red]to ‘[/COLOR][/SIZE][/FONT][/SIZE][/FONT][COLOR=red][FONT=CMTT10][SIZE=3][FONT=CMTT10][SIZE=3]~/.emacs[/SIZE][/FONT][/SIZE][/FONT][FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3]’ and restart Emacs.[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][/SIZE][/FONT][/SIZE][/FONT] 
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][SIZE=2]WHERE IS THE [COLOR=red].emacs[/COLOR] file??? I can't find it...How on earth do I find it? Does it exist for GNUEMACS? Is it on the root?? HELP! What shall I type with my fingers and where...[/SIZE][/SIZE][/FONT][/SIZE][/FONT]
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][SIZE=2][/SIZE][/SIZE][/FONT][/SIZE][/FONT] 
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][SIZE=2]Thank you in advance[/SIZE][/SIZE][/FONT][/SIZE][/FONT]
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][SIZE=2][/SIZE][/SIZE][/FONT][/SIZE][/FONT] 
[SIZE=2]regards[/SIZE]
[FONT=CMR10][SIZE=3][FONT=CMR10][SIZE=3][SIZE=2]knutendre[/SIZE]
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by lisati on 2010-08-30
The "~/" is shorthand for your "home" directory, which is where I'd expect to find ~/.emacs, if it exists. 

If you are looking for the file with the GUI file browser, you might have to use "View Hidden Files". This is because one of the meanings of "." at the start of a file name is "hide this file."

---

