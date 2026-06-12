---
title: "compiz problem"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by mick_86 on 2011-03-01
i have compiz installed, i had it all working with the cube effect and everything but now its not working and when i go into the compiz settings it wont let me click on any of the settings to activate them.

any ideas anyone?

---

### Post by Frogs Hair on 2011-03-01
I may not have an answer , but check Appearance Preferences > Visual Effects and see if your desktop effects are _still_ enabled.

---

### Post by mick_86 on 2011-03-01
> **Frogs Hair said:**
> I may not have an answer , but check Appearance Preferences > Visual Effects and see if your desktop effects are _still_ enabled.


yep still enabled, tried all 3 settings and none of them worked.

---

### Post by corncob on 2011-03-01
> **mick_86 said:**
> i have compiz installed, i had it all working with the cube effect and everything but now its not working and when i go into the compiz settings it wont let me click on any of the settings to activate them.

any ideas anyone?

I was going to suggest you check "Cube Reflection and Deformation" and try the sphere and cylinder but if nothing's working at all you might try reinstalling the compiz settings manager

---

### Post by mick_86 on 2011-03-01
> **corncob said:**
> I was going to suggest you check "Cube Reflection and Deformation" and try the sphere and cylinder but if nothing's working at all you might try reinstalling the compiz settings manager

tried that, same thing happening. i can change the settings such as sphere and cylinder but what it wont let me do is enable it. i can go into the options and change what i want but if i try to tick the box to enable it it does nothing.

---

### Post by ajmc on 2011-03-01
I have same problem before and I tried using simple compizconfig and I am able to manage my laptop's visual effects and its quite cool B-)

---

### Post by mick_86 on 2011-03-02
> **ajmc said:**
> I have same problem before and I tried using simple compizconfig and I am able to manage my laptop's visual effects and its quite cool B-)

tried that aswell, didnt work.

---

### Post by mick_86 on 2011-03-02
don't know if this is related but when i go to **system>preferences>appearance** then go to visual effects, every time i change it anything other than none it reverts back every time i close the window.

also the bottom quarter of my screen is blank.

---

### Post by vivek.pandey on 2011-03-02
wait this reverting back happened to me too ..let me remember what i did?
but before... you are not getting any error message while you are trying to active the features right? and your ati drivers are well activated?

---

### Post by corncob on 2011-03-02
> **ajmc said:**
> I have same problem before and I tried using simple compizconfig and I am able to manage my laptop's visual effects and its quite cool B-)

Good idea!  I see it in the Software Center.  I was going to say "You did reboot your computer since you lost the effects?"  That does wonders sometimes.  Its just that I leave mine on 24/7 as I'm into distributed computing and bit torrent.

---

### Post by mick_86 on 2011-03-02
> **neo_aryan said:**
> wait this reverting back happened to me too ..let me remember what i did?
but before... you are not getting any error message while you are trying to active the features right? and your ati drivers are well activated?

no error message, don't know about the ati drivers but the effects were working prviously.

> Good idea! I see it in the Software Center. I was going to say "You did reboot your computer since you lost the effects?" That does wonders sometimes. Its just that I leave mine on 24/7 as I'm into distributed computing and bit torrent.

i have rebooted several times since i lost the effects.

---

### Post by vivek.pandey on 2011-03-02
k since effects are working ati drivers are activated but to check it system->administration->additional drivers

---

### Post by mick_86 on 2011-03-02
> **neo_aryan said:**
> k since effects are working ati drivers are activated but to check it system->administration->additional drivers

when i go to that nothing appears in the window.

---

### Post by corncob on 2011-03-02
> **mick_86 said:**
> don't know if this is related but when i go to **system>preferences>appearance** then go to visual effects, every time i change it anything other than none it reverts back every time i close the window.

also the bottom quarter of my screen is blank.

My understanding here is to leave these settings alone if you're using compiz as it will reset compiz (a useful way out though in case you get compiz really messed up and want to start all over).

---

### Post by mick_86 on 2011-03-02
> **corncob said:**
> My understanding here is to leave these settings alone if you're using compiz as it will reset compiz (a useful way out though in case you get compiz really messed up and want to start all over).

i've played about with those settings, but only after compiz stopped working. any ideas?

---

### Post by vivek.pandey on 2011-03-02
k so i guess you accidently hit (do not do this!) the
"Remember currently running applications" button in System -> preferences->StartupApplications/Options
So have a look and uncheck the checkbox if checked

---

### Post by mick_86 on 2011-03-02
> **neo_aryan said:**
> k so i guess you accidently hit (do not do this!) the
"Remember currently running applications" button in System -> preferences->StartupApplications/Options
So have a look and uncheck the checkbox if checked

it was unchecked.

---

### Post by vivek.pandey on 2011-03-02
you sure you never hit that "Remember currently running applications" button? i would suggest hit it back if you have

---

### Post by mick_86 on 2011-03-02
> **neo_aryan said:**
> you sure you never hit that "Remember currently running applications" button? i would suggest hit it back if you have

yes i'm sure i never hit that button. when i looked it was unchecked and i'm sure i've never checked the box before.

---

### Post by mick_86 on 2011-03-02
update: i tried typing [COLOR="Red"]compiz --replace[/COLOR] this brought the full screen back for a few seconds then went back to having the bottom quarter of the screen blank.

this message appeared the terminal.

> libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start


don't know if this means anything to anyone.

update 2: typed the [COLOR="Red"]compiz --replace[/COLOR] command into the startup applications section, now i have my full screen back.

i also used the synaptic manager to uninstall then reinstall all files to do with compiz. now i have my screen and the menu but when i go to the compiz menu (ccsm), i still can't activate any of the options i.e. the cube.

---

### Post by lidex on 2011-03-02
Follow the compiz-check link in my sig and utilize the script provided. Post your result.

---

### Post by mick_86 on 2011-03-02
> **lidex said:**
> Follow the compiz-check link in my sig and utilize the script provided. Post your result.

thanks lidex but literally just fixed, after all this it was simple really. i went into [COLOR="Red"]ccsm>preferances>plugin list[/COLOR] and checked the automatic plugin sorting, made all my options available again. problem solved.

thanks everyone for all your patience and input!!

---

### Post by lidex on 2011-03-02
So, user error then? ;)

---

### Post by mick_86 on 2011-03-02
> **lidex said:**
> So, user error then? ;)

100% user error, but i'm just starting to learn. ive only been using ubuntu/linux for 3 weeks now so its all still new to me.

---

### Post by lidex on 2011-03-02
Just giving you a hard time, newbie. Can't tell you how many times I borked something. But you never stop learning. Have fun.

---

### Post by mick_86 on 2011-03-02
> **lidex said:**
> Just giving you a hard time, newbie. Can't tell you how many times I borked something. But you never stop learning. Have fun.

thanks, the more i learn the more it interests me, looking forward to learning more.

---

