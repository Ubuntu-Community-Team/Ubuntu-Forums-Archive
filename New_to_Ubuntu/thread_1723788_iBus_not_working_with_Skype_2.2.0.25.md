---
title: "iBus not working with Skype 2.2.0.25"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by Anuovis on 2011-04-07
Hello,
I've been using the Japanese iBus input without any problems but I think it stopped working after the Skype update. Now the iBus simply doesn't work, I can't trigger neither the language panel nor the actual input method while using a Skype window.

Things that I've tried so far that didn't solve it:

1. Installing ibus-qt4 package

2. Adding these lines to the .bashsrc ```
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
export XIM_PROGRAM=/usr/bin/ibus-daemon
```3. Launching iBus from the Startup Applications with this command
```
ibus-daemon -drx
```People have reported for these to work but they didn't for me. 
I also tried SCIM but it seems to be totally broken for any input in any applications.

Any ideas what I could do to solve this? Thanks.

---

