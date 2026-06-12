---
title: "window pane has disappeared"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by lizardbliz420 on 2009-02-23
im not really sure how i did this or how to undo this but my windows when maximized no longer have a window pane with a title minimize maximize close buttons.  Ive tried changing the themes around but to no avail.

thanks in advance for your help

---

### Post by BDNiner on 2009-02-23
Do you have your applications set to full screen mode? I believe the key is F11 to turn it on and off.

---

### Post by djinn1973 on 2009-02-23
I had the same problem, I got around it by turning off the visual effects.

---

### Post by lizardbliz420 on 2009-02-23
i have tried turning on and off the visual effects to no avail. and im not in fullscreen mode

---

### Post by stoogiebuncho on 2009-02-23
Have you tried pressing Alt+F2 and running
```
compiz --replace
``` 
(that could be what you meant when you said you turned on and off the visual effect, but just in case it's worth a shot)

The other thing that some people say helps is to open the Advanced Desktop Effects, go to "Workarounds" and make sure that Legacy Fullscreen Support is not checked.

---

### Post by lizardbliz420 on 2009-02-23
I did that and it hasn't worked nor has switching from compiz to metacity using the fuzion icon

---

### Post by Crafty Kisses on 2009-02-23
> **lizardbliz420 said:**
> im not really sure how i did this or how to undo this but my windows when maximized no longer have a window pane with a title minimize maximize close buttons.  Ive tried changing the themes around but to no avail.

thanks in advance for your help

Is this in all programs, or only a certain few? Do you have Emerald or something to that nature, we need a bit more information.

---

### Post by lizardbliz420 on 2009-02-23
It is only for windows that are maximize otherwise all the the windows have their panes but every maximized window lacks it.  I do have emerald but it doesn't matter if i switch to gtk window decorator the problem still persists in both.

---

### Post by frank002 on 2009-02-23
This was happening to me with Firefox. Someone here suggested the following:
 go to System>Preferences>CompizConfigSettings Manager. Once there go to 
Utility>Workarounds and uncheck the box that reads Legacy Fullscreen Support. That seems to have fixed the problem.

---

### Post by lizardbliz420 on 2009-02-23
I have tried changing the legacy work around however it does not help.  Nor is this a firefox only issue.

---

### Post by lizardbliz420 on 2009-02-24
i tried uninstalling compiz and that has failed to correct the problem either

---

### Post by lizardbliz420 on 2009-02-24
fixed! i reinstalled the libgnome-window-settings package

---

