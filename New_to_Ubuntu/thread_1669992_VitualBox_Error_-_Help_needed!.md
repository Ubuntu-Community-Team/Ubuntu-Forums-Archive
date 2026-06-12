---
title: "VitualBox Error - Help needed!"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by techningeer on 2011-01-18
I use Oracle VirtualBox Version 4.0on a Ubuntu 10.04 64bit PC. I was just going to start my VM today and it started in a snapshot that I had taken yesterday. I didn't choose to restore a snapshot. Then it told me that there wasn't any bootable media. I tried to attach the hard drive to the machine, but this is what it said:


Failed to attach the hard disk (**/home/myname/.VirtualBox/HardDisks/NewHardDisk.vdi**) to the slot *IDE Primary Master* of the machine **Dell Home Edition**.

Details


Result Code: VBOX_E_INVALID_OBJECT_STATE (0x80BB0007)
Component: Medium
Interface: IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
Callee: IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}


Then it said:

Failed to save the settings of the virtual machine **Dell Home Edition** to 
**/home/myname/.VirtualBox/Machines/Dell Home Edition.xml**.

Details:

Result Code: 
VBOX_E_INVALID_OBJECT_STATE (0x80BB0007)
Component: 
Medium
Interface: 
IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
Callee: 
IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}


Now I tried to start my machine, but it said:

Failed to open a session for the virtual machine **Dell Home Edition**.

Unknown error creating VM (VERR_NO_MEMORY).

Details:

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}


I attached the logs also.
Any help is greatly appreciated! Thanks
--techningeer

---

### Post by ubudog on 2011-01-18
Does this help?

[http://forums.virtualbox.org/viewtopic.php?f=1&t=31938](http://forums.virtualbox.org/viewtopic.php?f=1&t=31938)

---

### Post by techningeer on 2011-01-18
Thanks, ubudog for the suggestion. My hard drive now works and so does the machine.

---

### Post by KingPin2011 on 2011-02-07
How Can i Solve this problem???

please explain as not technical as possible i spent over hour on this and still cant figure out.

---

