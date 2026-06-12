---
title: "I need remote desktop control capability in Ubuntu 9.1"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by RedOctober on 2009-12-19
Situation:

Small medical clinic, 20 XP user machines, all remote desktopping (.rdp) into a single Windows Server 2003.  Microsoft is forcing us to Office 2007, Vista/Win7.

Goal:

Replace all XP machines with Ubuntu 9.10


Objectives:

Each Ubuntu machine must have:

1) Skype
2) OpenOffice 3.1
3) .Rdp capability into the server to run all Windows apps on the server

Progress:

Objective 1 and 2 are accomplished.  Objective 3... I'm stuck.  I read a bit about "remote desktop -ish" stuff in this forum, but I'm not sure which method is best, or which method applies to Unbuntu 9.10.  I need to see the Windows desktop on the Windows Server 2003 machine the same way it appears on my XP boxes.  If I can't accomplish Objective 3, then Ubuntu is a "no go" and I'll put my plans back on the shelf for another year, and not look at it again until Ubuntu has this capability out of the box.  For now, I'd appreciate any advice you can give me.  I'll install stuff, configure stuff, what ever, as long as it works fast and reliable.  Thanks in advance for any help.

---

### Post by tom.swartz07 on 2009-12-19
> **RedOctober said:**
> Situation:

Small medical clinic, 20 XP user machines, all remote desktopping (.rdp) into a single Windows Server 2003.  Microsoft is forcing us to Office 2007, Vista/Win7.

Goal:

Replace all XP machines with Ubuntu 9.10


Objectives:

Each Ubuntu machine must have:

1) Skype
2) OpenOffice 3.1
3) .Rdp capability into the server to run all Windows apps on the server

Progress:

Objective 1 and 2 are accomplished.  Objective 3... I'm stuck.  I read a bit about "remote desktop -ish" stuff in this forum, but I'm not sure which method is best, or which method applies to Unbuntu 9.10.  I need to see the Windows desktop on the Windows Server 2003 machine the same way it appears on my XP boxes.  If I can't accomplish Objective 3, then Ubuntu is a "no go" and I'll put my plans back on the shelf for another year, and not look at it again until Ubuntu has this capability out of the box.  For now, I'd appreciate any advice you can give me.  I'll install stuff, configure stuff, what ever, as long as it works fast and reliable.  Thanks in advance for any help.

Ubuntu has Remote Desktop built in, from the start. Assuming youre using Karmic (9.10), go to Applications, Internet, Remote Desktop Viewer. 

You could also configure your Ubuntu boxes to accept remote connections by using System, Preferences, Remote Desktop. This program will also give you information that you need to connect from other computers.

Ive had no problems using PUTTY and various VNC programs from my iPhone.

Let us know if thats what you needed!
Hope this helps!

---

### Post by 3rdalbum on 2009-12-19
Windows' Remote Desktop system uses RDP, not VNC.

Ubuntu's Terminal Server Client program can work with RDP desktop sharing without problems.

And it is preinstalled on Ubuntu.

Have a good migration :-)

---

### Post by tom.swartz07 on 2009-12-19
> **3rdalbum said:**
> Windows' Remote Desktop system uses RDP, not VNC.

Ubuntu's Terminal Server Client program can work with RDP desktop sharing without problems.


Sorry, thats what I meant. Ubuntu uses RDP and VNC both in the same program.

---

### Post by RedOctober on 2009-12-19
BINGO!  Terminal Server Client is what I was looking for.  I got it working. THANKS BUDDY!

---

### Post by RedOctober on 2009-12-28
Thanks for the help.  It worked.  Next step... I need to make a "desktop shortcut" (In "Windows" lingo) to this .rdp connection.  I've already saved it in my accounts folder/ .tsclient... but, I cannot "view" this folder...and I don't know how to make a desktop shortcut to it, so that my users can simply click on the desktop icon and connect.  How do I do that?

---

### Post by The Cog on 2009-12-28
Right-click the desktop and choose Create Launcher. The command will be something like **rdesktop 1.2.3.4** but there are lots of options you can add such as usename. Use the command **man rdesktop** to see what the options are. You can try the command out in the terminal before entering it into the launcher of course.

---

### Post by RedOctober on 2009-12-28
Works.  Thanks!

---

