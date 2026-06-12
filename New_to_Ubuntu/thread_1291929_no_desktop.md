---
title: "no desktop"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by jrandolph on 2009-10-15
I have just done a fresh install of 9.04 everything was working fine yesterday - restart today and everything seems to boot fine then nothing all i have is a black screen with my mouse pointer
There is nothing i have done that would have removed the graphical desktop
can anyone give me a way to repair this please

---

### Post by jrandolph on 2009-10-15
I really dont want to do another install - i can get to a comand line but have no idea what to do when i get there - not one of my strong points

---

### Post by wobin77 on 2009-10-15
did you try
shift ctrl F11
```
startx
```

I m not at my nix box now, so forgive me if the above is wrong...  ;-)

---

### Post by jrandolph on 2009-10-15
shft+ctrl+f11 just gives me a blank screen with a cursor 

do u maybe mean f1?

---

### Post by hellblazer on 2009-10-15
If you can, drop to a terminal CTRL+ALT+F1 and try
```
sudo dpkg-reconfigure xserver-xorg
```
This will reset your graphics to basic settngs and you can at least see what you're doing ;)

Hope this helps

---

### Post by jrandolph on 2009-10-15
doing so asked me some questions about my keyboardand then took me back to a command line

---

### Post by jrandolph on 2009-10-15
oh well - going with another install -if this one goes bad again ill go back to 8.10 and wait for sumthin else

---

### Post by durand on 2009-10-15
9.10 is coming out in about 20 days.

---

### Post by jrandolph on 2009-10-15
with that being said - I would like to ask if my ati video card will again be supported or am i going to have to upgrade it?

i have a radeon x550 - worked great it 8.10 but i cant use dual monitors in 9.04 without a bunch of tweaks

---

