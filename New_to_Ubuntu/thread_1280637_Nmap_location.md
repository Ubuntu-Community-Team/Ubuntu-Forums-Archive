---
title: "Nmap location"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by krisarnold on 2009-10-02
Hi all,
I downloaded Nmap and now I cannot find the GUI. Any ideas where it would have been put?

---

### Post by kanikilu on 2009-10-02
Can you clarify how you downloaded/installed it?

If you got the package from the repositories (either in Synaptic or **sudo apt-get install nmap**), then it's commandline only.

There's actually a basic GUI included in Ubuntu by default, just go to System > Administration > Network Tools > Port Scan.

If you want a more advanced nmap GUI, get zenmap:

```
sudo apt-get install zenmap
```

Then open it from Applications > Internet > Zenmap

---

### Post by krisarnold on 2009-10-02
Thanks, 
I realized I was missing something. Now I have zenmap, and another question. Since it is a GUI, how do I run it as root?

---

### Post by kanikilu on 2009-10-02
> **krisarnold said:**
> Thanks, 
I realized I was missing something. Now I have zenmap, and another question. Since it is a GUI, how do I run it as root? ```
gksu zenmap
``` or edit the menu item for it: System > Preferences > Main Menu > Internet. Click on Zenmap, and then Properties. Change the command to "gksu zenmap %F" (w/o quotes) and close the menu editor.

---

### Post by krisarnold on 2009-10-02
Alright! Thanks a lot!

---

