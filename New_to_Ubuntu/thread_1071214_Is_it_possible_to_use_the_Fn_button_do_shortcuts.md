---
title: "Is it possible to use the Fn button do shortcuts?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jjblackfox on 2009-02-15
A lot of my shortcuts, especially for compizfuxion, use the Super key. Unfortunately, on my laptop the Super button is on the top right of the keyboard, far out of the way, while the Fn button is where the Super key should be. 

Basically, all I want to know is if there is a way to change the keyboard layout so if I press the Fn button, my computer thinks I'm pressing the Super button.

---

### Post by jjblackfox on 2009-02-16
bump

---

### Post by jjblackfox on 2009-02-16
bump

---

### Post by konqueror7 on 2009-02-17
you could download compiz-settings-manager from the repos and edit the preferences for your custom shortcut keys for compiz-fusion...

---

### Post by PurposeOfReason on 2009-02-17
No. The 'fn' key is limited to those it can be bound too. It does not register a keystroke. It registers the key it is pressed in combination with as a new key, but those keys, and only those, have that ability. So you can't do fn + g for example.

---

### Post by mikewu on 2009-02-17
As PurposeOfReason said above, the Fn key does not register a key event. However if there are other keys you want to map, you might want to try fiddling around with xmodmap. 

What I did with my keyboard was switch the right control and caps lock. If you have another key that is nearby and you don't use it, Maybe you could possibly do something like this. 

The man page for xmodmap has a lot of info. 
Here's a site for remapping caps lock and control

[http://c2.com/cgi/wiki?RemapCapsLock](http://c2.com/cgi/wiki?RemapCapsLock)

Hope this helps!

---

### Post by jjblackfox on 2009-02-17
> **mikewu said:**
> As PurposeOfReason said above, the Fn key does not register a key event. However if there are other keys you want to map, you might want to try fiddling around with xmodmap. 

What I did with my keyboard was switch the right control and caps lock. If you have another key that is nearby and you don't use it, Maybe you could possibly do something like this. 

The man page for xmodmap has a lot of info. 
Here's a site for remapping caps lock and control

[http://c2.com/cgi/wiki?RemapCapsLock](http://c2.com/cgi/wiki?RemapCapsLock)

Hope this helps!

Thanks a lot, I'll look into it.

---

