---
title: "[SOLVED] Multiple Wireless Configs."
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by jay019 on 2007-07-20
Hi All,

I have a home wireless network with WPA and after following the howto I managed to get the laptop to connect to the wireless router. However when I go to the library that has free wireless broadband I have difficulty changing my network config back. I tried the gnome network applet but it doesnt seem to work after following the howto.

Is there any way of creating two configs one for home and one for the library and then easily switching between the two?

Thanks.

Jay
[SIZE="4"][COLOR="DarkOrange"]
UPDATE: Solved thanks to [WICD]("http://wicd.sourceforge.net/")!!! Top stuff wjp.reg!!![/COLOR][/SIZE]

---

### Post by wjp.reg on 2007-07-20
You did not describe how you got wireless working or what version of buntu you installed, but Feisty 7.04 has an upgraded network manager app whichdoes everything you want :-)

Check out this wiki:

[https://wiki.ubuntu.com/7.04Tour]("https://wiki.ubuntu.com/7.04Tour")

Cheers!

EDIT: Sorry, didn't notice your signature at first; you DID suggest you're using 6.10.  Maybe do an upgrade?

---

### Post by jay019 on 2007-07-20
Hi,

I got wireless working thanks to this thread [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

Thought about an upgrade, but at this time it's not possible.

Thanks.

---

### Post by jay019 on 2007-07-20
Should probably mention that at home I use a static IP but at the library it DHCP. So even if I upgrade the network-manager wont be much help would it (no static ip?)

Jay

---

### Post by wjp.reg on 2007-07-20
jay019;

Did you see this thread?  May be helpful.

[http://ubuntuforums.org/showthread.php?t=505341]("http://ubuntuforums.org/showthread.php?t=505341")

with reference to a replacement network manager [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by jay019 on 2007-07-20
Hi,

Thanks for replying! Checking out wicd. May take a little while...
At the moment I'm using my desktops dial up connection via the wireless router and VNC. lol!
Windows ICS just wouldnt work, which is not that bad as VNC is much better anyway. I can transfer files over smb and I can shutdown the computer from the bedroom, so its all good. 

Jay

---

### Post by jay019 on 2007-07-20
[WICD RULES!!!]("http://wicd.sourceforge.net/") 

Thanks heaps for the suggestion wjp.reg!

I recommend it to anyone who wants roaming with WPA. In fact, I recommend it as a replacement for the default network-manager full stop.

---

### Post by TravMan63 on 2007-08-09
WICD  DOES work much better...

but..

I'm having intermittant starts - it doesn't always start with gnome (does not appear in tray)

It never has started up as soon as network manager did (in the boot sequence - I would be connected before gdm started, now it starts after log on)

IT DOES - however WORK - for multiple networks - (WAPS) - MUCH better than gnome network manager ever did for me.

I'm not sure where it stores it's config files.  I had /etc/network/interfaces config'd with my wep key essid etc for gnome network manager to work - I had to rename/delete that file for wicd to work.

TM

---

### Post by imdano on 2007-08-10
Your config files are in /opt/wicd/data.  What version of wicd are you using?  Some other people have reported that startup issue, but I think I might have it fixed in the newest SVN version.

---

### Post by TravMan63 on 2007-08-10
1.3.1 

seems to 'pause' at least at 1st - before the config screen will display

I suppose there is a way to have it start earlier in the boot sequence as well?

--- edit
After I re-uninstalled it 1-2x-3x it now connects well before gdm starts.
One install did not have the tray.?? file extracted/installed.

Easy workaround is to make a launcher for it.
--

---

