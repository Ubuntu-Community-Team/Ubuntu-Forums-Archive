---
title: "the shift button is not working"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by heroidi on 2009-01-03
when i press the shift button and want to write something with big characters it doesnot work help plz.

---

### Post by heroidi on 2009-01-03
help plz im going mad :(:(:(

---

### Post by nemilar on 2009-01-03
Can you post the output of the following commands:

```
locale
```


```
setxkbmap -print
```



also try the keyboard on another computer, to make sure it isn't a hardware problem!

---

### Post by heroidi on 2009-01-03
```
heroid@heroid-desktop:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
heroid@heroid-desktop:~$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us+inet(evdev)"	};
	xkb_geometry  { include "pc(pc105)"	};
};
heroid@heroid-desktop:~$ 

```
here man

---

### Post by nemilar on 2009-01-03
Does the caps lock key work to produce capitals?  If not, does the light for the caps lock key work?

do all your other keys work correctly?

It looks like your keyboard setup is correct...standard 105 key setup.  Unless you are using some non-standard, non-american keyboard...??


Can you check that the shift key works on another computer?

---

### Post by nemilar on 2009-01-03
Can you also try dropping into a TTY and seeing if shift works there?

Key combination control+alt+F4 will give you a TTY

control+alt+F7 to come back to X.

---

### Post by heroidi on 2009-01-03
the caps lock works and the shift key works for other functions when i press shift and super for drawing fire or something else mabye ive lost the binding how can i bind shift for using it for writing something?

---

### Post by heroidi on 2009-01-03
shift works on tty

---

### Post by heroidi on 2009-01-03
help plzzzzzzzzzzzzzzzzzz

---

### Post by heroidi on 2009-01-03
help plz somebody

---

### Post by heroidi on 2009-01-03
I think i lost my key binding how can i bring it back to deafult plz helppppppp

---

### Post by nemilar on 2009-01-03
It sounds like you are experiencing this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/246081](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/246081)


The last post suggests this fix:
1. Go the System > Preferences > CompizConfig Settings Manager. If you don't have CompizConfig Settings Manager installed, you do so by opening a terminal and typing "sudo apt-get install compizconfig-settings-manager".
2. Launch the CompizConfig Settings Manager. On the left column there is a "Preferences" button. Click it.
3.Click on the "Reset to Defaults"

---

### Post by heroidi on 2009-01-03
i need something else man it does not work still

---

### Post by nemilar on 2009-01-03
Disable compiz and see if it works...

---

