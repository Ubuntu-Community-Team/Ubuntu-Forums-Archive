---
title: "how to update / roll back network manager in Gutsy?"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by bluepowder7 on 2007-11-27
i've got this network manager on gutsy, standard install piece, version 0.6.5

thing is, it is buggy when it comes to switching between wired and wireless connections - essentially, it doesn't switch.  only way to change is to reboot.  now, back when i had feisty, it worked fine (though i have no idea which rev it was).  how can i either grab an updated version, reinstall the existing, or install an older one (like whatever was in feisty)?  and, if i do that, will i need to reinstall my wifi driver using that ndiswrapper business?

i already submitted a bug report, but i've no idea if progress has been made by the development team, or if it's gotten cast aside as a very low priority item.

---

### Post by fraia on 2007-11-27
I'm having the same problem, my wlan wont reconnect if the signall goes down and back up again. The only way i've been able to reconnect is to reboot. 

I've tried /etc/init.d/networking restart
and ifdown wlan0, ifup wlan0
...they dont work

Im using the iw4965 driver on x64 gusty

---

