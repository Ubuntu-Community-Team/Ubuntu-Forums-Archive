---
title: "@sign not working"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by swappa on 2009-07-07
Hello
Weird issue after installing Jaunty x64. 
My "at sign" is not working. When I press AltGr + 2 (Norwegian keyboard) nothing happens. The same "at sign" is working on my virtual Vista workstation (virtualized using vmware workstation). 

My Device section in xorg.conf looks like this;

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option    "XkbModel"  "pc105"
    Option    "XkbLayout" "no"

My keyboard is a standard wired logitech keyboard. 
The same thing happens if I bypass the logitech keyboard and use the keys on my laptop so it is not related to the keyboard. 

Any ideas?

Thanks

Ah, the following fixed it ;

Option "XkbOptions" "nodeadkeys"

---

### Post by swappa on 2009-07-07
Ah, the following fixed it ;

Option "XkbOptions" "nodeadkeys"

---

