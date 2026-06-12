---
title: "Compiz and dual monitors not working"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by cjnkns on 2010-05-01
Hey all - 

I am running Ubuntu 10.04 and having issues with dual monitors.
When I use Metacity dual monitors are fine but, when I try to use compiz I can't drag my windows to the second screen.

I did the 'sudo nvidia-settings' and it is still set to twin view so that should be good...

Another interesting thing is if I am using Metacity everytime I reboot my title bars are gone. I have to go to Visual Effects and select normal or something to get them to appear again.

Does anyone know of a fix for this?

note: hopefully this is not posted twice :) having forum issues for some reason....

---

### Post by switch10 on 2010-05-01
> **cjnkns said:**
> Hey all - 

I am running Ubuntu 10.04 and having issues with dual monitors.
When I use Metacity dual monitors are fine but, when I try to use compiz I can't drag my windows to the second screen.

I did the 'sudo nvidia-settings' and it is still set to twin view so that should be good...

Another interesting thing is if I am using Metacity everytime I reboot my title bars are gone. I have to go to Visual Effects and select normal or something to get them to appear again.

Does anyone know of a fix for this?

note: hopefully this is not posted twice :) having forum issues for some reason....


compiz runs at a maximum resolution of 2048 x 2048. This is where most people run into trouble. You can't run both monitors side by side because it exceeds the maximum resolution.

Here is what I had to do (I use an ATI card, so you may have to do something slightly different): 
1. first off go to System>Preferences>Display
2. un-check "mirror screens"
3. stack your 2 monitors on top of each other. Just click and hold on one, and move it above or below the other.
4. then go to preferences>appearance>click on the visual effects tab, and enable extra effects.
5. If you have Compiz installed, it will work right away.

---

