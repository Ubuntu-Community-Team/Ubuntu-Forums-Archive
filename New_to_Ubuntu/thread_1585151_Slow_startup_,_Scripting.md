---
title: "Slow startup , Scripting"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by bokgeneraal on 2010-09-30
My system takes a long time to respond after it starts. 
I think due to screenlets.
Can I write a script to start all my screenlets after the computer has started?To start all non essential programs in one click? I  am not to fimiliar with scripts or the command line for that matter.

---

### Post by Ahava591 on 2010-09-30
Hm. If you think that is really the problem, then there is probably a way of doing what you want. I'm not familiar with "screenlets;" reading Wikipedia, it seems to me that they're just a bunch of widgets. Things like weather, time, etc.? 

A possible alternative might be Conky; it's notably used with Crunchbang Linux. 
Here is a picture of it in action with Lucid Lynx, it is the display of system information on the right hand of the desktop:
[http://upload.wikimedia.org/wikipedia/en/0/06/Conkyubuntu.png](http://upload.wikimedia.org/wikipedia/en/0/06/Conkyubuntu.png)

However, I think you want things like instant messaging, I'm sure there are widgets for Twitter, too, and so on. Look into Conky, it can be fairly easily configured, (the #! forums are the best place to learn how to work with Conky that I have found yet,) and is light on system resources.

But for the other stuff, let's start with what widgets exactly do you use? I'm sure others who are more capable will jump in here, but I will do what I can.

---

### Post by Ahava591 on 2010-09-30
[http://ubuntuforums.org/showthread.php?t=629076](http://ubuntuforums.org/showthread.php?t=629076)


I found that. I would recommend you wait for somebody else to confirm this is helpful--remember that that thread is three years old. In the meantime, pay attention to the second, replying post. I will research more about the particular "screenlets," you are using and find out how to modify the script to work with them as you give us more info.

The reason I asked what ones you are using in my first reply is precisely this; to write the script you will need to specify which widgets to work with like this person has in their script. 


Also, by navigating to System->Preferences->Startup Applications, are you able to find the widgets you use? The screenlets you have installed may appear there for you to choose. If so, try disabling them using Startup Applications and then enabling them individually once your computer has started up. 
-I realize this is not what you have asked for; but until we get your script figured out it's the best I can think of. Also, by disabling them all and then restarting your computer, we might be able to determine if screenlets is really what is causing the sluggish response.

---

### Post by bokgeneraal on 2010-09-30
I did disable all screenlets from starting automatically. It seems that the system does start more quickly. Here are the screenlets that I use:
DigiClock
Slideshow
Sysmonitor
Tomboy
Clearcalendar
Trash
:)

---

### Post by Ahava591 on 2010-09-30
I haven't done shell scripting in forever; to be honest, I wasn't good when I did it regularly.
Please audit this code for mistakes. I haven't put anything in that is malicious, but that doesn't mean the script isn't going to screw up a file somewhere.
Make it a text file, I recommend a text editor and not an office suite. (i.e., gedit, kate, etc. and not OpenOffice.) I think you would put it in your home folder, not sure.


[QUOTE] [PHP]
#! /bin/bash
sleep 60s;
exec /usr/share/screenlets/nameofscreenlet/nameofscreenlet.py > /dev/null &
exec /usr/share/screenlets/nameofscreenlet/nameofscreenlet.py > /dev/null &
exec /usr/share/screenlets/nameofscreenlet/nameofscreenlet.py > /dev/null &
[/PHP] [QUOTE]


this seems to work for me interactively.
I hope this has helped. I recommend you look up where to put a script, if you don't put it in your home folder. Please let us know what happens. 

Also, try bumping the thread once a day to attract more attention from those who are actually good at scripting, :)

---

### Post by bokgeneraal on 2010-10-21
being Lazy I tried something simpler
Launchers. So I have a single launcher for each screenlet
Now the only question is can you have a single launcher for all the screenlets?

---

### Post by AngusH on 2010-10-21
Yep, using a script or something similar.
You will need the commands to launch each screenlet. Then as the command in the launcher you want something like this:
```
bash -c "command1 & command2 & so-on
```
I'm sure there's a better way but that will see you by.

---

### Post by bokgeneraal on 2010-10-23
Yippy:KS
Thanx Everyone I used Avaha591 's script and it worked
Just didn't use /dev/null , what's that for?
:)

---

