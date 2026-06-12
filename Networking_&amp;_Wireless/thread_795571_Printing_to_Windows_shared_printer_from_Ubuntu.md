---
title: "Printing to Windows shared printer from Ubuntu"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2008-05-15
I have search the forum for a while and could not find a definate answer to my question.
My coworker and I share a printer that is connected to his Windows XP box. I finally had enough of the wacky things windows was doing to me so I had a Ubuntu Box I had been working on for some time and decided to make that my workstation. I am trying to connect to the printer on his computer. We are in a W2K3 domain, JFYI. When I go to System--> Administration-->Printing, click on new printer, Windows printer via SAMBA, Browse, I can see his computer but not the printer.

Is there something that we need to do on the XP side?

Thanx in advance!

---

### Post by bill516 on 2008-05-15
Hmmm, I just got done wrestling with this very same little bear on my home network, admittedly a simpler environment than yours might be.

Two things to check:

Make certain that on the XP side the printer has been marked for sharing.  If it has not you will not see it.

If the windows firewall on the XP machine(or some other for that matter) is on, turn it off briefly for testing purposes.

I doubt this last is the culprit, partly because Windows firewall should allow sharing and partly because you can see the XP machine.

But worth a check, perhaps.

---

### Post by lsutiger on 2008-05-16
Firewall is not on. Printer is definitely shared. 

Not much information about this subject out there.

---

### Post by avtolle on 2008-05-16
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter) worked for me. Hope this helps you.

---

### Post by cb951303 on 2008-05-16
BTW there has been some bug in accessing windows computers in 8.04
unfortunately using winxp computer name to access shared folders and printers does not work. in printer configuration try something like this 

```
 smb://XXX.XXX.XXX.XXX/printer_name 
```

where XXX.XXX.XXX.XXX is the local IP address of the windows machine, it worked for me

---

### Post by lsutiger on 2008-05-16
Thanx for the input, but no dice on using the IP.

I did a lil troubleshooting. The computers that are logged on to the domain are the ones where I can not see the printer.
Anybody have a solution for this?

---

### Post by cb951303 on 2008-05-17
that may not be related but did you try adding yourself to the "sambashare" group?

---

### Post by lsutiger on 2008-05-20
Thanx for the advice. Now it has gotten worse!

I added myself to the samba group. Now when I go to Printers-->New Printer, Select Windows printer via Samba, I see the domain, but now it shows only my computer on the domain.
Wow!

---

### Post by cb951303 on 2008-05-21
> **lsutiger said:**
> Thanx for the advice. Now it has gotten worse!

I added myself to the samba group. Now when I go to Printers-->New Printer, Select Windows printer via Samba, I see the domain, but now it shows only my computer on the domain.
Wow!

as I said earlier don't try to connect via domains but try IP addresses instead

---

### Post by lsutiger on 2008-05-21
Thanx, but IP doesn't work either. Attached is the screenshot of the printer config. The name of the printer is exactly as it is on that computer.

---

### Post by Mudre on 2008-05-21
I kind of have the same problem. I'm a newbie on linux (not on computers in general), and just installed Hardy Heron on my workstation.

Shared printer on XP-box on LAN. 
I have Samba up and running ok i think. Can connect to the network, see other Windows comps and access their shared folders no problem.
Trying to add printer from the System-> Administration -> Printing menu, select New Printer -> Windows printer via SAMBA, browse, it finds the XP-box, and it finds the printer too, no problem.
Except it does_not_print..! Printer is a Canon multifunction MF5700 series, which is supposedly unsupported under Linux. Have tried the first 10 other drivers, but absolutely nothing happens. The printer is shared ok (others can access it from win-boxes), no firewall blocking, Bidirectional Talk turned off. Using IP-address instead of //Domain/Computername/ doesn't help.

Any ideas??

---

### Post by lsutiger on 2008-05-22
OK..I can now print a test page. But no other application can I print from!
Now this is freaky-deaky....What should I do?

While doing stuff today, I went back and tried to print something from Gedit. In the print dialog box this was listed under status:
/usr/lib/cups/backend/smb failed

Another clue on what may fix the problem?

---

### Post by cb951303 on 2008-05-23
> **lsutiger said:**
> Thanx, but IP doesn't work either. Attached is the screenshot of the printer config. The name of the printer is exactly as it is on that computer.

can you try with "smb://" instead of "smb:///"

---

### Post by lsutiger on 2008-05-29
Since we are in a domain, I tried smb://<domain>/i.p.a.dress/<name of printer>

Works like a charm. Thanx for all of your posts!

Hey Mudre, any luck?

---

### Post by lsutiger on 2008-05-30
AARRGGHH!!!
I was trying to ge the pdf file generator working (cups-pdf). I followed the advice [from this thred]("http://ubuntuforums.org/showthread.php?t=801187&page=2"). After that, I was no longer able to print to the windows shared printer. The previous post instructed to completely remove cups-pdf and ghostscript, the reinstall in the reverse order. I did notice that when I removed ghostscript, there were a lot more packages removed than what was reinstalled.

Any clues?

---

### Post by lsutiger on 2008-06-01
??

---

### Post by lsutiger on 2008-06-03
After a large update I did today, I am able to print a test page again, but can not print from any application....again!

Any clues??

---

### Post by LaneLester on 2008-06-08
> **cb951303 said:**
> BTW there has been some bug in accessing windows computers in 8.04
unfortunately using winxp computer name to access shared folders and printers does not work. in printer configuration try something like this 

```
 smb://XXX.XXX.XXX.XXX/printer_name 
```

where XXX.XXX.XXX.XXX is the local IP address of the windows machine, it worked for me

That just worked for me in connecting Xubuntu 8.04 to a printer on a Vista machine. I did not have to add myself to sambausers.

I prefer to set up printers with Firefox pointed to [http://localhost:631/](http://localhost:631/)

Lane

---

