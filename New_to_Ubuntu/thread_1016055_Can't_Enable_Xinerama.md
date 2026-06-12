---
title: "Can't Enable Xinerama"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by pmains on 2008-12-19
First, some background. I am on Gutsy Gibbon. Here is my current xorg.conf ServerLayout:

```
Section "ServerLayout"
    Identifier  "Default Layout"
    screen 0 "Default Screen"
    screen 1 "Right Screen" RightOf "Default Screen"
    Inputdevice "Generic Keyboard"
    Inputdevice "Configured Mouse"
    #Option      "Xinerama"  "true"
    Option      "Clone" "off"
EndSection
```

Now, I have tried with Xinerama enabled, and with Xinerama commented out.

With it commented out, I have a dual screen of sorts, but once my mouse travels from the left screen to the right screen, it can't get back again.

With in active, GDM doesn't load. I get a screen full of vertical, colored bars several times. Eventually the system kicks over to failsafe mode, which is, of course, not what I want.

Is there anything I need to check to make sure that xinerama is configured properly? I installed it under Feisty Fawn, and it seemed to work then. Do I need to reinstall it? Was there a big change in the X server between Feisty and Gutsy?

---

### Post by GMachine_24 on 2008-12-19
you might want to check the search results from google.com for xinerama and ubuntu.... there are lots of posts re: problems in later Ubuntu versions... or you can just click on this link and search the messages for what you need...



[http://www.google.com/search?hl=en&q=xinerama+ubuntu+8.10&btnG=Google+Search&aq=7&oq=%22xinerama%22](http://www.google.com/search?hl=en&q=xinerama+ubuntu+8.10&btnG=Google+Search&aq=7&oq=%22xinerama%22)

---

