---
title: "Remote login to Ubuntu machine using Ubuntu"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by bdfoster on 2008-07-04
I was wondering if it is possible to remotely login to another computer every time you had to login so that all settings would be the same. I would like it if both machines were still usable, I just want to be able to keep the same settings or atleast the same files on one computer. They both run dual boot with Windows (one with XP pro, the other with Vista) but I want to migrate over to Ubuntu. This isn't the first time I have delt with computers, I know windows very well. Anyone have any ideas? I have tried VNC through windows to one of the Ubuntu machines and that works but I haven't tried to do VNC from one Ubuntu to the other Ubuntu OS. They are both running Hardy, just installed a week ago.

P.S. One machine (the one with XP) is a desktop, the other a laptop. The laptop is the one I want to remotely login with. The laptop is wireless, both going through a Netgear router.

And I really would not want to have to use VNC.

---

### Post by bdfoster on 2008-08-04
Bump

---

### Post by cariboo on 2008-08-05
I don't know if this is waht you are looking for, but remote desktop is installed by default. To enable the rdp server got to System-->Preferences-->Remote Desktop and set up what you like. On your second computer go to Applications-->Internet-->Remote Desktop Viewer, click the connect button, enter the ip address of the computer you want to connect and you're done.

Jim

---

### Post by bdfoster on 2008-08-05
I figured it out just now. Used Remote Login via X server. Works great!

---

