---
title: "Network Issues after clean installation of gutsy"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by experience on 2007-10-29
I am experiencing annoying network problems which disappointed me a lot. I did do some searching and adjusting, and I fixed most of them, but there are still some issues I have nothing to do with them.

Issue 1:
I start the computer with wired network, connect the computer to a new wireless network through the networkmanager, Then I can't go back to the wired network. no response if I click the wired network on the networkmanager. Only a "sudo /etc/init.d/dbus restart" will reconnect the computer back to the wired network. But I will lose any possibility to connect to any wireless network. Either the networkmanager will crash when I click the "Connect to other wireless network". Even the "sudo /etc/init.d/dbus restart" or "sudo /etc/init.d/networking restart" won't work.

Issue 2:
I can't reconnect the computer back to the wireless network after a suspend-and-wake-up action. I find some post talking about losing wired network connection after suspend, the "sudo /etc/init.d/dbus restart" might work. Or adding a line in the a line "networking" in the acpi-suppout will possibly work. But actually nothing happened.

Issue 3:
After "sudo /etc/init.d/dbus restart" the gnome-keyring-daemon will not start. then I will have to tell the nm-applet the wireless network password again and again....

Issue 4:
Sometime when the nm-applet crashed, and I started it manually by "nm-applet --sm-disable", I will get a icon with a primary click menu says that "No network interface found". #$%^&*, There are interfaces when I call the "Ifconfig" command. but nm-applet failed to get any response from the dbus functions. what a shame.

Help me please. These issues keeps me from deploying the Ubuntu in a productive environment.

---

