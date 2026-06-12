---
title: "Menu's no longer Have Minimize, Maximize or Close option"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by DanTheBib on 2010-08-27
I have realised in Ubuntu applications/menu's etc, I don't have the ^ v X selection...

How do I solve this :S I've restarted the pc, to no avail..

---

### Post by DanTheBib on 2010-08-27
Bump...

---

### Post by TwoEars on 2010-08-27
I'm not sure what you mean :/ Could you take a screenshot for me?

---

### Post by DanTheBib on 2010-08-27
See, in the top right of the front window where the minimize etc should be, there is nothing...

[http://i59.photobucket.com/albums/g316/Goku2212/Screenshot-1-1.png]()

---

### Post by TwoEars on 2010-08-27
Ah, I see. This implies to me that you're using emerald to draw your windows. Is this true?

Regardless, open a terminal(Applications -> Accessories -> Terminal) and run ```
metacity --replace &
``` If that doesn't work, try ```
emerald --replace &
```

---

### Post by DanTheBib on 2010-08-27
Okay, I tried that and have reinstalled Emerald. How do I un-install Emerald and not have this problem again?

---

### Post by TheStroj on 2010-08-27
> **DanTheBib said:**
> Okay, I tried that and have reinstalled Emerald. How do I un-install Emerald and not have this problem again?

Run

```
sudo apt-get remove emerald
```

---

### Post by sikander3786 on 2010-08-27
Alternatively you can install "fusion-icon". It will sit in the system tray and will allow you to quickly switch between windows managers and decorators, and reload one if you are getting problems.

```

sudo apt-get install fusion-icon

```

---

### Post by DanTheBib on 2010-08-27
Thanks guys. Uninstalling Emerald presented the same problem, so have installed Compiz Fusion.

Thanks again :)

---

