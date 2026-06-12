---
title: "default shutdown behavior"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by dndrich on 2010-05-19
Ubuntupals:

Just updated my brother to Lucid. Just terrific. Anyway, he complains that the default shutdown behavior has changed. He claims that when choosing the option on the right upper panel to shut down, in Karmic it would just shut down. Now he gets a window asking him to confirm the shut down. Is there a way to change this behavior to simply shut down without a confirmation screen?

---

### Post by -humanaut- on 2010-05-19
Not sure, Karmic always prompted me to confirm if I wanted to shutdown. He could always shutdown via terminal: sudo shutdown -h now

---

### Post by Ozymandias_117 on 2010-05-19
> **-humanaut- said:**
> Not sure, Karmic always prompted me to confirm if I wanted to shutdown. He could always shutdown via terminal: sudo shutdown -h now

+1 If he didn't have a dialog after clicking shutdown in Karmic, it was a bug.

---

### Post by Contra75 on 2010-05-29
I think what he meant was that in Karmic by default if you click shutdown the confirmation in the pop-up window was not required as it would shut-down in 60 seconds. You could of course force it by clicking "shut down" it the pop-up window. 
I actually miss that too in Lucid. Any way to put it back??

---

### Post by dndrich on 2010-05-29
It turns out that you can add a shutdown button to the upper panel from the add applets to panel dialog. That button has the old behavior where you push it and it will shut down in 60 seconds. You can replace the default button with that one.

---

### Post by CCC999 on 2010-08-26
Easiest I found for Lucid Lynx is the option to suppress the confirmation dialog box in Ubuntu Tweak. You will find that as a check box in Ubuntu Tweak, Startup, Session Control. There are several additional handy options in the Tweak. Just do a Google search for Ubuntu Tweak for various versions.

---

### Post by Miljet on 2010-08-26
I think this may be what you are looking for.

 Press Alt-F2, enter gconf-editor, navigate to apps-->indicator-session and check the box next to suppress_logout_restart_shutdown

Also forgot to add, In Karmic you can disable the shutdown confirmation window by right clicking on the shutdown icon and turning the window off.

Cheers

---

### Post by salima on 2010-09-12
when i right click on the applet there is no 'preferences' which is what i read on another thread was where i could stop the confirmation in lucid 

*"Also forgot to add, In Karmic you can disable the shutdown confirmation  window by right clicking on the shutdown icon and turning the window  off."*

should this work in lucid also? what means 'turning the window off'? you mean remove from panel? 

*Press Alt-F2, enter gconf-editor, navigate to  apps-->indicator-session and check the box next to  suppress_logout_restart_shutdown*

this i have never done before (new to linux) and i dont know how to navigate...i am already lost after i enter gconf-editor...

i would really like to get rid of this, it is the last little annoyance that bothers me. i had intrepid for about a month and it was so nice and clean and sleek...no stupid questions or anything. i got enough stupid questions myself, i dont need the pc to ask me any!

other than that i am really loving linux!

---

