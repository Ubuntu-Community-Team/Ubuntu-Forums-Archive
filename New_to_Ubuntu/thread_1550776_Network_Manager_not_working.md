---
title: "Network Manager not working"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-08-11
I have managed to uninstall and completely remove the NetWork Manager.
And as a result, I'm not online anymore... 
I have reinstalled NetworkManager and Gnome NetworkManager through an USB, but I still can't manage to get it online. My last solution is to reinstall Lucid. But if anyone has any better ideas I'd be very gratefull...:)

---

### Post by Uslayme on 2010-08-11
I don't know if this will help but the "default" packages for network management (as shown in Ubuntu's Software Center) are:

Network Manager
network management framework (PPTP plugin)
network management framework (PPTP plugin, GNOME UI)
network management framework daemon
database of mobile broadband service providers
network management framework (shared library) libnm-util1
Network Tools

It may be worth a shot to check your Applications > Ubuntu Software Center to see if these packages are installed.

---

### Post by tweety_r78 on 2010-08-11
Thank you so much for answering, but yes... I do have all of these installed..
But I can't find anyplace to "set" the internet connection... I used to have the icon of the Network Manager in the system panel, and I could set the internet connection there. But this icon is now gone...??!!

---

### Post by Uslayme on 2010-08-11
Try going to System > Preferences > Startup Applications and see if Network Manager is available, and enabled. If it is not there I would try these steps:

In Terminal type:

```
nm-applet --sm-enable

```This should start your Network Manager. Then go back to System > Preferences > Startup Applications and "ADD" Network Manager by selecting Add. 

Name: ```
Network Manager
```Command: ```
nm-applet --sm-disable
```Comment: ```
Control your network connections
```and then Save.

Note-The Command: entry is entered as "disable" because it should have started when you enabled it in the Terminal.
 
If your "Applet" is not in the top "Panel" try this: Right click on the Panel > Add to Panel > Notification Area to see if your applet is restored. If not, try the following procedure:

 					"Originally Posted by **ankur1990** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9236722#post9236722") 				
 				[I]Hey Fellas
nm-applet problem solved :grin: :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit  /etc/NetworkManager/nm-system-settings.conf" change the "managed=false"  to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :grin::grin:"

**The Quote is from this thread:  [http://ubuntuforums.org/showthread.php?t=1469625](http://ubuntuforums.org/showthread.php?t=1469625)**
[/I]
 
I hope this works for you :)

---

### Post by dineshs on 2010-08-11
1)system-preferences-startup applications
tick network manager
2)Right click on the top panel-click add to panel-select notification area -click add
3)```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
``` 
and set```
managed=true
```

---

