---
title: "Playing with Xterm options - now screen is all black/grey"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Cheffrey on 2009-04-29
Hello, 

I am pretty much a total newb with linux and i was going through the options in xterm. I had been checking out various options for how the windows looked and i had just clicked on Redmond and Oxygen which were fine but then i clicked on a third (dont recall which one it was) and then it gave me a message that if i wanted to keep it click "ok" within 10 seconds and directly after that my screen changed to all black/grey.

My cursor is there in all its pointy white glory but everything is just a silhouette. What just happened? I know my monitor works as i just hit my kvm switch to hop over to my windows box from which i am typing this.. 

Is there something akin to safe mode that i can make changes or can i/should i ssh into it and change things there? I really dont know where to go on this and appreciate any and all help. 

Thanks, 
Cheffrey

---

### Post by Cheffrey on 2009-04-30
bump - I, with help, managed to fix this. I moved gtkrc-2.0-kde4 to gtkrc-2.0-kde4.bk and .kde to .kde.bk which seemed to reset my kde desktop back to defaults. So i wont be messing around w/that again any time soon.

---

