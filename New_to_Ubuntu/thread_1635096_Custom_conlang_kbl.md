---
title: "Custom conlang kbl"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Tirean on 2010-12-01
I have been looking around trying to find a good easy way to do this...if it is even possible.

I am lets say fond of conlangs and I want to make a custom kbl for it.

I want to make a layout that looks like this:

° 1 2 3 4 5 6 7 8 9 0 - =
kx w e r t y u i o p [ ] \
a s tx f ng ì k l ; '
z ä ts v px n m , . /

Shift:

~ ! @ # $ % ^& * ( ) _ +
Kx W E R T Y U I O P { } |
A S Tx F Ng H Ì K L : "
Z Ä Ts V Px N M < > ?

I was easily able to do it on windows(via Microsoft Windows Keyboard Layout Creator), now I want to do it on Ubuntu 10.04 LTS. what exactly do I do? I am a noob so the more specific, the better. Thanks!

EDIT: and yes, kx, tx, ng, ts, and px are "two characters-one key" which i think may be what makes this impossible on Linux...or does it?

---

### Post by Tirean on 2010-12-02
So I was able to get simosx's keyboard layout editor software to create the file for a layout. I put it in /usr/share/X11/xkb/symbols with all the rest of them but it didnt work. 

then I tried making sure the language was technically US English and pasted the output at the end of the us symbol file via sudo gedit.

Here is what I pasted at the end of the pre-existing us symbol:
```

//kxwerty for Na'vi

xkb_symbols "nav" {

  name[Group1] = "USA - Kxwerty";

  include "us(basic)"

  key <AB02> { [     adiaeresis,     Adiaeresis                                 ] }; // ä Ä 
  key <AB03> { [             ts,             Ts                                 ] }; // ts Ts 
  key <AB05> { [             px,             Px                                 ] }; // px Px 
  key <AC03> { [             tx,             Tx                                 ] }; // tx Tx 
  key <AC05> { [             ng,             Ng                                 ] }; // ng Ng 
  key <AC07> { [         igrave,         Igrave                                 ] }; // ì Ì 
  key <AD01> { [             kx,             Kx                                 ] }; // kx Kx 
  key <AD03> { [	      e,              E,     eacute,     Eacute ] }; //   é É 
  key <TLDE> { [         degree                                                 ] }; // ° 
};

``` 

I am now having difficulty actually changing TO this layout to test it. when you add a layout variant to a symbol, how do you make that variant available for switching to via the Keyboard Preferences under System menu?

---

