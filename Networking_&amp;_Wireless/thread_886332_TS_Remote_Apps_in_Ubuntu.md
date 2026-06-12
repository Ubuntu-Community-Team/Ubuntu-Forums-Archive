---
title: "TS Remote Apps in Ubuntu"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by cobra741 on 2008-08-11
Hey All. 

I was wondering if there's any way if me making my Server 2008 (TS Gateway) remote apps work in ubuntu?

i'm guessing it'll probably be a no considering RDP is shaky at best (with my laptop at least :)  ) but figured it's worth asking. 

Please save me from having to boot into vista for this!!! :roll:
Any help would be greatly appreciated.. 

Cheers,
Steve

---

### Post by abbbottt on 2011-08-10
I have been banging my head against the wall for weeks trying to look for any solution to get connected to work network through a damn TS Gateway. In the end I found a solution that I'm not 'idealistically' happy with but am just bloody glad IT FINALLY WORKS.

If you're in a similar position and can live with a small diversion from your FOSS ideals then it's 20 Euros well spent!

[http://itap-mobile.com/desktop/rdp](http://itap-mobile.com/desktop/rdp)

Think this is fairly new...? Hope this helps some of you guys out!

Chris

---

### Post by whatspaz on 2011-11-29
It is now possible to load Windows RemoteApps from Windows Server using an up and coming project called FreeRDP. You'll have to compile your own to get much use out of it at this point, but there should be a stable 1.0 coming soon. Also, take a look and see if Remmina has incorporated the RemoteApp feature; as of this writing, I wasn't able to get that to work just yet.

[http://www.freerdp.com/]("http://www.freerdp.com/")

I have also wrote some FreeRDP + RemoteApps integration scripts for GNOME on Ubuntu. I suggest anyone wanting to run FreeRDP-powered RemoteApps in Ubuntu to try out these scripts. They take away much of the complexity needed to get RemoteApps onto the GNOME Main Menu and to launch your RemoteApps by file extension / mime-type associations when opening local files. Basically I have my notebook where I can double-click a .doc file in Nautilus and launch Microsoft Word via a RemoteApp deployment on my Ubuntu system. It's fantastic stuff, and it wouldn't have even been possible without the great work they've done at FreeRDP. My scripts:

[http://www.daball.me/2011/11/windows-meet-linux-linux-meet-remoteapp.html]("http://www.daball.me/2011/11/windows-meet-linux-linux-meet-remoteapp.html")

---

