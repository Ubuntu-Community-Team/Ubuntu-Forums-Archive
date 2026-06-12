---
title: "Azureus crashes on load...missing package?"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by yaazz on 2007-07-30
Everytime I attempt to load Azureus, nothing happens. 
When I look at the terminal output, it appears that I need to add an eclipse package. Can someone tell me what this package is?

~$ azureus
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Display
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
~$

---

### Post by lonce on 2007-07-30
This has to do with the .jar file.  Download the previous version of azureus and just replace the  current .jar with the older .jar file.  

Worked like a champ for me.

---

