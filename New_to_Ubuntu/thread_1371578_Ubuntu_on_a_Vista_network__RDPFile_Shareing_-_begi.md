---
title: "Ubuntu on a Vista network  RDP/File Shareing - beginer help please"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by akira2501 on 2010-01-03
[FONT=Calibri][SIZE=3]Hello everyone, I’m new to Linux and the forum here and I’m looking for some guidance.  I’m sure my questions aren’t original so if possible, please point me to existing guides.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I’ve searched heavily for a couple days now, but with all the variables involved, and my complete ignorance to Linux and command lines, I’ve been unable to resolve my issues.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Both issues are concerning getting Unbuntu 9.10 to integrate into a Windows Vista network (workgroup).[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Issue 1:  RDP: Cannot Remote Desktop from or two the Linux machine; I’ve completed all GUI-based steps to connect. Vista posts the genaric "unable to connect" message.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Issue 2: Network File Sharing:  Ubuntu can access Windows shares.  It posts come errors about being “unable to mount” but accesses the drives anyway.  I cannot however access the Linux machine from Windows.   It can be pinged by its IP but does not appear.  (Samba is installed and configured to the best of my limited knowledge).[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]That’s all for now, Thank you for your time.[/SIZE][/FONT]

---

### Post by bodhi.zazen on 2010-01-03
Those are two issues and you may have better luck with one issue per thread.

Second, please use the default font size. If you can not read the text adjust the text size on your browser.

For your RDP connection are you trying to connect to the windows box from Ubuntu or to Ubuntu from Windows ?

Likewise with your file sharing, which is the server and which is the client ?

Ie is the shared directory on Windows and you are trying to connect from Ubuntu or is the share on Ubuntu and you are trying to connect from Windows ?

My guess is you have a firewall , most likely on Windows, blocking the connection attempts.

Please describe what guide you are following, what step you are on, and the exact error message you are getting.

Otherwise see :

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by akira2501 on 2010-01-03
Hi, thank you for the response.

Sorry about the text size, I did a copy and paste, didn’t realize it changed the font.

For the file sharing, I’m trying to get Windows to access Ubuntu.  Ubuntu would be the file server in this case and Windows the client.  
 
I’ve successfully configured Ubuntu to access the Vista shares (with Vista as the server).

This is on a workgroup, not a domain.

There is no error on either Windows or Ubuntu, the problem is that the Windows machines are unaware of the existence of the Ubuntu machine.  The opposite is not true, Ubuntu can browse and access the windows PCs.

---

### Post by The Cog on 2010-01-03
For RDP to Vista, use Programs->Internet->Terminal Server Client.

For Vista to Ubuntu, you need to install a VNC viewer on Vista, and in Ubuntu, System->Preferences->Remote Desktop choose to allow others to view the desktop.

---

### Post by akira2501 on 2010-01-03
Ok I've gotten a bit farther by re-editing the SAMBA config file.
 
I can now see the Ubuntu computer on the Windows network.
I receive the following error when attempting to map to a drive:
 
"Check the spelling of the name. Otherwise, there might be a problem with your network."
 
Second error "Windows confirmed that the server "SERVERNAME" exists, but cannot find "sharename".
 
Also there are two shares visable through windows browse:

One was created through Samba.  This one gets the error message.
 
The other share was created through righ-click "share" on Ubuntu.  This share prompts me for a user name and password, but will not let me in.
 
Any ideas

---

