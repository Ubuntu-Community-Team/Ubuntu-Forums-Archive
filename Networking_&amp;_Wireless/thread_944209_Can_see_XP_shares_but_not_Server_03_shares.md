---
title: "Can see XP shares but not Server 03 shares"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by kayamon on 2008-10-11
Hello and Thank You for any help.

I'm running Ubunutu in VMware on a fresh installed xp box(vmxp). The vmxp machine sees the network, and a 2003 server with shares no problem. Ubunutu vmware machine sees the network, machine names on the network and can access this xp workstation shares, however when browsing the 03 server no shares become visible, blank browser. I've run a few different vmware ubuntu images to see if it was a particular configuration but 3 out of 3 do the same thing, what am I missing. Advice?

Many Thanks
Kayamon

---

### Post by superprash2003 on 2008-10-11
is the ubuntu able to ping the 03 server??

---

### Post by kayamon on 2008-10-11
Hi Super...

Thanks for the reply. 
Yes, I can ping the SRV03 server. I can also see the shares listed using 'smbtree', but can't see them in the browser. I've modified my dns 'resolv.conf' file to add the host record of the SRV03 and so the ubuntu system can see the server no problem but simply cannot see the SRV03 shares. It will browse the XP box shares just fine. What's up, all 3 images are doing the same thing with the SRV03 box. I know it's configuration but don't know what?

Thanks Again
Kmon..

---

### Post by superprash2003 on 2008-10-13
try connecting like this [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html) .. remember replace x.x.x.x with the ip of the 03 server..

---

