---
title: "Good VNC client"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by movb on 2007-04-11
Hi all

I have got a windows box and want to connect it through the net. I installed UltraVNC server on windows machine. Before it I was using Radmin software.

Is there a good client for my ubuntu to connect it?
I tried several: vncviever, krdc..

But i want some features like file transfer, listening sound on winbox, normal cursor, proporional resizing screen and saving properties for next session.

Is it real?

---

### Post by kc0eks on 2007-04-14
I am looking for something similar, I loved UltraVNC on windows. I havent found anything I like much on ubuntu in the way of VNC.

---

### Post by xpan on 2007-04-17
similar problem here...

---

### Post by dangling participle on 2007-05-11
i just tested the ultravnc standalone viewer using wine, and i can say that in my quick testing, 

*remote desktop works
*file transfers work

that's all I really need so i am happy.  I noticed that the top toolbar in the viewer doesn't work, but there's a file transfer button in the main window so it's ok.  the wine output says:
fixme:toolbar:TOOLBAR_SetRows multiple rows not supported!

google how to install wine on ubuntu, then download the standalone ultraVNC viewer, then run: 

wine vncviewer.exe

cheers!

im gonna test out the tabbed vnc viewer, see if that works any better.

---

### Post by dangling participle on 2007-05-11
tabbed vnc viewer doesn't work as well. it crashes on connect, with this output:

X Error of failed request:  BadPixmap (invalid Pixmap parameter)

  Major opcode of failed request:  54 (X_FreePixmap)

  Resource id in failed request:  0x4800480

  Serial number of failed request:  8029

  Current serial number in output stream:  8155

---

### Post by docsmooth on 2007-05-11
Unless you're using WinXP Home, this will work (WinXP Home doesn't support RDP outside of RemoteAssistance)

rdesktop -0 -g 1024x768 -a 15 -r sound:local -r disk:C=/home/username -r clipboard:CLIPBOARD windows-box.dyndns.org

-0 = connect to console, optional
-g = geometry
-r = redirect
-a = colors

There's a lot of optionsin the help file.  I have the above line (minus the "windows-box..." part) aliased to "rdp" so I can "rdp servername" and have all my fun stuff.

On WinXP, right-click My Computer, choose "Properties" then the "Remote" tab, and pick "allow remote connections".  Click "OK" and test.

---

