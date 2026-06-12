---
title: "Mouse back/thumb button works in firefox but not in thunar."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by sunexplodes on 2009-02-13
So I've got a Logitech Mouseman. 1 thumb button, and I've always mapped it to {Alt}+{Left}. using a combination of xbindkeys and xkvbd. It's always gone smoothly (and by always, I mean I've been doing this for about 3 years on every Linux install I do, from Arch to Ubuntu), but on my most recent Ubuntu install, the back button only works in firefox. 

I'll post the relevant section from xorg.conf and my xbindkeys config, so hopefully someone smarter than me can make some sense of it. 

Thanks. 


XORG: ```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "ButtonMapping"         "1 2 3 6 7"
    Option         "Protocol" "ExplorerPS/2"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
    Option         "Resolution" "800"
EndSection
```

.xbindkeys:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7
```

---

### Post by sunexplodes on 2009-02-16
Bump.

---

