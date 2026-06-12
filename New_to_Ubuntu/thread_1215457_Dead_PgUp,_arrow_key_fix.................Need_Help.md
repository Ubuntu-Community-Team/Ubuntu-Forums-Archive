---
title: "Dead PgUp, arrow key fix.................Need Help.........!"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Csongi on 2009-07-17
I actually try to use my forward arrow key, its same as the PgUp key....


But it doesn't works.....Does anyone having a clue how to reconfigure it, or any programmes to use a different keypad button for the same function....






Thanks:




Csongi

---

### Post by drs305 on 2009-07-17
Until someone gives you an easier method, here's an "old-school" solution.

Type "xev" in a terminal. It will open a window. Put your mouse cursor there. Hit the "right" key and note the keycode an key name (on mine, it's Right, keycode 51). Next hit the key you want to use. Note them again (example: backslash, keycode 51).

To use the backslash key as the Right key, use this command:
```

xmodmap -e "keycode 51 = Right"

```
Note: If the key you are reassigning has a different uppercase, add a second entry after 'Right' to retain it:
```

xmodmap -e "keycode 51 = Right bar"

```

 
To make it stick, put it in your startup list (Applications, Preferences, Sessions or Startup Applications).

If your Right key is completely dead and you can't get the value from xev, you can try to print out your computer's keymap with:
```

xmodmap -pke

```

---

### Post by bodyharvester on 2009-07-17
> **Csongi said:**
> I actually try to use my forward arrow key, its same as the PgUp key....


But it doesn't works.....Does anyone having a clue how to reconfigure it, or any programmes to use a different keypad button for the same function....

Thanks:

Csongi

is it a laptop? 

my dell mini 9 UP ARROW key has Pg Up on it under the arrow in blue, there is a key next to left Ctrl which has the blue letters Fn on it and holding that button then pressing UP ARROW uses the Pg Up instead

---

