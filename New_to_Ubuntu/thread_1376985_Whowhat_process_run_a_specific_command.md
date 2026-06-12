---
title: "Who/what process run a specific command"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by karatedog on 2010-01-09
I have a real n00b question. 
I was recently tinkering with syndaemon, to see what parameter suits me best to avoid accidental touchpad "touching" and by that replacing the cursor.
I did everything by the book, and everything was working. I clearly remember using '-i 0.5' parameter. 
For a time now, I thought that this value is a bit low, and I wanted to raise it. I remembered putting this setting ('syndaemon -i 0.5 -k') in System->Preferences->Startup applications (I use GNOME), so I went there, and modified the value.
Restart X didn't help, the value stayed the same. Then restarted the computer, that neither helped. 
I did a 'ps ax | grep synd' and two copies of [FONT="Fixedsys"]syndaemon[/FONT] was running. So I removed the line from the "Startup applications" list, and there remained only one instance:
```
'17652 ?        S      0:00 syndaemon -i 0.5 -k'
```

However I cannot find what starts syndaemon now, but I really want to find what script or process does it. I even issued a full scale 'grep' for my entire harddisk, with no success (the search criteria was the parameters only). 

Any idea where I should start?

---

### Post by warfacegod on 2010-01-09
```
gksudo gconf-editor
```

I think the setting you are looking for might be in there. I used it to change my volume stepping which is kinda similar to what you're talking about. Hardly seems like a noob question though.

---

### Post by karatedog on 2010-01-10
Thanks for the suggestion, I'll check it. The internal Find in gconf-editor is not helpful though :-)

---

