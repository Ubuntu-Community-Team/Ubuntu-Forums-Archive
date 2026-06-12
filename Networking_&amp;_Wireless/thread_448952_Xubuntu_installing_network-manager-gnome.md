---
title: "Xubuntu installing network-manager-gnome"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by MLTPaul on 2007-05-19
Tried Ubuntu 7.04 on my laptop- very much liked the new network manager that lets me tie into my WPA network. It was also way too slow.
   I read that Xubuntu 7.04 can use the same network-manager-gnome, and that it has a systray applet for XFCE. Installed Xubuntu and did the sudo aptget install network-manager-gnome and it says everything was installed. 
  So how does one get the new manager up and running? Have been all over the net and have yet to find instructions to replace the existing manager with the new and how to get an icon to show on the XFCE desktop. 
   The laptop currently can get onto a secondary WEP network and has no etherport.
TIA
Paul

---

### Post by ugm6hr on 2007-05-19
In a terminal:
nm-applet

Or - using GUI:
Using Thunar (File Manager), double-click file "/usr/bin/nm-applet"

This will run Network Manager in the taskbar panel (top-right).  Try not to click on it more than once - it ends up with three of the same icon, and now I can't get rid of the others (Process Manager will Term/Kill, but they reappear at reboot!)

I like Xubuntu7.04 too.  I have installed an icon in the top taskbar to allow it to be restarted again should it ever disappear.

---

### Post by MLTPaul on 2007-05-19
Tried the Thunar usr/bin/nm-applet...
No joke on the multiple icons!

The icon does not seem to relate to the new network-manager-gnome that allowed me to tap my WPA network in Ubuntu 7.04. It pulls up the stock Xubuntu network manager.

Suggestions? Might the fact that I have to have the stock manager running to tap the net to pull down the new version be impacting this?
Paul

---

### Post by MLTPaul on 2007-05-19
OK, let's rephrase this. 
How does one go from a stock Xubuntu 7.04 running on a WEP network, with no ethernet capability, to a Xubuntu 7.04 able to connect to a WPA network? 

I was able to connect WPA with Ubuntu 7.04 on this laptop; have since changed it to Xubuntu 7.04

Uninstall/reinstalls of network-manager network-manager-gnome gives me an icon in the upper right, but it's only talking about manual configurations, and if clicked, takes me to Xubuntu's old network manager. 

There do seem to be multiple folks like me out there, but no step by step seems to exist.

---

### Post by ugm6hr on 2007-05-20
Ok - I think I misunderstood your situation the first time (so sorry about the multiple icons you have too!).  Let me just double-check where you are.

You have already:
1. Installed "network-manager" and "network-manager-gnome" (check in Synaptic Package Manager)
2. Got a Network Manager icon in the Sys-tray (top right corner, next to clock) with 4 vertical bars filled with grey or blue (dependent on connection quality), which says "Wireless network connection to 'MyESSID' (39%)" when you roll the mouse pointer over it, or in your case, probably something like "No connection".

If this is true (and you probably now have more than 1 icon in Sys-tray after my error earlier), then:
1. Go to Applications -> System ->Network
2. In "Connections" Tab, select "Wireless Connection" and click "Properties"
3. Select "Enable roaming mode" (so that there is a tick in the box), and then click "OK" - if this is already selected, then this advice is obviously irrelevant
4. Select "Close"
5. Left click on the Network Manager Sys-tray icon, which should hopefully now list all available networks.

Hope this now works for you.  As I said, this is how I connect my Xubuntu7.04 laptop to my wireless router.

If this has solved your problem, I can now resolve the multiple Sys-tray icons situation too:
EDIT # see Belathor post below #
1. Go to Applications -> System -> Synaptic Package Manager
2. Click "Search" and enter "network-manager-gnome"
3. Right-click on "network-manager-gnome" and select "Mark for removal"
4. Click "Apply", and then keep accepting until it un-installs it.
5. Click "Search" and enter "network-manager-gnome"
6. Right-click on "network-manager-gnome" and select "Mark for installation"
7. Click "Apply", and then keep accepting until it installs it again.
8. When it's finished, DO NOT double-click on icon to run (as suggested)
EDIT # 8b. Restart computer #
9. Go to Applications -> Accessories -> Terminal
10. Type "nm-applet" and press Enter

Hopefully, you should now be back to just one Sys-tray icon again.  Essentially, it just un-installs and re-installs it, and runs it just once!

Don't give up on Xubuntu, I think it's great.  You can add as many useful shortcuts and managers to the taskbar panels as you could ever think of.  I've just added an AOL-style "You've got mail" entry for my pop mailbox that doubles as a shortcut to Thunderbird.  Battery Monitor is another good one for laptops, and I've found it useful to have a "File Explorer as root" shortcut too to allow full access to everywhere.  And I've only had it installed 3 days now.

EDIT #Note problem with multiple icons not quite resolved - probably best solution by Belathor below.  Nevertheless, I've edited my solution again - it was definitely something like that! #

---

### Post by MLTPaul on 2007-05-20
Thanks for the reply. Will check it out this afternoon,
Pau

---

### Post by Belathor on 2007-05-20
Thanks for the walkthrough ugm6hr! The first part worked for me and I now my applet. The cleaning up part about getting rid of the icons didn't though. I still have 5 nm-applet icons in my tray that seem to startup automatically when I log in. I'm going to go try to uninstall them, log out, and then reinstall them to see if that works.

EDIT: I marked network-manager-gnome for complete removal -> clicked apply a few times -> logged out -> logged back in -> reinstalled network-manager-gnome -> added nm-applet --sm-disable to my autostarted applications -> logged out -> logged back in and now there is only one icon.

---

### Post by MLTPaul on 2007-05-20
Big thanks to ugm6hr and Belathor!
For me the matter was selecting roaming on the network manager.
Also important for me to note was the double dash on  /usr/bin/nm-applet --sm-disable
50 year old eyes and a laptop...
Thanks again folks. Very much appreciated.
it actually works. 
Paul

---

### Post by ugm6hr on 2007-05-21
@MLTPaul:
Glad you're online with WPA :)
About making a typo with "--", I would suggest always cut and paste from these forums - it even works in Terminal.  Eyesight's not so important then ;)

---

### Post by ZeroXR on 2007-06-08
Funny... I just tried to do the instructions to minimize the instances to just 1 icon and somehow it gave me 3!

Any other work-arounds for this?

---

### Post by ugm6hr on 2007-06-08
> **ZeroXR said:**
> Funny... I just tried to do the instructions to minimize the instances to just 1 icon and somehow it gave me 3!

Any other work-arounds for this?

To get it to work:

> **Blofeld said:**
> Quick 101 tutorial:  getting rid of multiple printer and networking icons in Xfce (Xubuntu) system panel (the bit at the top right corner of the desktop):
* PRINTER ICON:  disable in "Xfce Menu > Settings > Autostarted applications" the "Print queue applet" and reboot.  There should only be one printer icon in the system panel now.
* NETWORKING ICON:  uninstall "NetworkManager Applet" in "Add/Remove Applications" or "Gnome Network Manager" in "Synaptic", reboot, reinstall, reboot.  There should now be no networking icon in the system panel.  Go to "Xfce Menu > Settings > Autostarted applications" and add "nm-applet --sm-disable" (the latter stands for "disable session manager"), and reboot.
And voilà, Bob's your uncle.

---

### Post by ZeroXR on 2007-06-08
I did as instructed and on the reinstalled NetMan tbe icons automatically pop up in the systray. Keep in mind I removed the entry from the auto-start... Is there something I am neglecting? Because the session manager is disabled from every reboot for me as of now.

From all this, I now have 5 icons and it's more bothering me than anything.

---

### Post by ugm6hr on 2007-06-09
> **ZeroXR said:**
> I did as instructed and on the reinstalled NetMan tbe icons automatically pop up in the systray. Keep in mind I removed the entry from the auto-start... Is there something I am neglecting? Because the session manager is disabled from every reboot for me as of now.

From all this, I now have 5 icons and it's more bothering me than anything.

When you re-install (after uninstalling) - DO NOT DOUBLE-CLICK to start as offered.
Why don't you want NM to auto-start?

---

### Post by ZeroXR on 2007-06-09
I was just making mention that I did follow the procedures on mentioning the autostart.

The odd thing was, I never even clicked the icon to start it... After the reinstall and reboot, an additional icon would appear if I had the NM auto-start to run on the boot of a session.

Don't sweat it too much... I'm back to Ubuntu because after trying to just make the icons go away, it just ended up creating more and more icons. I was just hoping to learn, that's all.

---

