---
title: "HELP! hp d1660 printer quit"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-06-13
Upgraded to 10.04 the other day and just tried to do a print with my HP Deskjet D1660. Nada! Says job has been sent but no printing occurs. Tried a test page, says sent, but nothing happens. Worked fine in 9.10. Getting a little confused with this now.

Tried uninstalling and reinstalling printer. No printing.
Tried updating, thru installation, here's what shows on 
Settins:

Description:   Hewlett-Packard reflash
Location:      (This is blank)
Device URI:     usb://HP/reflash
Make & Model:   HP Deskjet 1600c, hpcups 3.10.2
Printer State:  Processing - Processing pag 1.....

     Under Policies:
State     Enabled (ck'd)
          Accepting jobs (ck'd)  (Italics beside that Not published See 
                                   Server Settings)
          Shared (ck'd)
Access Control     Allow printing for everyone (marked)

System > Admin > Printing > Printing - localhost shows HPD1660 checked

Click Printer > View Print Queue shows 2 test pages 
Job 27 > pending (15 min ago) 
Job 26 > processing 1(17 minutes ago)

System info in signature.

Any suggestions?

---

### Post by flyfishingphil on 2010-06-13
Add on info, if anybody can figure it out.

Deleted/removed everything, disconnected printer, unplugged power cord from printer, restarted computer. 

Went to synaptics and installed: hplip, libhpmud0, hpijs, hplip-dbg, dj tools, hplip data, hplip-gui, and all of the dependents listed under those. Did a computer restart, reconnected via usb to Hp D1660 and it now shows the hp icon on the top bar Check and it shows the printer as ready to go, standing idle.

Click on document to print and a box pops up with HP Alert, big exclamation point, and shows the print being "ordered". Give it about 30 seconds and it changes color saying print job completed. Nothing has been printed. Tried again, while watching the job queue and it never appeared there but in the Status bar it shows it as having been completed.

Now, I'll add another question. How hard is it to go back to 9.10 from 10.04 without doing a format? Any directions anyone know of for doing that. Haven't found any in the forum but I may be asking/searching with wrong heading.

---

### Post by KinGnu on 2010-06-13
Hi all!

I have Ubuntu 10.04 LTS and I'm having the same problem with HP Deskjet D1660, hplip is installed, everything works, but the printer is not printing. Printer was tested in another windows computer and it works just fine! Please help!

---

### Post by joseph2221 on 2010-07-07
hey-- did ubuntu 9-10 work for this printer. tried all the threads to RESOLVED, and nothing worked-- it's been 3 days, looking and nothing!! HELP~!!!

---

### Post by flyfishingphil on 2010-07-07
> **joseph2221 said:**
> hey-- did ubuntu 9-10 work for this printer. tried all the threads to RESOLVED, and nothing worked-- it's been 3 days, looking and nothing!! HELP~!!!
joseph2221,

Don't know what I did, with everything I tried, but the printer works just fine now. If anybody can tell me how to get all of the printer operational listings I'll run that and see what it says and post it. 

As I remember I went thru and made sure everything was checked to operate, left the printer on and did a shutdown/restart on the computer. I think that was when 10.04 finally recognized the printer as being there and started printing on demand.

---

