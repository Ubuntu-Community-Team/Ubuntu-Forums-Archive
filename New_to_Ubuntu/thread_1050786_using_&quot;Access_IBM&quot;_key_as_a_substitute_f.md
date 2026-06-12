---
title: "using &quot;Access IBM&quot; key as a substitute for windows key for compiz shortcuts"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by rookworm on 2009-01-26
Hello,

I'm using Ubuntu on my T42 Thinkpad, and enjoying it greatly....

I want to be able to get all the special compiz effects that use the windows key, but un/fortunately, there is not windows key on my computer. There is however, an "Access IBM" key.

I did a lot of searching, and managed to get it _almost_ working by following the instructions I found....

[LIST]
[*]I added  "setkeycodes e017 148"  to /usr/share/hotkey-setup/ibm.hk to get ubuntu to recognize it 
[*]I used xmodmap to get it to send the "Super_L" keysym by entering the command ```
xmodmap -e 'keycode 156 = Super_L'
``` at the console.
[*]Now, when I press "Access IBM" when xev is running, I get something like

```
KeyPress event, serial 31, synthetic NO, window 0x5200001,
    root 0x69, subw 0x0, time 15829950, (-538,590), root:(266,643),
    state 0x0, keycode 156 (keysym 0xffeb, Super_L), same_screen YES,
    XKeysymToKeycode returns keycode: 133
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x5200001,
    root 0x69, subw 0x0, time 15829950, (-538,590), root:(266,643),
    state 0x40, keycode 156 (keysym 0xffeb, Super_L), same_screen YES,
    XKeysymToKeycode returns keycode: 133
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
[/LIST]

No more events are registered as i hold down the key or when i release it.

Now, I'm aware there's some sort of way of adding "modkeys" with the xmodmap command, and that may be relevant somehow, but what i've tried in that regard has not worked.

Can the computer detect if the "access IBM" key is being held down at all?
If so, where do I go from here?
If not, which keys can be made to substitute for the win key?


-Thanks!

---

### Post by rookworm on 2009-01-26
by the way, I'm not sure if this is the right forum for this post.... hope i can get some insight here, though

---

