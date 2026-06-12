---
title: "Keyboard layout changes on thin clients"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by conand on 2010-12-03
Hi!
 
I have setup a small network with a server running LTSP on Edubuntu 10.04, and seven thin clients. The server is configured to use a Swedish keyboard layout (works fine), but for some reason the keyboard layout changes to English for several of the network users on the thin clients (especially when running OpenOffice). The users use the same profile, and do not have access to the setup functions (so they haven't changed it themselves).
 
Happy to get any suggestions at all about what could be wrong.
 
Thanks in advance!

---

### Post by conand on 2010-12-23
The complete solution can be found at [http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html) 
 
In short, you have to edit the [FONT=Courier New]lts.conf[/FONT] file and make the default keyboard swedish.
 
1. In terminal: [FONT=Courier New]gksudo gedit /opt/ltsp/i386/etc/lts.conf[/FONT]
2. Insert:
 
[FONT=Courier New][default][/FONT]
[FONT=Courier New]XKBLAYOUT=se[/FONT]

3. Save and close
4. In terminal: [FONT=Courier New]sudo ltsp-update-image[/FONT]

---

