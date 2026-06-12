---
title: "Unable to connect to CIFS host; port 9100"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by jlhughes on 2008-05-14
I have a Ubuntu Gutsy desktop with a printer attached to the USB port.

The printer is "shared" and I have samba installed.

From my laptop -- also Ubuntu Gutsy -- I can see the samba share and I can see the printer. 

When I go to print, I'm told the laptop is unable to connect to CIFS host.

When I port scan the desktop with the printer attached, I can see that port 9100 is NOT open.

I don't understand how I can see the share and create the printer on the laptop, but I can't print to the machine. 

If port 9100 is the issue, how do I open that port?

---

### Post by netztier on 2008-05-14
> **jlhughes said:**
> 
When I port scan the desktop with the printer attached, I can see that port 9100 is NOT open.


tcp/9100 (aka the "JetDirect port") is for directly printing to a network-attached printer, not for CIFS printing. I believe it's HP who started to use tcp/9100 on the "JetDirect" modules or boxes you could buy for their printers, and this goes back way into the 90ies.

CIFS printing is done via - you guessed it - CIFS on tcp/445. If a system "shares" it's printer, it does so on the SMB or CIFS ports (tcp/139 or tcp/445), maybe with CUPS (tcp/631), possibly even in the "classic" UNIX way on the LPD/LPR port tcp/515; it generally does not do this on tcp/9100.

regards

Marc

---

### Post by jlhughes on 2008-05-14
Anyone want to offer a way to troubleshoot why the laptop reports being unable to connect to the CIFS host?

As I said above, the share shows up on the laptop when I administer printers. However, when I go to print, I'm told the laptop cannot connect to the CIFS host.

---

### Post by rial_024 on 2010-10-27
i am printing to a network printer..! i can print to other printers except to LQ680 which is also a network printer. error message unable to connect to CIFS host. i tried to delete the printer and add again but the same problem occur (oh when im adding printer driver only lq570+ there is no driver for LQ680)  what should i do?.. can you help me please..

---

