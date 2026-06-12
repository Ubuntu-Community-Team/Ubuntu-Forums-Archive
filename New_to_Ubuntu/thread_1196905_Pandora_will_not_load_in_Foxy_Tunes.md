---
title: "Pandora will not load in Foxy Tunes"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by dansar99 on 2009-06-25
I can not get Pandora to finish loading in Firefox.  the loadbar only goes so far and then stalls.  Thank you for any help.  Dan

---

### Post by lovinglinux on 2009-06-25
The solution to your problem is in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **lovinglinux said:**
> 

**Problems:**

[list][*] 
[*] **Can't play streaming videos**
[*] **Flash videos display only a symbol and won't start**[/list]

**Solution:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content. You can disable plug-ins through the Addons window. Open "Tools >> Addons", then select the "Plug-ins" icon, then select the plug-in you want to disable and click the "Disable" button. Unfortunately, this not work every time, so the best procedure is to remove the conflicting plug-ins.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

To solve additional video issues, visit the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It solves most of the problems related to video codecs and plug-ins.

---

