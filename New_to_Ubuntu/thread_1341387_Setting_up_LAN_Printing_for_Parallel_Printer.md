---
title: "Setting up LAN Printing for Parallel Printer"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by held7over on 2009-11-29
All my computers are Ubuntu 9.10 Gnome.

I have an old hpdeskjet 940c parallel printer connected to my personal desktop's parallel port. My desktop computer is connected to a D-Link router and there are 3 other computers connected to the same Router.

What is the easiest way to make my hpdeskjet 940c printer available to accept printing jobs from my other three computers and still leave it connected to my personal Desktop?

I have set the System/Administration/Printer application to broadcast and told my firewall to allow their IP addresses and port 9100, but scanning for a printer from any of these other computers using System/Administration/Printer application finds nothing no matter how I fiddle with it. Is there a simple set of instructions to enable this ability somewhere?

Thanks! ;)

---

### Post by plucky on 2009-11-29
You need to **publish** the printer.

**System > Administration > Printer ** and then select **Server > Settings** and tick the box that says "Publish shared printers connected to this system".

Good Luck

---

### Post by held7over on 2009-11-29
Thanks plucky, but I have already enabled publish the "shared" printer. (I am assuming by enabling this box, it makes the printer a shared printer, and nothing else needs to be done to achieve that other than allowing the other computer's IP's in the firewall policy.)

Maybe I am doing something wrong on trying to "find" the printer from the other computers? As scanning for the printer...nothing is found.

It also offers me 4 different choices such as Samba, etc., to try to use, but I am not sure which one of those to attempt to use either...

---

### Post by plucky on 2009-11-29
> **held7over said:**
> Thanks plucky, but I have already enabled publish the "shared" printer. (I am assuming by enabling this box, it makes the printer a shared printer, and nothing else needs to be done to achieve that other than allowing the other computer's IP's in the firewall policy.)

Maybe I am doing something wrong on trying to "find" the printer from the other computers? As scanning for the printer...nothing is found.

It also offers me 4 different choices such as Samba, etc., to try to use, but I am not sure which one of those to attempt to use either...

What operating systems are on the other computers?

All I did was ticked the box to share the printer,and on the other computer ticked the box to "show printers shared by other systems" and it then found the printer.I then had to install the drivers for the printer.

My printer is connected by USB cable,but I don't think it being a parallel connection should make any difference.

You should also install the drivers for the printer on the remote systems,or hplip in your case.

Good Luck

---

### Post by held7over on 2009-11-29
All computers are Ubuntu 9.10 right now.

And yes, I too have "show printers shared by other systems" ticked on the other computer I am scanning from.

So, when it found the printer, you didn't have to pick a connection method.....all you had to do was install the drivers?

Do you think my Router could be getting in the way?

---

### Post by held7over on 2009-11-30
Here is what the problem solving wizard had to say:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.0.100', 'remote_server_name': 'ispy'}
Page 5 (Check network server sanity):
{'remote_server_name_resolves': False, 'remote_server_try_connect': 'ispy'}
Page 6 (Locale issues):

---

