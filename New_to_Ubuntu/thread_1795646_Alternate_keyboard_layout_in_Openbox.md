---
title: "Alternate keyboard layout in Openbox"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Kexolino on 2011-07-03
I constantly need to switch between the English and Hungarian keyboard layouts. When I add the Hungarian layout in Gnome/KDE/XFCE, I get multiple variations of the layout (like, Hun (101 key, qwerty, dead keys) etc), which I need, because the default Hungarian layout switches the y and z keys (qwertz). So I always choose the "qwerty" option. 

 In Openbox there's no option for this, but I found a post about switching layouts with keybindings. That's OK, but if I type the command

```
setxkbmap -model pc101 -layout hu
```

I can only get the default "qwertz" option, which I refuse to use, lol.
So I would like to know how I can get that Hungarian "qwerty" layout in Openbox. This keeps me from using it pretty much... Any help would be nice :)

---

### Post by frankbooth on 2011-07-03
I don't remember how I solved this, but basically what you need to do is to find out what the layout is called. I'll try to remember how I did this and will edit this post once I do.

To switch between english and phonetic bulgarian I use the following command:```

setxkbmap -layout "us,bg(bas_phonetic)" -option "grp:alt_shift_toggle"

```

This also lets me switch between layouts with Shift+&#1040;lt.
I then added this command to be executed at login.

---

### Post by Kexolino on 2011-07-03
> **frankbooth said:**
> I don't remember how I solved this, but basically what you need to do is to find out what the layout is called. I'll try to remember how I did this and will edit this post once I do.

To switch between english and phonetic bulgarian I use the following command:```

setxkbmap -layout "us,bg(bas_phonetic)" -option "grp:alt_shift_toggle"

```

This also lets me switch between layouts with Shift+&#1040;lt.
I then added this command to be executed at login.

Thanks!! Changing your command to this ```
setxkbmap -layout "us,hu" -option "grp:alt_shift_toggle"
```

gave me the regular qwerty Hungarian layout :D Dunno why it didn't work before, but I'm happy now :lolflag:

---

### Post by qu4nt1n on 2013-02-08
in order to add the cyrillic layout while using openbox, i typed in the following command in a terminal window:

```
gedit  ~/.config/openbox/autostart
```and i inserted at the end of the file the following command:

```
setxkbmap -layout "fr,ru" -option "grp:alt_shift_toggle & "
```so that each time i start openbox i can toggle between the French and the Russian through ALT+SHIFT.

hope it helps!

---

### Post by oldos2er on 2013-02-08
Old thread closed.

---

