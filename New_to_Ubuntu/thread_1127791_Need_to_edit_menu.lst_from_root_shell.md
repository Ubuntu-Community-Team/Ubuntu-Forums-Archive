---
title: "Need to edit menu.lst from root shell"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by kgeil on 2009-04-16
Hi, I did a dual boot install of Ubuntu with windows XP this evening, and cannot get the GUI to work (Known issue, just get an arrow and a blank tan screen, and I hope to fix that soon) BUT, my big problem now is that GRUB lists Ubuntu as the first OS to load (which isn't nice to the other user of this machine).  I need to change that to default to windows XP, but the only interface I get to interact with is "drop to root shell prompt", and I don't know how to edit menu.lst without a gui.  Can someone provide me with some guidance?

Thanks,

Kevin

---

### Post by llamabr on 2009-04-16
You should have access to any text editor, like nano, which is pretty friendly.

If not, I'm sure you can use vi.

---

### Post by leonardo_neo on 2009-04-16
If you want a GUI to edit menu.lst then run this command....

> sudo apt-get install startupmanager

To know more about startup manager, follow the link....

[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html")

P.S. My bad, I didn't notice that you have access only for shell prompt :(

---

### Post by kgeil on 2009-04-16
OOPS! That's way too easy!  Rookie move for sure!   All I could think of was gedit.-:(

Thanks,


Kevin

---

