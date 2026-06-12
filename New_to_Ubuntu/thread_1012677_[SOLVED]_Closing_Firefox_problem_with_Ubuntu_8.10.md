---
title: "[SOLVED] Closing Firefox problem with Ubuntu 8.10"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by germanix on 2008-12-16
I have made a clean install of Ubuntu 8.10. In general I am very happy with it. I only noticed two small problems, one of which is the that I can not close Firefox like usual. The X in the top right corner of the browser which would normally close the window is not there. Instead I only have the circle which runs clockwise when loading the page. Normally this circle then turns into a x for closing the window, but this does not happen. The only option that I now have for closing the browser window is the File-Quite option. Does anyone know of a solution for this problem?

---

### Post by Tatty on 2008-12-16
Do you not have the window decorator at all on the window?  By window decorator I mean the brown bar at the top that says the name of the app and has the minimise, maximise and close buttons.

Do other apps have the window decoration?

Are you running any desktop effects / compiz?

---

### Post by germanix on 2008-12-16
You are right. I do not seem to have the windows decorater on at all? I can neither close, minimise or maximise. I am not running any desktop effects. This is only true for the browser, other windows are ok.

---

### Post by Tatty on 2008-12-16
Im not sure if this will work since your other apps are working correctly, however try this:

```
metacity --replace &
```

---

### Post by alienexplorers on 2008-12-16
If you are running an nvidia driver make sure you have in your screen section of xorg.conf:
Option  "AddRGBGLXVisuals" "True"

---

### Post by germanix on 2008-12-16
metacity --replace &
This worked. You are a real Star. Thank you very much. May the blue bird of happiness fly over your head.

---

### Post by Tatty on 2008-12-16
> **germanix said:**
> metacity --replace &
This worked. You are a real Star. Thank you very much. May the blue bird of happiness fly over your head.

Why thank you, lol.

Im not sure if that fix will stick between boots though.  If not you could always add that command to System->Preferences->Sessions.  A bit of a dirty hack but it should work.

---

### Post by germanix on 2008-12-16
If you are running an nvidia driver make sure you have in your screen section of xorg.conf:
Option "AddRGBGLXVisuals" "True"
__________________
I thank you for this tipp. It seems my problem is solved anyway (see above) however if I wanted to use your advice I would not know where to start. It is all alien to me.

---

### Post by germanix on 2008-12-16
I rebooted to see if the fix works after the re-boot. The problem is however that now I do not have an Internet connection at all. I am writing this on my laptop. it seems that this fix has done something to the internet connection? any ideas?

---

### Post by Tatty on 2008-12-16
This sounds like a separate issue, metacity --replace will not affect your internet connection.

Have you tried rebooting again?  try pinging ubuntu.com to see if you can reach it:

```
ping -c3 ubunu.com
```

---

### Post by germanix on 2008-12-16
ping -c3 ubunu.com
I have done this and yes I do reach them. I now notice that I do in fact have a internet connection but the icon fot the network (2 screens) does not show up on the top panel? this led me to believe that I had no internet. How do i get this back?
I rebooted a couple of times with same result.
The good news is however that the "fix" also works after the reboot!

---

### Post by Tatty on 2008-12-16
That is odd.  I have seen a few people with this issue in Intrepid.  Im not sure why it happens.

try

```
nm-applet &
```

---

### Post by germanix on 2008-12-16
jac@jac-desktop:~$ nm-applet &
[1] 6207
jac@jac-desktop:~$ 
** (nm-applet:6207): WARNING **: No connections defined
The icon is now back, your fix worked. What is with this Warning?

I rebooted. This fix did not live after the reboot.

---

### Post by germanix on 2008-12-16
I found the problem. The applet was switched off under preferences-sessions-start-up programms. I again thank you all. There is no fool like an old fool. I guess i must have switched it off and fotgot about it.

---

