---
title: "Installed anon-proxy not showup in menu"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by plowhman on 2009-11-06
I just updated to ubuntu9.10 version and had installed Anon-Proxy through Synaptic Packet Manager. Expecting an icon to show up in the menu (Application>internet>anon) as the previous version 9.04 did. However it was not. 

How could I start Anon-proxy now?

Is there any way to creat the icon into the menu manually?

Any help please!

---

### Post by plowhman on 2009-11-06
[Adding] Its GUI is missing. I prefer to have the GUI for easy to control its on/off. 
[B]
[/B]

---

### Post by MatisseGroening on 2009-11-15
I just made the browser use localhost 4001 and it worked. Actually I don't need the GUI that much, but it seems missing and there is no download. 

In the Console there is an error:

[2009/11/15-17:37:07, critical] Error: Cannot parse configuration file!
[2009/11/15-17:37:07, critical] Terminating Programm!

I think you just have to create the config file and it should be startable.

---

### Post by Dude-PWB- on 2009-11-15
You need to install the JonDo client as well for anon-proxy. It still requires you to change the settings in your browser, or use their profile for firefox called jondofox but at least you can see what mixes you are connected to with the JonDo gui.

---

