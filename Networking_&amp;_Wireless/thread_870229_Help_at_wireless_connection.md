---
title: "Help at wireless connection"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2008-07-25
I'm absolutely positive that i have no wep, wpa, or any other security things for my linksys connection. But when i try to connect to the network on linksys it tries to connect for a while but then it says it needs a security code. What do i do? Im on my windows right now, i always have low connectivity on my windows connection, does the ubuntu networking system give up after a while? I'm trying to connect just to the internet. Any suggestions?

~~Dragos240~~

Edit: Im on a sony VAIO laptop that has windows xp. I hope his is enough info.

---

### Post by funkydan2 on 2008-07-27
When you left-click on the networking icon in your system tray (top right hand corner if gnome) and you get the list of available wireless networks you should see a 'radio button' (to select the network) followed by the network's name and on the far right end a bar indicated the signal strength.

If the netork you're trying to connect to is 'protected' there will be an icon (that maybe looks like a shield) to the left of the signal strength bar.  This is a simple way to see if the network is encrypted and whether you need a password.

If Windows says you have 'low connectivity' that might mean that there's something not quite working on your router - like the way that it gives out network addresses (DHCP) isn't quite working.  Have you rebooted your router recently?

Finally, you can get some information about why the computer can't connect to the network by looking at the system log.  After trying to connect run 'dmesg' at the command prompt and if the output doesn't help you, post it here.

---

