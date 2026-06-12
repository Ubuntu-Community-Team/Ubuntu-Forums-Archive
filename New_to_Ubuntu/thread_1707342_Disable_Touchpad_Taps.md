---
title: "Disable Touchpad Taps"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Chrissd on 2011-03-15
Hi all,

Simple problem I hope, my touchpad clicks are annoying when typing. I have a button for clicking so ideally I'd like to completely disable touchpad taps rather than after a period of time.

I installed gpointing-device-settings which stopped it for a few minutes but eventually the taps come back.

Is there a way I can disable the taps completely but keep the clicks?

Thanks

---

### Post by mikewhatever on 2011-03-15
System->Preferences->Mouse has a checkbox to disable tapping, it's called "Enable mouse clicks with tapping".
Alternatively, 'synclient TapButton1=0' in a terminal window disables tapping for me, and changing the value to 1 re-enables it.

---

### Post by pqwoerituytrueiwoq on 2011-03-15
touchfreez may be useful for you
disables the touchpad while you are typing

---

### Post by Chrissd on 2011-03-15
synclient TapButton1=0

The above worked for me and I just added a line to the start up for everytime it boots. 

I never understood why they have taps and a button. Surely one or the other?
 
Thanks

---

