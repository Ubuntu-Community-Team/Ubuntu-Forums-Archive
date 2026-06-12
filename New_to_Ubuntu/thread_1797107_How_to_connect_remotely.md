---
title: "How to connect remotely?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-07-04
I want to know what's the simplest and easiest way to connect to a ubuntu machine remotely please?

The source machine will run windows 7

I want to install software and do everything else just like I'm sitting in front of the ubuntu machine.

Thanks

---

### Post by lmarmisa on 2011-07-04
I recommend TeamViewer:

[http://www.teamviewer.com](http://www.teamviewer.com)

---

### Post by seawolf167 on 2011-07-06
There are a couple ways of doing this, I'll list two different approaches.

You can connect via SSH, and [optionally] forward xwindows to your Windows 7 install. Information on SSH can be found [here]("https://help.ubuntu.com/community/SSH"). If you want to foward x to your Windows install you'll also need a window manager like xming running. Report back if you want more information on this.

Another way is to enable remote desktop on your machine (System -> Administration -> Remote Desktop [? not sure about the exact name]), select to enable remote desktop and enter a password instead of "prompt to allow each access". Then use a VNC viewer like [UltraVNCViewer ]("http://www.uvnc.com/download/1082/1082viewer.html")to connect to your remote machine from Windows.

---

### Post by Perkins on 2011-07-06
If you need to be able to connect to it from *any* windows machine without carrying software around (although VNC is pretty tiny and portable) try XRDP

[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

Then you can use Windows' native Remote Desktop program to connect.

---

