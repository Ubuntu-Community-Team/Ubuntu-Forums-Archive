---
title: "Can't print on HP DJ F4180 from Ubuntu to XP"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by taz205 on 2008-02-18
When I try to print to a printer on an XP box from my Ubuntu 7,10 laptop, it doesn't print.

I have an HP DeskJest F4180 (printer/scanner/copier) connected to an XP Pro box (NetBIOS name "CHEWBACCA" in workgroup "WORKGROUP") and shared as "DJF4100," and I have Ubuntu 7.10 on my laptop. I added System > Administration > Printing > New Printer > Windows Printer via SAMBA, using the following URI "workgroup/chewbacca/DJF4100" and proper credentials for the XP box (I even created an XP user with the same name as the account logged in on the ubuntu laptop). "Verify" button returns "This print share is accessible." For the driver, I manually select HP > DeskJet F4100 > "HP DeskJet F4100 Foomatic/hpijs (recommended)" (and later "HPLIP 2.7.7.dfsg.1").

Printing from the ubuntu laptop sends a job to the XP box which I can see in the printer status as "Remote Downlevel Document" (this name shows up for everything I try to print from the laptop). The job status changes to Printing and the printer makes some noise as it would if it were about to print something, and then it just stops--nothing happens. The "Size" indicates that 64.0KB/1.41MB (no matter what the size job is, it doesn't seem to get passed 64.0KB on any of them) is processed (or whatever), and after a while the status changes to Error - Printing. I've tried tweaking CUPS settings through the GUI in ubuntu (localhost:631 doesn't show any additional options that aren't available through the GUI--at least not that I could see).

I can print from the XP box directly without any problem at all. If I try to delete the job from the ubuntu box, the status changes to "Deleting" but doesn't remove the job unless I kill the spoolsv.exe process and then restart it.

Any ideas? I'm totally at a loss.

---

### Post by coggz on 2008-03-08
I have this exact same problem with a DeskJet 2180, it sends 64kb and sticks. I believe it is something to do with the fact that hpijs does not do samba shares. Please email me if you get a solution: i[dot]am[dot]luke08[at]gmail[dot]com

---

### Post by Lichoy on 2008-03-29
O_o
I have EXACTLY the same problem with my HP deskjet 3325. It is connected thru winXP network and all the other users that have winXP can print to it with no problems, however when printing from Ubuntu using HPLIP driver it gets stuck somwhere between 32kb to 64kb.
HHHHHHHHHEEEEEEEEEELLLLLLLLLLLPPPPPP!!

---

### Post by toupeiro on 2008-04-24
Make sure bidirectional support is turned **off** in the windows printer settings. Clear the printer queue, and resubmit the print jobs. Your jobs should take right off after that.

---

