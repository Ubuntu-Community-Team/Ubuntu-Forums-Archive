---
title: "Network manager issues in hardy -- keeps prompting for wep key"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by nickwilliams1975 on 2008-11-07
Have a dell 1720 laptop that I installed ubuntu on as dual-boot with vista.

No issues at the start with getting network manager to find the wireless network and connect.

Recently, the connection has been very problematic - network manager finds the wireless network ok, but keeps prompting for the wep key.  Doesn't matter how many times it is entered, it just keeps prompting for it.

I have done some searching, but I'm not sure what to do.  I've tried clearing the list of wireless networks.  I've tried running iwconfig - which seems (to me) to show that the card is connected (displays essid and access point). 

Sometimes, the wireless manager connects straight away with no issues.  So it's not like the card isn't supported -- it has worked in the past, and works occasionally.

Is there anything else I can try?  It's essentially making Ubuntu useless for what we need, which is a reliable os to connect to the internet.

---

### Post by stanley drew on 2008-11-07
A lot of people are experiencing the same issue, including myself and my roommate. As of yet I haven't read about any solution but I think network-manager needs to be patched. Until then you can try wicd instead of network-manager, which worked for me in 8.04 but I haven't had any luck with it in 8.10.

wicd set up info is here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by nickwilliams1975 on 2008-11-08
Thanks, I wonder does wicd work for others?

---

### Post by stanley drew on 2008-11-14
I am also wondering that. Did you get it to work for you?

---

### Post by zenithdave on 2008-11-14
Wicd worked for me :D atheros wireless . Easy to install too and uninstalls the flakey network manager.

---

### Post by stanley drew on 2008-11-14
That's great. I'll warn you that I've been unable to get wicd to work in 8.10 and network-manager is even worse than before in 8.10 so beware before you upgrade.

Are you using the madwifi driver or ndiswrapper by the way?

---

### Post by mac-i-bear on 2008-11-14
i have the same issue. after installing 8.04 over vista (one way ticket no return) it worked great until some stuff got updated and rebooted... but i have no idea what are you guys talking about (old dog trying to learn new tricks) removing network manager. i had to re-plug the leash and the box connects to the internet but cannot go mobile. if i remove network manager and the leashless does not work, can i replug the leash ?

---

### Post by stanley drew on 2008-11-14
You can follow the instructions above for installing wicd but it sounds like you might have upgraded to a newer kernel and now you are having a driver incompatibility issue. Search the forums for posts about your wireless card to see if they can help.

---

### Post by mac-i-bear on 2008-11-14
how do i know which kernel do i have and with which kernels these solutions work ?

---

### Post by stanley drew on 2008-11-16
you can figure out your kernel with uname -a in a terminal

---

### Post by mac-i-bear on 2008-11-17
thank you !

---

### Post by stanley drew on 2008-11-20
So just to cap this off I did eventually get wicd to work in 64-bit intrepid. It turns out wicd wasn't detecting my wireless interface. After I added wlan0 as the wireless interface under preferences everything was fine. Using wicd fixed the inconsistent and slow connection issue for me as well. And I never get prompted for my password anymore.

---

