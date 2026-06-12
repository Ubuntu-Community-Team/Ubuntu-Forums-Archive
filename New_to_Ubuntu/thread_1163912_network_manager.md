---
title: "network manager"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by pramodmmuraly on 2009-05-19
i ve installed jaunty on my laptop nd is workin fine.i m using ubuntu in my office network(wired).jaunty is takin ip automatically very well,but i need to use static ip for my uses.for that i ve configure new static ip through GUI.when selecting that internet is working fine. i ve given my IP,netmask and gateway details in /etc/network/interfaces and nameserver in /etc/resolv.conf,every thing is goin smoothly.but when i restarted my system my network applet is not showing ny wired network,nd respective fields are not highlited. i dont know y.then i ve removed all my /etc/network/interface entries and restarted its fine nd applet is taking auto IP and respective fields are highlited.

ny one ve ny idea on this issue.nd how can i enter my static IP details in jaunty.i dont know. i ve this static IP issue in ibex too.is this a non curable bug or something.

ny help is appreciated

---

### Post by alphacrucis2 on 2009-05-19
> **pramodmmuraly said:**
> i ve installed jaunty on my laptop nd is workin fine.i m using ubuntu in my office network(wired).jaunty is takin ip automatically very well,but i need to use static ip for my uses.for that i ve configure new static ip through GUI.when selecting that internet is working fine. i ve given my IP,netmask and gateway details in /etc/network/interfaces and nameserver in /etc/resolv.conf,every thing is goin smoothly.but when i restarted my system my network applet is not showing ny wired network,nd respective fields are not highlited. i dont know y.then i ve removed all my /etc/network/interface entries and restarted its fine nd applet is taking auto IP and respective fields are highlited.

ny one ve ny idea on this issue.nd how can i enter my static IP details in jaunty.i dont know. i ve this static IP issue in ibex too.is this a non curable bug or something.

ny help is appreciated

I have set static address through network manager. I have dhcp for wireless and static for wired. When you right click NM and select Edit Connections then select the Wired tab. Do you see auto eth0? If the wired tab is empty, you could try manually adding it in there. Otherwise select auto eth0 and click edit. It will ask for the admin password. You enter everything in NM, address, subnet mask, default gateway and the DNS servers.

---

### Post by porchrat on 2009-05-19
If you can't get it to function (I personally don't use network manager as I do find it a little buggy) then you could always try wicd as an alternative to network manager.

Obviously that is a last resort as there are more people here using network manager than wicd so help is easier to come by.

---

