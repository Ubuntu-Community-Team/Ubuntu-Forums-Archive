---
title: "Terminal Server Client Problem"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Jmeyering on 2008-09-15
Ok so I'm only 2 weeks into my ubuntu/vista dual booting lifestyle, so I really know very little. but I have previously been able to connect to my schools windows network via the terminal server client with no problems. 
Recently, however, I have encountered some problems when I try to access the school server. now I get this error from TS Client after a minute or so wait.

Autoselected keyboard map en-us
ERROR: channel_register
WARNING: Initializing sound-support failed!
ERROR: connect: Connection Timed Out

I do know that I ran the xorg config to get my display settings set properly before this error starting coming but I'm not entirely sure what the problem is, which would be why I'm here. Any help would be greatly appreciated! thanks
Jared

---

### Post by Jmeyering on 2008-09-15
I feel awful for bumping, but if anyone has any ideas at all it would be great. Thanks so much!

---

### Post by jimmythegeek on 2008-12-26
Try disabling sound support in the terminal server client "Local Resources" tab.  

/all I got, having my own issues or I wouldn't have seen your post

---

### Post by eel on 2009-01-22
I have the exact same problem!!!!
And no idea what to do, tried disabling sound but that didn't do the trick...
Also tried reinstalling TSC but that didn't help either. Which sucks because i work from home and not being able to connect to my works server is a big problem.
What i do know is that the workserver just got updated, do you know if the same happenend to the servers you tried to connect to? When i looked on the TSC homepage it seemed as though the last update was from 2007 so maybe there are some compatibility issues?

---

### Post by eel on 2009-01-29
I'm sorry but i just have to bump this one...
Tried everything i could think of (which wasn't all that much) and didn't find any answers here on the forum. I really really need to get connected to my works server, is there any other way besides Terminal Server Client that doesn't include installing new programs on said server? The server is running xp and was updated about three weeks ago.

When pinging the server i get this output: 

>  --- xxxxxx.dyndns.org ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


This gives me the idea that the problem exists on my side but then again i have a lot left to learn...

---

