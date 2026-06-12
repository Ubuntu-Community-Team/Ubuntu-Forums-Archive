---
title: "copy/paste does not work in terminal"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by trikster_x on 2009-09-21
I am having a problem getting the keyboard shortcuts for copy/paste to work in my terminal.  The shortcuts work fine in any other situation, but when I press SHIFT+CTRL+C or Z in a terminal, nothing happens.  I have tried to find a setting that might enable or disable this function, but don't really know where it would be.

I am using 8.04 Hardy.

---

### Post by NoaHall on 2009-09-21
It's "ctrl + shift + v" to paste.

---

### Post by oldsoundguy on 2009-09-21
try highlight and right click select copy
then go to terminal and right click select paste.

---

### Post by drs305 on 2009-09-21
Anything you highlight should be put into memory/clipboard and you can copy to or from a terminal simply by middle-clicking in the new area (terminal, text editor, etc).

---

### Post by trikster_x on 2009-09-21
@Noahall:

Yeah, sorry, I meant to put "v", not "z".

@oldsoundguy:

I know how to do it with the mouse, but the keyboard shortcuts are just a bit quicker.

@drs305:

Thank you, that works beautifully.  I would still like to be able to use the keyboard, though.

I figured out what needed to change to get the shortcuts working:

I opened a terminal, then went EDIT>>CURRENT PROFILE>>COMPATIBILITY>>RESET COMPATIBILITY OPTIONS TO DEFAULT

Now it works for everything but my screenlet terminal, but I can work with that using drs305's suggestion.  Thanks to everyone for the quick responses, though.

---

