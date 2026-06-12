---
title: "Problem with DHCP and wireless in Hardy"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by guildofghostwriters on 2008-05-10
My rt73 usb dongle has been working fine in Hardy with rutilt (apart from being unable to remember profiles unless I run it from terminal as root) and the serialmonkey drivers but lately it's been acting strangely. Sometimes it just fails to connect to the router. There's a windows pc upstairs connecting to the same router (with the same brand dongle - and I've tried swapping them over to make sure) so I'm pretty sure it's not the dongle or router. Today I watched the terminal output to see what was happening and (forgive my ignorance here - I'm not well versed in the 21st century) it looked like it was making repeated attempts to connect to xx.xx.xx.2 and when that didn't work it said something along the lines of 'no leases - sleeping' and that was that, no connection. The thing is, the windows pc was already using xx.xx.xx.2. Shouldn't it then attempt to connect to an available ip? I switched off the windows pc, rebooted the hardy pc and the router, and now rutilt has connected to xx.xx.xx.2.

The weird thing is, all this seems to have started since I was reading about setting up Samba. The Samba guide said I would need a fixed ip and I looked in rutilt and network-admin to see what I'd have to do but I'm sure I didn't change any settings. Maybe that's just coincidence but it seems odd.

Anyway, grateful for any help offered - even if it's just an alternative to rutilt and network-manager.

Ta

ps I posted a similar request in the thread I followed to get it working in the first place but nobody replied (it's in the archives) so apologies for posting the same thing twice.

---

### Post by guildofghostwriters on 2008-05-10
Please help!! In the absence of replies I tried network manager again and also apt-get --purge remove rutilt and reinstalling it but it just won't connect at all now.

---

### Post by ozelot on 2008-06-17
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=763801&highlight=network-manager+alternative[/COLOR]]("http://ubuntuforums.org/showthread.php?t=763801&highlight=network-manager+alternative")
Its called wicd. enjoy! If you dont like it, write different config files and copy them back and forth
using scripts to switch between different netw. modes.
My post could help you:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=5197358#post5197358[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5197358#post5197358")

---

