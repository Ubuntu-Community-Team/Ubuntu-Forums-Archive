---
title: "Network Manager Icon missing after update to 13.10"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by prashanta2 on 2014-02-11
After updating from 13.04 to 13.10 the Network manager icon disappeared. All other icons are there, like sound, power management, etc, just nm is missing. If I run nm-applet on terminal it comes up to its rightful place. The problem is that whenever I close terminal the icon vanishes again. Tried many thing but can't seem to make it work. 

Any help would be appreciated.

Thanks

---

### Post by varunendra on 2014-02-11
Welcome to the forums prashanta2!

To make sure nm-applet is included in "Startup Applications", make sure its .desktop file is available in /etc/xdg/autostart directory, and is in default state.

Accordingly, please check the output of -
```
ls -1 /etc/xdg/autostart
```
Does it show "nm-applet.desktop" in the list? If yes, check its contents :
```
cat /etc/xdg/autostart/nm-applet.desktop
```

For reference, here's its contents from my 12.04 installation -
```
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
**NoDisplay=[COLOR="#006400"]false[/COLOR]**
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```
(Note that the "NoDisplay=" value by default is "true". I changed it manually to make it appear in "Startup Applications").

By the way, you can run the "nm-applet" command with Alt-F2 also, so that you don't have to keep a terminal running in the background :) -
**Alt-F2 > nm-applet > press 'Enter'**

---

### Post by Bucky Ball on 2014-02-11
Second of your posts I've moved to its own thread today. Please refrain from hijacking threads. If you have a support question, post a new thread and ask it there. You will greatly increase your chances of getting help rather than reducing someone else's and will also avoid creating confusion.

Thanks.

---

### Post by varunendra on 2014-02-11
> **Bucky Ball said:**
> If you have a support question, post a new thread and ask it there. You will greatly increase your chances of getting help rather than reducing someone else's and will also avoid creating confusion.

Thanks.

+1

*[By the way, I'm posting just so it starts showing up in 'MY' search results. It won't until 'I' make a new post in it, as I've experienced and reported a few times before. Forum bug I guess (regarding posts moved to their own threads).]*

---

### Post by prashanta2 on 2014-02-11
Hello Varunedra,

tried your solution. Still not working.

The applet is showed in the autostart output and I change the value from true to false. Still not showing after reboot.

The ALT-F2 is useful though, since I do not need to keep terminal open.

---

### Post by varunendra on 2014-02-11
Maybe a possible upgrading bug then? Most probably crashing nm-applet at startup. Can we see the contents of your nm-applet.desktop file please?

And have you tried reinstalling Network Manager yet? If not, please try this -

1) Update repository, update the packages and download the NM packages beforehand, so you can install them offline :
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```

2) Purge the current installation :
```
sudo apt-get purge network-manager-gnome network-manager
```

3) Reboot and reinstall the packges :
```
sudo apt-get install netwok-manager network-manager-gnome
```

Does it bring the nm-applet back? If not, maybe file a bug report against it at launchpad. The command to collect relevant information for bug report -
```
apport-bug
```
How to effectively Report a Bug : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by prashanta2 on 2014-02-11
Did not work the reinstall...posting here the nm-applet.desktop```
[Desktop Entry]Name=NetworkComment=Manage your network connectionsIcon=nm-device-wirelessExec=nm-appletTerminal=falseType=ApplicationNoDisplay=trueNotShowIn=KDE;X-GNOME-Bugzilla-Bugzilla=GNOMEX-GNOME-Bugzilla-Product=NetworkManagerX-GNOME-Bugzilla-Component=nm-appletX-GNOME-Autostart-enabled=trueAutostartCondition=GNOME3 unless-session gnomeX-GNOME-UsesNotifications=trueX-Ubuntu-Gettext-Domain=nm-applet
```will try to file the bug report in the meanwhile...

---

### Post by prashanta2 on 2014-02-11
I'm not really a tech savy... could not understand how to file a bug report...

---

### Post by varunendra on 2014-02-12
Yeah, the bug reporting system does seem to be a daunting task by that wiki page, although it is not. That's why I hesitate in linking to it. :P

You can simply register on the launchpad, then follow the instructions/prompts by the "apport-bug" command to collect and submit the details it collects. You may also submit a bug report without those details (just give it a suitable title, and mention the details as you do here in the forum threads), in which case the people there *should* ask you to collect and post relevant details (telling you how to do that, if you needed help with that). The wiki page just tells how to get attention quickly.

I hope you understand that filing bug reports is actually contributing to the community to make things better, not just a way to get your own problem solved, hence is a respectable thing. No problem if you can't do it right in the first few attempts, you are trying to help. :)

Anyway, the part highlighted in red below doesn't look good to me -
> **prashanta2 said:**
> ```

[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-Autostart-enabled=true
**[COLOR="#FF0000"]AutostartCondition=GNOME3 unless-session gnomeX-GNOME-Uses[/COLOR]**
Notifications=true
X-Ubuntu-Gettext-Domain=nm-applet

```
Why is there a condition? And the condition looks suspicious to me. Please try removing it, by editing it out (with root privileges) with your text editor, or via command -
```
sudo sed -i '/^AutostartCondition/ d' /etc/xdg/autostart/nm-applet.desktop
```

For confirmation, please post the contents again (after running above command, and preferably after a reboot) -
```
cat /etc/xdg/autostart/nm-applet.desktop
```

---

### Post by prashanta2 on 2014-02-12
It works!!! It works!!!

Great, thank you so much. After several reboots, the icon is always there where it should!

Posting the file:
```
[Desktop Entry]Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-Autostart-enabled=true
X-GNOME-UsesNotifications=true
X-Ubuntu-Gettext-Domain=nm-applet
```

I am marking this post has solved.

---

### Post by varunendra on 2014-02-12
Yay !! for our little victory :P

---

