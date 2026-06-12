---
title: "Ubuntu drive me CRAZY!!!"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by MacPC on 2006-12-09
AAAAAAAAAAArgh!!!!!!!!!!!!    

I posted this on the other forum then I realised I was in the wrong. Hope no one mind I post it here again.

Awhile ago, I spent quite a bit of time to set up the Ubuntu network. It was working perfectly, my Macs and Windows could browse the Ubuntu and the Ubuntu can do the same. Since then I havn't been using it, I turn on the Ubuntu machine today, the Macs and the Windows can no longer see the Ubuntu machine anymore, but the Ubuntu machine can still browse the Macs and the Windows without a problem, what's going on???

The printer sharing is fine, Ubuntu can print to any of the printers on the Mac and Windows and they can VNC each other, so it's not a problem with the LAN. 

The Macs are using OS X tiger 10.4.8 and the Windows are Win2k pro SP4 and Win XP SP2. Ubuntu is 6.06.

Any help will be appreciated.

MacPC.

---

### Post by TheWizzard on 2006-12-09
mmm, a bit more information would be nice. nevertheless, my first guess would be something with your router or a different ip address. please give us the output of ifconfig (ubuntu) and the content of the host files (mac & windows).

---

### Post by Malakia on 2006-12-09
Are they all setup with static ip addresses or is it setup through a DHCP server with a dynamic IP address.

---

### Post by FrodoB on 2006-12-09
This is likely a browse master issue. Ubuntu/Samba probably became the browse master and when you rebooted the other machines got out of sync with the master.

I cannot remember the exact commands, but go to the Windows machines and open a Command prompt and then use net view to see the Ubuntu machine by it's IP address:

net view \\192.168.0.10

assuming it this case that the Ubuntu machines is at 192.168.0.10.

Do this on all of the Windows machines if necessary. Afterwards you can likely browse by name again.

Find out how to disable Samba being a browser master in the smb.conf file.

---

