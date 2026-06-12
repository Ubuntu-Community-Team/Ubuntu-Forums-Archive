---
title: "Disbale window docking/maximizing in Natty"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by donescamillo on 2011-07-18
Hi,

I am running Ubuntu 11.04 and have switched off Unity. I do not have Compiz installed. My problem is that whenever I try to drag an window by its title bar, it gets maximized and the title bar seems to try to get docked to the top of the screen. Is there a way to configure/disable this behaviour?
I remember previous versions had an additional tab in System/Preferences/Appearance where one could set some features regarding UI behaviour (like wobbly windows etc.), but it is not there any more. 

Thank you

---

### Post by frankbooth on 2011-07-18
The reason this feature was added was to save vertical screen space. I'm not sure if it's Compiz related or related with the GlobalMenu (or both).

Anyhow, you can try and see if there's a setting in CCSM (short for CompizConfig Settings Manager).

Either download it in the Software Center or open a terminal and write:```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by donescamillo on 2011-07-18
Thank you for your reply!

It turns out I do have Compiz installed (must have gotten installed by default). So I will try various options and see how goes

---

