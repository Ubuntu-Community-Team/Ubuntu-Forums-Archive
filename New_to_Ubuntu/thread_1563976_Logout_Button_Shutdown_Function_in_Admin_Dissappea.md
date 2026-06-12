---
title: "Logout Button Shutdown Function in Admin Dissappears"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by koolkev on 2010-08-29
I have a dell inspirion 530 w/ Lucid

I am logging in and using the admin account and find that I loose the log out/ shutdown function in the upper right corner. 

I have also had some problems with loosing sound in Firefox w/videos but this may not be related. 

If I shut down I get back the sound and the logout button/shutdown function.

---

### Post by zeroseven0183 on 2010-08-29
It seems you accidentally removed the User Switcher applet. You can add it again by right-clicking on the panel and select Add to Panel...
You can also  see the power options under the System menu by the way.

---

### Post by koolkev on 2010-08-31
Thanks 07,
But if I did accidently remove it why would it come back with a restart? I don't yet know what actions result in it dissappearing but accidentially removing a button takes some steps.

It's happened several times but not apparently every time.

---

### Post by MisterLambda on 2010-08-31
I imagine the applet is crashing. Panel applets in GNOME work like tabs in Chrome: they're separate processes. Thus, if one crashes, it disappears and doesn't bring down the entire panel.

---

