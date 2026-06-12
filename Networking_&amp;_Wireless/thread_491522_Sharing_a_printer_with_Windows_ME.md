---
title: "Sharing a printer with Windows ME"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by sab0403 on 2007-07-03
I have a printer connected to my Ubuntu box. The configuration there is correct since I can print remotely from another Ubuntu box; however, I cannot seem to connect to it from the Windows one. That's Windows Millenium. Every single pointer I find on the net talks about WinXP, but I try to follow the same instructions and nothing happens. The printer simply appears as disconnected (offline). 

The route I'm using for the printer in Windows is ```
http://mycomputername:631/printers/myprinter
```. Do I need anything else?

The version of Ubuntu I'm using is Feisty, on both boxes.

---

### Post by coldstatue on 2007-07-04
Have you tried file sharing just to be sure the network really is working?

---

### Post by sab0403 on 2007-07-05
Yes.

Both file sharing (NFS) and printer sharing (CUPS) work with my *other* Ubuntu box (a laptop), through the same network.

Thanks for the reply.

---

### Post by coldstatue on 2007-07-06
But to be sure the windows box is working with your network... I may be wrong here, but I think that you need to use samba to share files OR printers between win/linux. I don't use Win anymore, so i can't remember. Look into that. You should be able to set it up within an hour. if your file sharing works, the printer should work. I am pretty new to linux (It's been my only OS for 2 months, and I've been using it since Nov), so hopefully someone else will respond here. From what i remember, I had to have samba working to share the printer.

If you search the forums for samba, and how to, you will find lots of info. File sharing is good to have anyway, so you could set that up, then try the printer.

That's the best i can offer.

Anyone else?

---

