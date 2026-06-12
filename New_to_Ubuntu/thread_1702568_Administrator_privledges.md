---
title: "Administrator privledges"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Canime on 2011-03-08
Hi there I want to use Wire shark network analyzer on my system, but it seems I need the right privilege. The reason I say this is because as I start it from the menu, and then go to change some of the options in the configuration panel, there are no interfaces to select. I looked on the net, and it seems I need to add admin privilege to it, in order for those devices to show up. Can I make it to start with the right access every time?

---

### Post by zenwalker on 2011-03-08
Or may be you can add your user account into the root user groups to get most rights. No idea if this would harm to your system or not.

---

### Post by Canime on 2011-03-08
Yeah, but how to do this in Ubunutu for just one program and not the account. After all I think this account is the default account I set up when I installed and it by default should have root privilege for most things, if it doesn't I still want to do it just for Wire shark and not have to type, sudo Wire shark all the time, or harm my account.

---

### Post by mikewhatever on 2011-03-08
Simply start Wireshark from a terminal window with **gksudo wireshark**, or modify the menu entry from Wireshark and add the 'gksudo' part to it. To modify the menu, open Main Menu under System->Preferences.

---

### Post by Canime on 2011-03-08
Ok I think I have it now. Its easy, I needed to go to the applications menu, click edit menus, select wireshark, then click properties and in the command bar add, "sudo wireshark". It runs perfectly now, thanks.

---

### Post by mikewhatever on 2011-03-08
While sudo may work well for Wireshark, it's considered good practice to use gksudo for graphical apps.

---

### Post by Canime on 2011-03-08
@mike Thanks, I appreciate the value adding!

---

