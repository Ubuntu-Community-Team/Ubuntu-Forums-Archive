---
title: "New to Ubuntu [Shortcuts and other newbie questions]"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by rawrmarkie on 2011-07-14
Hi, I am new to Ubuntu. I just recently changed because my Win XP kept blue-screening due to hardware failure, apparently. Ubuntu (11.04) hasn't crashed yet, so I blame the drivers.

Anyway, I have a few questions. I have tried googling a bit and have worked my way through some things (I installed Avira, for example!), but others didn't work (Dazuko didn't install when I tried for some reason). I have also read [this thread]("http://ubuntuforums.org/showthread.php?t=801404"). I am still working my way through things. :) However, I thought it may be quicker to ask some questions. I hope that is okay. So here I go, I hope none of these are too silly; sorry if they are.

My first question: In the ALT+F2 thing, is there any way to clear the history? Also, can I copy files from there to my desktop (as shortcuts)? I tried, but got this error: There was an error getting information about "/"
What am I doing wrong?

I'll update this when I have other questions, but I will try not to be a nuisance. Thanks for your help in advance :)!

---

### Post by ngubk on 2011-07-14
1/Open gconf-editor 
apps/gnome-settings/gnome-panel/history-gnome-run 
R. click > edit on history-gnome-run
It works for me.
2/ Open /usr/share/applications. Pretty much all of app icons are there. Copy anything you like to the desktop.

---

### Post by androssofer on 2011-07-14
does alt-f2 bring up a little box to type in a command to run? (using kde atm, not sure if gnome/unity is the same...)

where you would type say "firefox".. and it would open firefox?

if so, i think i understand about the shortcut thing.. if u right click on the desktop and create a new shortcut. then right click it and select properties. in the section called "command" you would put in what you would have typed in the alt-f2 box. eg "firefox" then when you run the shortcut, it will run tht command and u'll get firefox... :-)..

if thts not wot u meant... my bad..

ps, no idea how to clear the history... is probly a conf file sumwhere tht you can set the length of the history. if you make it 0 it will remove them.. however, thts a guess...

---

### Post by rawrmarkie on 2011-07-14
Wow, you guys are quick! Thank you so much for replying.

> **androssofer said:**
> does alt-f2 bring up a little box to type in a command to run? (using kde atm, not sure if gnome/unity is the same...)

where you would type say "firefox".. and it would open firefox?

if so, i think i understand about the shortcut thing.. if u right click on the desktop and create a new shortcut. then right click it and select properties. in the section called "command" you would put in what you would have typed in the alt-f2 box. eg "firefox" then when you run the shortcut, it will run tht command and u'll get firefox... :-)..

if thts not wot u meant... my bad..

ps, no idea how to clear the history... is probly a conf file sumwhere tht you can set the length of the history. if you make it 0 it will remove them.. however, thts a guess...
Yes, that is just what I meant and thanks. It says 'create launcher' for me...I didn't realise that that was the equivalent to a shortcut. Anyway, thanks a lot, it worked fine. The reason I needed it there is because I am using multiple profiles (firefox -no-remote -P profile).

> **ngubk said:**
> 1/Open gconf-editor 
apps/gnome-settings/gnome-panel/history-gnome-run 
R. click > edit on history-gnome-run
It works for me.
2/ Open /usr/share/applications. Pretty much all of app icons are there. Copy anything you like to the desktop.
Thank you :) That helped very much; I wiped the history.

I hope it's okay if I keep using this thread for other questions? [Please tell me if that's not okay]

My next question is in regards to Avira..how do I use it? I can't seem  to figure it out. >_>

 I'm sorry if some of these questions are a bit pathetic but it's a learning curve, really!

---

### Post by androssofer on 2011-07-15
> I hope it's okay if I keep using this thread for other questions? [Please tell me if that's not okay]

My next question is in regards to Avira..how do I use it? I can't seem to figure it out. >_>

I'm sorry if some of these questions are a bit pathetic but it's a learning curve, really! 

u can use this thread if u want.. but might be best to start new threads tho. for example a thread called "trouble using avira" is more likely to be picked up by someone who knows the answer, if its in this thread they might skip over it and u miss out... 

haha, dnt worry about it, we all started sumwer. i'm still a noob and i've been using ubuntu for 4 years. Thats wots this forums all about :-)

ps. never used Avira (hadnt even heard of it til i read this thread...) so cant help u ther :-(

---

### Post by mastablasta on 2011-07-15
you need to install linux version and then it might be comand line only version. 
 
you could try Avast! instead. maybe it's easier to configure and run.

---

### Post by rawrmarkie on 2011-07-15
> **androssofer said:**
> u can use this thread if u want.. but might  be best to start new threads tho. for example a thread called "trouble  using avira" is more likely to be picked up by someone who knows the  answer, if its in this thread they might skip over it and u miss out... 

haha, dnt worry about it, we all started sumwer. i'm still a noob and  i've been using ubuntu for 4 years. Thats wots this forums all about :smile:

ps. never used Avira (hadnt even heard of it til i read this thread...) so cant help u ther :sad:
Aw thanks for the encouraging words. Yeah, we do all start somewhere. Don't worry about Avira anyway, I've picked ClamTK instead. Oh and also, thanks for the hint. I have taken your advice and opened another thread regarding Rainlendar. Thanks again!


> **mastablasta said:**
> you need to install linux version and then it might be comand line only version. 
 
you could try Avast! instead. maybe it's easier to configure and run.
Yeah I have installed the Linux version :) Perhaps you're right, it seems that it is only command line, I think GUI is exclusive to the paid version. However, I have chosen to use ClamTK, which seems fine to me at the moment. :) Thanks for your help.

---

