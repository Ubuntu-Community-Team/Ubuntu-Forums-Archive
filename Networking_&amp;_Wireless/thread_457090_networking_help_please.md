---
title: "networking help please"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Crazz on 2007-05-28
hello

i am new to ubuntu. i need help with my network, here is my setup
verizon fiber modem --------- my firewall is plugged into the fiber modem--------- then my hub is pluged into the clean side of my firewall------------ my computer and my brothers computer is plugged into the hub. 

so i need to get my computer where it will connect to my brothers computer. so he can use my printer and i can transfer files to his when need be. he is running ubuntu as well we both are running the newest version and all updates applied.

thanks for any help you can provide it is very much appreciated
Rich

---

### Post by Pragmatist on 2007-05-28
Select this menu:
**System-->Administration-->Printing**

Now, within the printing dialog, select this menu:
**Printer-->Add Printer**

 (note: if you like the command line, you could get here right away by typing **gnome-cups-add** )

Now you'll be at step one of the add printer wizard.  Under "Printer Type" "Local or Detected Printer" is selected by default.  You need to select "Network Printer".

Now there will be a box labeled "URI".  Here, you need to put the IP address of the computer with printer attached to it.  You can find out its address by typing:
```
ifconfig
```

That should do it.

---

### Post by Crazz on 2007-05-28
thanks, but i just read a few other forums and leaned that my printer will not work. i have a lexmark x3350

---

### Post by Pragmatist on 2007-05-28
> **Crazz said:**
> thanks, but i just read a few other forums and leaned that my printer will not work. i have a lexmark x3350

Well, when you get a working printer, the above instructions are how you network them (which was your question right! ;) )

---

