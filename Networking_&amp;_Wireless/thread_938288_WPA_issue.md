---
title: "WPA issue"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by glynn on 2008-10-04
I have finally found that I can move away from XP with Ubuntu 8.04 with my laptop - my issue has always been with my wireless card - it would never connect (Netgear WG511T) in any version before this one using WPA - it now does with WPA authentication.  However, each time I boot up the laptop, I need to head into the network settings, remove the WPA key and re-type it.  It then establishes a perfect connection with the modem.  Any ideas or suggestions to enable the software to automatically use the WPA key when it starts up?

This is my first post so please keep it simple if possible.  It took me about a week of trying different searches to get my laptop to dual boot again when I reinstalled XP a couple of months ago and lost grub startup.  I can get there but it does take some time for me to do so.

Thanks in anticipation of success.

---

### Post by jmbargar on 2008-10-05
If you have running a dhcp server in your router/AP and your wireless card supports WPA authentication, I would use Network Manager for connecting your PC via wireless. Usually, it's installed by default in Gnome desktops. Anyway, you can install it easily using Synaptic or typing in a terminal something like this:

> sudo apt-get install network-manager-gnome

This tool is very intuitive to use. Otherwise, you can find a lot of information about it searching by Google. Here is the project page:

[http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")

Good luck!

---

### Post by glynn on 2008-10-05
Thanks for your suggestion.

Is Network Manager the same as the System-> Administration-> Network option? I looked at my system through Applications-> Add/Remove-> Search and it said that "network management framework (GNOME frontend)" was installed.

If not, how can I find it on my system?

My problem is that it does not remember my WPA password and needs to be reinserted each time I log into Ubuntu.  Once I do this it works well.

---

### Post by jmbargar on 2008-10-06
No. Network Manager must appear at the top of the screen and next to the clock, where the image describe:

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

If you have configured your wireless network using the System -> Administration -> Network frontend, you must disable the wireless interface in this tool for using Network Manager. I have my wireless network configured in this way using a WPA2/AES encryption and I have no problem with it.

Good luck!

---

### Post by glynn on 2008-10-06
I must have the wrong software installed.  When I click the computer icon at the top of my screen I do not get the same options that you posted.  I have attached a screen image of both my desktop and the network screen.  I also cannot see a way to disable the System-> Administration-> Network settings.  When I disable the network option at the top of the screen, it seems to have no impact on my wireless network connectivity.

My wireless works perfectly, except that I have to remove the WPA authentication key and re-enter it each time I start the laptop.

The PCMCIA card is a Netgear WG511T

---

### Post by jmbargar on 2008-10-06
If you have installed Network Manager, the applet I showed must appear in the Gnome panel typing something like this:

> sudo nm-applet

If it works, just put it in the System -> Preferences -> Sessions -> Startup programs for running this tools when Gnome boots up. Type the next command in the corresponding field:

> nm-applet --sm-disable

To use Network Manager, you have to check "enable roaming mode" in your wireless interface that you can find in the System -> Administration -> Network frontend.

Good luck!

---

### Post by glynn on 2008-10-07
Thanks for your help - it seems to be working - the secret was to make sure that I checked "enable roaming mode" in my wireless interface. Once I did this I was able to click on the "computers" next to the sound & clock icons and put in the details - it automatically found my wireless network and reconnected after I shut down and restarted!

Once I have worked through the issue - and it is not as easy a task as in the other major OS - Ubuntu works very well.  When these little inconsistencies such as the "simple" one that has afflicted me have been ironed out, then it will be an OS that I can recommend to my acquaintances without fear of being on call 24/7 for them when issues do arise.

I will keep using it and hope that it does become even more user friendly and intuitive (not that W*****s is intuitive).  Meanwhile I will only improve my skills with the command line and how the OS works.

Thanks again!!

---

### Post by jmbargar on 2008-10-07
Congratulations! It's good to know you have achieved to solve your problem. Good luck in your learning process. I suggest you have a quick look at this website:

[http://commandliners.com/]("http://commandliners.com/")

It would help you to learn some tricks about the command line interface.

---

