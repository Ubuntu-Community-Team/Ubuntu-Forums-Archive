---
title: "[SOLVED] create launcher for media stream url"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by broecher on 2008-12-24
Hi,
Newbie here, I am trying to organize my streaming media sources by creating launchers for each source some require different players. I am running hardy.

I tried entering each of the following into the command line of the launcher:

gmplayer /mms://ski-media-win-1.lsops.net/euronews_en
gmplayer mms://ski-media-win-1.lsops.net/euronews_en
gmplayer %u /mms://ski-media-win-1.lsops.net/euronews_en
gmplayer %F /mms://ski-media-win-1.lsops.net/euronews_en

I get an error "no stream found to handle mms://....."
I url does work in that player.

Clearly, I do not know how to use the commands very well yet.

Can anyone give me an example of what should be in the launcher command line for opening a specific url in a player?

Thanks so much!

---

### Post by laceration on 2008-12-24
The 2nd one was correct and should work, it works for me. 
```
gmplayer mms://ski-media-win-1.lsops.net/euronews_en 
```

Maybe you just were not getting a good stream.  Video streams are not reliable, there are a lot of potential network bottlenecks that can mess them up.  Mplayer is not fantastic at persevering at it either, it will just shut down. Try it again.

---

### Post by broecher on 2008-12-24
wow. it does work... I get a terminal window that has to stay open during viewing, and an error message that i can close "Error: Could not open required DriectShow codex wvcldmod.dll"

I don't know why I couldn't get it to run earlier, probably closed it after the error message without waiting long enough.

Anyway to hide the terminal window?

Thanks so much I should probably post a new question for my error message.

---

### Post by laceration on 2008-12-24
Those are weird messages you are getting because a dll is a windows library and I am not aware of direct show codecs working in mplayer, they are definitely not default.  Thats for the Euronews?  If it is playing properly I would not worry about it, mplayer has a lot of messages.  If you just used mplayer instead of gmplayer in your launcher you should just get the viewing window,  That's the way I do it.  You won't have the gui controls but there is a good keyboard control setup.
```
mplayer --help
```
at the command line will list them.  There are ony a few to learn and once you do I think it works better than the gui.

---

### Post by broecher on 2008-12-25
Thanks again laceration,
Leaving out the g makes it only open the video viewer and the terminal. No control window (the gui control? - good riddance), and no error message! this is good.
I wish I could get the terminal to not show up...

---

### Post by laceration on 2008-12-25
I am assuming you are using the gnome panel for your launcher.  This is what comes with the standard Ubuntu.  Right click the launcher.  Click properties.  If the type says "Application in Terminal", that would explain it.  Change it to "Application".
If that is not it, try putting an "&" at the end of the command.

```
mplayer mms://ski-media-win-1.lsops.net/euronews_en &
```

---

### Post by broecher on 2008-12-25
Thanks, It was set on 'application in terminal' instead of just 'application'. 

After I made the first one, I just copied it to make the rest of my channels. 

You cannot view or edit this option in the launcher properties once it has been created. I started over and, voila!

---

