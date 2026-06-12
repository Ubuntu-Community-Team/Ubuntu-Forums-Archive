---
title: "Sorry but, uh, what's a script?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by StartedTheFire on 2011-06-28
I'm trying to learn how to do more stuff with linux and I came up with a quick little problem to solve. I want to make a link to open Minecraft with the java runtime environment, while still making it so that double-clicking .jar files opened them in archive manager.

Isn't that something that scripts do? Like, tell your computer to do stuff? This is probably pretty dum but I don't even know what filetype a script is or what programming language or anything. I looked it up on wikipedia but it was really general and my eyes kind of glazed over. Thanks.

---

### Post by seawolf167 on 2011-06-28
I suggest to start reading this [BashGuide]("http://mywiki.wooledge.org/BashGuide"), it is quite good at explaining things from basic questions to complex scripting examples and help.

---

### Post by StartedTheFire on 2011-06-28
Thanks a lot, this is really interesting. I figured out how to make the script and it works fine, but the point was to have an icon to run minecraft just so I didn't have to click multiple things. Now when I double click it it asks me if I want to run it or run it in terminal, which makes the whole thing silly because it's just as time consuming as before. Is there any way to set what happens when I double click it to just running it?

---

### Post by seawolf167 on 2011-06-28
Easiest way to do that would probably be to simply create a launcher for Minecraft. [Here ]("https://help.ubuntu.com/community/HowToAddaLauncher")is the how-to for that.

---

### Post by e79 on 2011-06-28
and possible this link for help about running Minecraft on Ubuntu 

[http://ubuntuforums.org/showthread.php?t=1537099&page=1](http://ubuntuforums.org/showthread.php?t=1537099&page=1)

---

### Post by StartedTheFire on 2011-06-28
> Some programs need additional commands before they can be started. Java programs need to be started from within the directory in which their files exist. Others must be run within Wine. Unfortunately launchers do not have access to the Bash environment so you cannot just include the needed commands.

So apparently making a launcher is just equivalent to double-clicking the file. I guess what I want is just to make it automatically "run" the script instead of give me a prompt to run in terminal/display/close/run. 

I was really just looking for a guide to scripts so that's definitely solved, now I'm just wondering if this little thing is possible.

---

### Post by mcduck on 2011-06-28
> **StartedTheFire said:**
> So apparently making a launcher is just equivalent to double-clicking the file. I guess what I want is just to make it automatically "run" the script instead of give me a prompt to run in terminal/display/close/run. 

I was really just looking for a guide to scripts so that's definitely solved, now I'm just wondering if this little thing is possible.

Easy. Just go to the file manager's preferences, and on the Behavior-tab change the "Executable text files" option from "Ask each time" to "Run executable files when they are opened".

..although if you make a launcher for the script it will just execute the script regardless of that setting. And making a launcher would also allow you to add Minecraft to your Applications menu or panel.

(and no, making a launcher is in no way the same as double-clicking the file. A launcher will always execute the file it's told to launch, while double-clicking a file in browser could either execute the file or open it for editing. And of course launchers can contain many kinds of additional features like a proper description for the program, translations for different languages, and quicklist entries for the Unity panel)

---

### Post by StartedTheFire on 2011-07-01
Oh I see. I had to make a launcher, *for the script*. This is cool thanks it works perfectly now. I love linux.

---

