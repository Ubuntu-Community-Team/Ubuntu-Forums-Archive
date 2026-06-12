---
title: "cannot capitalize.."
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-21
the only way to capitalize letters for me is by hitting the caps lock key....shift key has no power anymore besides to not let me press anything while shift is held down...today is the first day this has happpend and i dont remmeber doing anything weird with the setting on the keyboard, i would'' greatly appreciate some help from you guys about this...it gets anoying as im used for the shift key usage.....and also in email adressed i cannot tipe a  ''2'' shift plus 2 on the laptop...lol...

shift is essential..

---

### Post by Skol312000 on 2009-03-21
bumping this, cause, i got not shift............

---

### Post by mkvnmtr on 2009-03-22
You might try cleaning the keyboard and under the keys. that didn't help mine. Once I started having problems I had to buyb a new keyboard. Not likely to be a software problem but you might try plugging in another keyboard to check.

---

### Post by gali98 on 2009-03-22
Okay.. try these commands in the terminal:

	sudo update-rc.d -f hotkey-setup remove
	sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .

That just may fix both problems.. it resets the keymap.
Kory

---

### Post by lisati on 2009-03-22
Hope it's something simple like cleaning the keyboard - tipping it upside down and giving it a gentle shake (repeat: GENTLE) can sometimes dislodge dust and other muck the messes up the contacts. 

A friendly reminder for smokers: cigarette smoke and ash can be hazardous to the health of computer equipment.

---

### Post by Skol312000 on 2009-03-22
brand new laptop...i tryed cleaning it anyways, and nothing...the sudo code did nothing as well.......

when i press the shift key in a text box somewherer..i exites me out of the text box so nothing can get tiped in and once i release shift key it lets me back into text box...

what the heck/

---

### Post by mkvnmtr on 2009-03-22
Plug in another keyboard. If it works then you have a hardware problem.

---

### Post by Skol312000 on 2009-03-22
JUST DID and it dindnt work...

ive messed around with compiz a lot yesterday, i wonder if i did something in there.

---

### Post by Skol312000 on 2009-03-22
i dont know what to do....and i need this...

can i assign another key to equal the special ''a'' charraacter so i can use it//

i cant even tipe the question mark

---

### Post by Skol312000 on 2009-03-22
i tryed adding every other english layout keyboard and they still dont work.

what i found out that may be the problem is when i press shift it DESELECTS the text box..the mouse '''line '' no longer shows and it is useless... what should i do

I got it, it was in Compiz ...sry for the waste of time..

---

