---
title: "nm-applet and KDE"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by jakejas on 2008-03-09
I am having problems with network manager in KDE (not knetwork manager). I liked the nm-applet in ubuntu, and xubuntu, so I decided to try it in Kubuntu. I ran it from the command line, and I can not figure out how to shut it off, or not get it to load automatically when the computer starts. Also, every time I log into my network, it wants the password for the network. In GDE and XDE, it only asks for it once and then it saves it and I don't have to enter it every time, but for some reason in KDE it does not do this. I like the program, because it handles wpa well, but I can't figure out how to get it to save the keys, close, and not load automatically. If anyone could help me with this I would appreciate it. I have searched the forums, and could not find another post to help me.

Thanks,
Jake

---

### Post by ajgreeny on 2008-03-09
Surely you can run at startup the same as any other application; just add a launcher to it to the ~/.kde/Autostart folder.  If you have to start it in terminal, that can be done with the launcher properties when you make it in the first place.  To stop it you can do it in terminal if you wish with ```
killall application_name
```  Password retention may be possible with kwallet, but that may only work with kde applications, I'm not sure about that.

---

