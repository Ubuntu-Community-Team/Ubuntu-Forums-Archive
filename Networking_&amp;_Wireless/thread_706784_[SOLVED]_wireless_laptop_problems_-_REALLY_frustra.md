---
title: "[SOLVED] wireless laptop problems - REALLY frustrating network manager"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by bluepowder7 on 2008-02-24
hello all.

first, i apologize if i seem a bit irritated, but honestly i am.  mr.network manager applet is driving me INSANE and i've got no idea why.

my laptop has a wired and wireless interface.  drivers are installed, all is fine when it works.  i want to have static IP on both wired and wireless interfaces, and that appears to be impossible for network manager applet to handle.

i can do the static IP using wired, so that part is ok.  but if i want to do static IP using wireless, i have to turn off roaming.  if i do that, 99% of the time it won't connect to my wireless router.  i do have the SSID and passwords entered in the various fields (when i turn off roaming), but for some reason it still just does not connect.  my laptop currently is 3 feet away from the router, so signal strength is not an issue.

another problem (which drives me even more insane) is that if i want to modify anything in network manager, i need to reboot.  wanna go wired?  plug in the cable and reboot.  wanna go wireless?  unplug the cable, reboot, and hope it actually connects (see above).

how do i:

1 - get network manager to let me use static IP on the laptop and just bloody connect to the router?
2 - get network manager to accept changes without having to reboot or sit-n-wait for a long time?  (sometimes, though rarely, it'll accept and work with changes after 5 minutes or so)
3 - get network manager to let me change from wired to wireless and back again without having to reboot?

---

### Post by mrsteveman1 on 2008-02-24
I think this is something only the developers can solve. NM has serious issues thats for sure.

I've never used it but I've heard other people recommend WiCD

---

### Post by bluepowder7 on 2008-02-24
if i install WiCD, can i then uninstall NM safely?
how would i go about determining which applet i'm using to establish connections if i still have both installed? (if, for example, i want to make sure WiCD works before blowing away NM)

also, if i connect my ethernet cable, how can i check which interface is actually being used (wired or wireless)?


EDIT - ok, i found and installed WiCD, and it blew away NM.  hmm, this seems to work MUCH better!  i can set static IP's for wired and wireless, and so far it works.

THANKS!!!  man, i wish someone had recommended this before!  i've put in quite a few tickets about NM being a flakey POS that i was about to ditch ubuntu altogether because of it.

---

### Post by mrsteveman1 on 2008-02-24
I'm glad things work :D

NetworkManager the daemon isn't all that bad as far as i can tell, but the frontends need some work.

---

### Post by kelbizzle on 2008-02-24
Did you uninstall NM all together? I have the same problem when I take the laptop into the office.

---

### Post by bluepowder7 on 2008-02-25
> **kelbizzle said:**
> Did you uninstall NM all together? I have the same problem when I take the laptop into the office.

when i installed WiCD from Synaptic, it automatically told me that it has to uninstall NM.  i assumed it blew away all of it, since i didn't do any additional removing or cleanup after that.


from the [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) page:

> Installing Wicd in Ubuntu

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) [r]**feisty**[/r] extras 

where [r]**feisty**[/r] is your version of Ubuntu (Dapper, Edgy, Feisty, Gutsy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".



.

---

