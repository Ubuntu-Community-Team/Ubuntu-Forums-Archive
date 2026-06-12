---
title: "[SOLVED] File and printer sharing between Ubuntu 6.06 and Windows XP"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2006-10-30
OK, so after awhile I finally got my Ubuntu machine to work with my WUSB54G wireless network adapter. The Internet is fine. However, I would like my Ubuntu machine to be able to share designated files and folders, as well as my printer with my main PC (Windows XP box).The Ubuntu machine and the Windows machine are sitting 3 feet away from each other on opposite sides of my desk. Through a KVM switch they share my keyboard, monitor, and mouse. They are both individually connected to my wireless home network with WUSB54G adapters. How do I go about making this happen. I downloaded and installed Samba and tried a few things but I could not get the Ubuntu machine to manipulate or see anything on the Windows machine. Please help!!

---

### Post by Kulgan on 2006-10-30
is the windows machine part of a work group or domain?

If you haven't set up file-sharing in windows, you have to do that first :P 
To start the Network Setup Wizard:
Click [Start] [Control Panel] [Network and Internet Connections]
Under [Pick A Task...] click [Set Up Or Change Your Home Or Small Office Network]
The Network Setup Wizard will open, and you can select you desired workgroup. Blah blah blah. [this]("http://www.theeldergeek.com/quick_guide_to_simple_file_sharing.htm") might help. -.-

When you share a folde and it appears in "Shared Folders" in windows, it should be listed in "Places -> Network Servers -> <WORK GROUP> -> <HOST COMP NAME>", in my case "MSHOME -> DESKTOP".

If you are looking to set up samba to share files FROM linux, it is in "System -> Administration -> Shared Folders" thou shalt seeketh. There's a good walkthrough somewhere, I'll see if I can find it...

---
found it : [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
---

---

