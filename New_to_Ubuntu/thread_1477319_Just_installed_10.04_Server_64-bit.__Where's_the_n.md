---
title: "Just installed 10.04 Server 64-bit.  Where's the nm-applet at for manageing wifi?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-08
I just installed Ubuntu 10.04 Server 64-bit edition for someone on a new computer I just built for them.  I've not messed with the server edition before so it's been a bit of a learning experience for me (having to install a GUI, for instance... forgot about that not being installed by default).

Anyway, system is up and running fine after installing the "ubuntu-desktop" package and all available updates.

Only problem is, there is a wifi card in this system that I'd like to configure but I don't see the regular Network Manager Applet available in the upper panel like I'm used to seeing.

Checking the System Monitor Processor Viewer shows that it is running, and ending the process followed by manually starting it back up via ALT-F2 fires it back up, but it still doesn't appear in the panel.  I don't even see "Successfully connected to ath0" when I plug in an Ethernet cable, but the interface is working (I'm posting from this PC right now).

Above all I just need an app that will let me manage WiFi network connections and I like using the traditional nm-applet package for this.  But it's either not working or some other package that's normally installed with the Desktop edition of Ubuntu is missing, causing what I need to not appear in the upper panel.

Any help would be greatly appreciated.  Thanks!!

---

### Post by cariboo on 2010-05-08
You may want to install:

[list]
[*] network-manager-gnome
[*] network-manager
[/list]

They are  both in the repositories. 

If you want to set up wireless manually with out installing network manager have a look at [this]("http://ubuntuforums.org/showthread.php?t=571188") howto.

---

