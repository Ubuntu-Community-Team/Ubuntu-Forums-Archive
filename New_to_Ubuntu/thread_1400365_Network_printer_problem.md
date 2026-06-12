---
title: "Network printer problem"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Tholley on 2010-02-06
Ever since I switched from 9.04 to 9.10, getting something to print on my network printer has been hit and miss, and now all miss.

Before I could go to Printing and it would find my printer, but I would have to do that every time. Now it is unable to see my printer at all, even tho my daughters computer with 9.04 has no problem.

When I go to Printer, New, it searches, but comes up empty, I select Network Printers/Windows printer via Samba, click browse, and get this 

[HTML]There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration.

To do this, select System->Administration->Firewall from the main menu.[/HTML]I even removed Firestarter, and still the same...

I bet it is something simple, but is eluding me!

Any help would be great!

---

### Post by Tholley on 2010-02-06
Ok... something a little different. I rebooted, not realising I needed to, after installing Samba.

So now, it finds share - workgroup, my "server" here on this computer, but still no printer.

Any ideas?

---

### Post by Tholley on 2010-02-06
Nevermind... after that last post, I noticed my Laserjet Printer "magically" appeared under Network Printers.

I guess installing Samba and rebooting was all it needed.

I hope it stays put this time...

---

