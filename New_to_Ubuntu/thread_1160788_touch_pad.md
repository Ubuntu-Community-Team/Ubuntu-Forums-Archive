---
title: "touch pad"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by scghunter on 2009-05-16
thank you so much to the developers of ubuntu!!!   i love when my "winblows" friends say "hey, check this new program out.  it only cost $___" and i say back "oh really, check this out...it was free!"

but anyway, the only problem i seem to be having, so far, is with the touchpad on my toshiba satellite.  sometimes i can click on things by just pushing on the touch pad. other times i have to click the button.  is there a driver issue or something like that?  or is that just the way it is?  

either way, I LOVE UBUNTU.  finally i feel confident enough about linux to compleetly quit using "winblows". and my dependancy on forigen oil has gone down too!!!  

thanks yall, any help would be wonderful!

keep it real!

---

### Post by stoogiebuncho on 2009-05-16
Easy.

First, make a backup of your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf.backup
```

Next, open it up with a text editor:
```
gksudo gedit /etc/X11/xorg.conf
```

Scroll down until you find the section for your touchpad.  Add a new line that says:
```
Option "TapButton1" "0"
```

Save, log out, log in, you should be good to go.

---

