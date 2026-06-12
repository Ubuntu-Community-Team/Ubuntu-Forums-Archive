---
title: "malfunctioning Windows key on netbook keyboard"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by razaz03 on 2011-06-19
Hi all,

So I searched how to make Natty recognize my Samsung nc10 netbooks windows key, and came up with [https://wiki.ubuntu.com/Lkraider/XmodMap](https://wiki.ubuntu.com/Lkraider/XmodMap). 

It seems xmodmap didn't like my key suggestions and decided not only will the windows key remain idle but so will half my other grammar type buttons. 

I cant tell you the error code exactly as I didn't back up the xmodmap file and tried to change it back since but xev returned keycode 133 for my left (and only) windows key. When I mimicked the instructions on that page with Meta_L and Meta_R as keycodes 115 and 116 respectively (as they appeared on my xmodmap file too), and typed ```
xmodmap /usr/share/xmodmap/xmodmap.br
```an error message was produced and the windows key didnt work. 

I then had the genius idea to repeat the process and change keycode 115 Meta_L (now Super_L) to 133 as xev indicated, and this has now messed up half my grammar buttons! (I usually enjoy the use of apostrophes!).

It seems I would need to revert to default xmodmap to get my buttons working, and an experienced mind on how to get my windows key running.

Thanks in advance,

razaz

---

### Post by razaz03 on 2011-06-19
Bump pls

---

### Post by pqwoerituytrueiwoq on 2011-06-19
this may be useful
system->preferences-> keyboard
layouts tab
options button
alt/win key behavior

---

### Post by razaz03 on 2011-06-19
> **pqwoerituytrueiwoq said:**
> this may be useful
system->preferences-> keyboard
layouts tab
options button
alt/win key behavior

That only replaces my windows key with Ctrl or Alt for e.g., or whatever option I set in the keyboard options tab- what I'm looking for is to have the windows key as a seperate recognised button in its own right, which is why I (ab)used xmodmap.

I seem to have functionality back in the keys that were involved, yet I still can't get my windows key recognised for e.g. to use as a keyboard shortcut.

---

### Post by idoitprone on 2011-06-19
post the output of 

```
xmodmap -pke | grep -i "meta\|super\|alt"

``````
xmodmap
```

I wonder what is your current mapping

It should be a quick fix i guess

btw, i want defaults

---

### Post by razaz03 on 2011-06-19
> **idoitprone said:**
> post the output of 

```
xmodmap -pke | grep -i "meta\|super\|alt"

``````
xmodmap
```I wonder what is your current mapping

It should be a quick fix i guess

btw, i want defaults

$ xmodmap -pke | grep -i "meta\|super\|alt"

keycode  10 = 1 exclam 1 exclam onesuperior exclamdown
keycode  11 = 2 quotedbl 2 quotedbl twosuperior oneeighth
keycode  12 = 3 sterling 3 sterling threesuperior sterling
keycode  64 = Alt_L Meta_L Alt_L Meta_L
keycode 133 = Super_L NoSymbol Super_L
keycode 134 = Super_R NoSymbol Super_R
keycode 204 = NoSymbol Alt_L NoSymbol Alt_L
keycode 205 = NoSymbol Meta_L NoSymbol Meta_L
keycode 206 = NoSymbol Super_L NoSymbol Super_L


xmodmap

xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

I thought I changed the file back to default: I still see super_L in mod4 there- perhaps I didn't execute xmodmap /usr/share/xmodmap/xmodmap.br after I reverted the changes back to default there. I could if you want me to!

---

### Post by idoitprone on 2011-06-20
i believe it is default and your keys should be working unless i have to remap it so the x server will recognize the keyboard

---

