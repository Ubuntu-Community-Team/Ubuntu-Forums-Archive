---
title: "update error"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by sjparida on 2011-04-17
Hi, everyone
i m new to ubuntu and using ubuntu 10.10 
as i was trying to update ubuntu using the update manager its always showing me this error
plz help me out and pardon me for my english

-------------------------------------------------------------------------------------------------------------------------
E: Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.
-------------------------------------------------------------------------------------------------------------------------

---

### Post by Paqman on 2011-04-17
At the bottom of the Update Manager is a button marked "Settings", click on it, go the the "Other software" tab and check the entry for that PPA in the error message. It looks like the line is mlaformed. The easiest thing to do is probably just to delete the entry for that PPA then add it again. To do that enter:
```
sudo add-apt-respository ppa:tualatrix/ppa
```

---

### Post by sjparida on 2011-04-17
thnx for your quick reply but as i am opening the update manager it is showing a error window with this message and closing automatically 

-------------------------------------------------------------------------------------------------------
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list'
-------------------------------------------------------------------------------------------------------

---

### Post by Paqman on 2011-04-17
Ok, lets change tack and edit the offending file directly.
```
gksudo gedit /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

Replace both lines with:
```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main 
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main 
```

If you're using a version other than Maverick, edit the entry appropriately.

---

