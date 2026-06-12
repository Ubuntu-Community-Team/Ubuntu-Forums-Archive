---
title: "How do I print wirlessly with my printer connected to my router via usb"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by matt39 on 2013-10-02
Hi I'm completely new to this, so please forgive me if something like this has been posted before. I have a CANON Pixma iP1000 that is connected to a router via usb. I initially set all this up in windows, so I could print from my laptop without being in the same room as the printer. I'm kinda hoping I can do the same in Ubuntu, so I can move away from windows and transition into Linux. I done some digging around the internet and managed to get the drivers installed (I had to convert the rpm packages into deb using alien) and I got samba and cups installed and running. I seem to be able to find my printer with the ip address, but when I get to 'Queue' and 'Connections' I don't know what to put in? I tried a few things, but must admit I'm stumped on this one. If anyone can help I would really appreciate it.
Thanks

---

### Post by chili555 on 2013-10-02
I think you want something like this. Of course, substitute the actual IP address on your system. A few printers have a bit of trouble with the ipp protocol; mine for example. If so, you might try ipp[COLOR="#FF0000"]14[/COLOR]://192.168...etc.

---

### Post by matt39 on 2013-10-02
Hi Tarballs R Us, thanks for your quick response. I tried your suggestion and when I print a test page, it goes through the motions, but nothing prints out. If I add ipp14://192.168.1.. I get Held in the status of the print queue window. I don't know, but it seems like I'm missing something?
Is there someway of having TCP/IP in Ubuntu?

---

### Post by chili555 on 2013-10-02
May I assume you went to administration pages of the router and confirmed the correct IP address for the printer on the network. Also, after you added the URI, did you follow the guided process to find the drivers automagically? Are there any clues after you print a test page if you check the print queue?

TCP/IP is present and in use on every Linux system.

---

