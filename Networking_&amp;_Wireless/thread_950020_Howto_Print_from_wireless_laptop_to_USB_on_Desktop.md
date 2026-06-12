---
title: "Howto? Print from wireless laptop to USB on Desktop"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by lawtech on 2008-10-16
Seems like this should be simple, but I've found nothing that says how to do it. (Please point me if I've missed it.)

I have a desktop running a fully current Hardy. It has an HP F300 series printer/scanner attached via USB, with hplip installed. Runs great. I have system-config-printer set up with access control showing nothing and the server set to share this printer.

I have a laptop also running a fully current Hardy. I can print a test page to the desktop's printer using CUPS. I have hplip installed--except it complains it can't find that printer. When I try to set up ipp in the system-config-printer server section, I get asked for a password for root, and I'd rather not set up a root account. Same thing if I use "other" and specify hp protocol, as in

hp:/net/Officejet_F300_series?ip=192.168.1.2

Is there a way to get printing and scanning working from the wireless laptop without setting up a root account in the desktop?

Can anyone verify that it works if one does set up a root account?

Thanks.

---

