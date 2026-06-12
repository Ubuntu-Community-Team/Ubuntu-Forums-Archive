---
title: "xmodmap: map keys for russian layout only"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by netimen on 2009-04-10
This maps numpad key 4 to the { for all layouts:
```
keycode 83 = braceleft braceleft braceleft braceleft
```
But how can I map it for russian layout only? (mapping it for en_US layout prevents mapping it in vim - [http://groups.google.com/group/vim_use/browse_thread/thread/1e2789d03dd426e8](http://groups.google.com/group/vim_use/browse_thread/thread/1e2789d03dd426e8))

---

### Post by computermacgyver on 2009-04-10
I'm not quite sure yet, but you can execute xmodmap -e "SOME COMMAND" at anytime to change the mapping instantaneously. 

Thus
```
xmodmap -e "keycode 83 = braceleft braceleft braceleft braceleft"
```
will change it how you want it for Russian and
```
xmodmap -e "keycode 83 = KP_4"
```
will change it back

```
xmodmap -e "keycode 83=KP_4 braceleft"
```
will make the key a 4 and shift+the key a {

If we can find a way to execute these commands whenever you change the layout, you should be all set. There also should be a way to edit the layout files directly I would guess.

---

### Post by netimen on 2009-04-10
Oh, I got it! How stupid of me!
```
xmodmap -e "keycode 83 = KP_4 KP_4 braceleft braceleft"
```

How do I mark the tread as solved?

---

