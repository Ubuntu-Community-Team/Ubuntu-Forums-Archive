---
title: "Compiz Fusion"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by bostock73 on 2008-12-17
Ive installed it, got the gui up and stuff.

cant seem to get anything working though?

plus i unchecked snapping windows yet the windows still snap.

any help?

---

### Post by adult swim on 2008-12-17
what are you trying to do?

---

### Post by bostock73 on 2008-12-17
Im trying to actually use the effects. nothing is working.

i forgot to run the program, so i hit alt f2 typed compiz --replace.

Now i can only do one effect, flat desktop... but even then everything is white. Am i missing something here?

i downloaded compizsettingsmanager and emerald.

was that all i needed?

---

### Post by adult swim on 2008-12-17
say you wanted to spin your cube, if youve already done this, my apologies.
go to system>preferences>compizconfig settings manager
then go to general options up at the top
go to the desktop size tab and set horizontal virtual size to 4
then go back and make sure that desktop cube and rotate cube are checked.
then press ctrl+alt+left click and drag your mouse.  does that do anything?

---

### Post by Tatty on 2008-12-17
System->Preferences->Appearance gives you a friendlier way of switching on compiz.  Although by default the only two compiz options are Normal and Extras, which will change your compiz settings to presets. 

If you install simple-ccsm then it adds another option "Custom", which will let you use your custom settings.

Do you mean that literally the screen has gone white?

---

### Post by bostock73 on 2008-12-17
wow, that worked great! thankyou!

anything else cool to do?

the mouse thing isnt working either? the spiral thing around the mouse?

---

### Post by adult swim on 2008-12-17
a good thing to do is open the compiz settings manager and click on the option you want to do.  then look for initiate in the options that it presents.  for example, in the show mouse options, it says that to make the thing around the mouse, you have to press <super>k  the super button is the one that usually has the windows logo on it.  press that and press k at the same time.  does it work?

---

### Post by bostock73 on 2008-12-17
yes worked great!
thankyou for your help.

digressing slightly, but, do you know how to get wireless cards working?

broadcom specifically?

i tried that ndiswrapper thing been im a complete n00b, just starting using ubuntu about 3 hours ago

---

### Post by mrbiggbrain on 2008-12-17
i like wobbly windows, they are preatty cool to pull around,
and ADHD prevention keeps you focused

---

### Post by Tatty on 2008-12-17
> **bostock73 said:**
> yes worked great!
thankyou for your help.

digressing slightly, but, do you know how to get wireless cards working?

broadcom specifically?

i tried that ndiswrapper thing been im a complete n00b, just starting using ubuntu about 3 hours ago

Did you check in System->Administration->Hardware Drivers to see if any drivers are suggested for your card there?

---

### Post by bostock73 on 2008-12-17
yeah but it only comes up with my graphics card.

what do you wreckon?

---

### Post by Tatty on 2008-12-17
Do you know the model of your wireless card?  Can you post the output from:
```
sudo lshw -C network
```

---

