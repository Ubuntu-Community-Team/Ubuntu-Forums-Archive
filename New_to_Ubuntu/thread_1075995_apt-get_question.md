---
title: "apt-get question"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by homey69 on 2009-02-20
hi there, i've been using sabayon for 1 year now and am new to ubuntu, so far everything seems cool. one (nit-picky) thing though;

i noticed when i use apt-get install it's overly sensitive to package names, for example, i typed in apt-get install qgrubeditor and the result was "E: Couldn't find package qgrubeditor"
so i had to open synaptic and find an alternative which turned out to be... kgrubeditor. so i went back to terminal and corrected it and it installed, great.

i guess my point is that i'm used to equo's built-in fuzzy search component and wondering if there's a way to make apt-get behave in the same manner. i dislike having to use synaptic and would like to avoid it if possible...
thanxxx

---

### Post by taseedorf on 2009-02-20
There is one built in ( i think? ) but it doesn't work the best.... in your case though, you were trying to install something completely different.

for example... gnome would maybe install gnome-desktop

---

### Post by Vadi on 2009-02-20
I don't think a fuzzy search would be safe, but you can always do "apt-cache search <package>" beforehand.

---

### Post by homey69 on 2009-02-20
> **Vadi said:**
> I don't think a fuzzy search would be safe, but you can always do "apt-cache search <package>" beforehand.

it is safe because it's interactive. anyway, i'll try your advice, and thanks for the response

xoxo

---

### Post by jerome1232 on 2009-02-20
> **Vadi said:**
> I don't think a fuzzy search would be safe, but you can always do "apt-cache search <package>" beforehand.

+1 on apt-cache search, also you can use apt-cache show to get more info about a specific package your find.

---

### Post by Vadi on 2009-02-20
> **homey69 said:**
> it is safe because it's interactive. anyway, i'll try your advice, and thanks for the response

xoxo

For interactivity, just start typing in the name and press "tab". It'll fill in / display possible results. The fuzzy match though is prolly a nice addition.

---

### Post by MeBeMikeyC on 2009-02-20
Probably just semantics, but I like "aptitude search", because it has the indicator of installation state by default, like below.  

"p  apache2    - Next generation..."

Either way, +1 for aptitude/apt-cache search.

---

