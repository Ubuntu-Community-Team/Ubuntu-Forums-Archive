---
title: "Knetworkmanager doesn't show 'wireless network' selections"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by ceros on 2006-08-19
The only selections I see in knetworkmanager are options, help, quit, and the selections for wired devices. I do not see any other selections including the ones that I need, "Wireless Networks" and "Connect to Other Wireless Network." How can I get these to show up?

---

### Post by ceros on 2006-08-19
Well I posted too soon. The thread [here]("http://www.ubuntuforums.org/showthread.php?t=208422") helped out with this one.

In Kubuntu, on top of commenting out all lines in /etc/network/interfaces except for the lines dealing with the loopback, I also had to go into Start > System Settings > Network Settings, click each interface and select Configure Interface, and uncheck the option to 'Activate when the computer starts.' After all this, I rebooted and now I see the settings I need in knetworkmanager.

---

### Post by RayNiu on 2006-11-02
hey ceros, i have the quite same problem as you, i have finished modifying the /etc/network/interfaces as you mentioned. But i can not find Start>System Setting>Network Settings, can you tell me where to find them? by the way, i am a really rookie. Thank you for any help!

---

### Post by daller on 2007-02-08
> **RayNiu said:**
> hey ceros, i have the quite same problem as you, i have finished modifying the /etc/network/interfaces as you mentioned. But i can not find Start>System Setting>Network Settings, can you tell me where to find them? by the way, i am a really rookie. Thank you for any help!

Solved by now?

Well... anyway:

Press the "K-menu" button, click "System Settings", and find "Network Settings" in the bottom of the list!

---

