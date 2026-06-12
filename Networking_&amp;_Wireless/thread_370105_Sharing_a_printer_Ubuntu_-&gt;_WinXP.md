---
title: "Sharing a printer: Ubuntu -&gt; WinXP"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by cb03BoilerUp on 2007-02-25
Been trying to share an HP Officejet 5610 on my Ubuntu 6.06 LTS with a Windows XP laptop connected via wireless router.  I'm not sure I'm even starting right, I've seen so many different suggestions on how it should be done.

I've tried this command:
sudo /usr/share/cups/enable_sharing 1
But get:
Error: cannot modify custom configuration

And I've tried to modify cupsd.conf but it said I don't have permission.

This is probably a issue of my limited level of experience more than anything, but any suggestions are greatly appreciated.

---

### Post by chili555 on 2007-02-25
See post number 2 here: [http://www.ubuntuforums.org/showthread.php?t=356436](http://www.ubuntuforums.org/showthread.php?t=356436)

I hope this will be helpful. Post back if you get stuck.

---

### Post by cb03BoilerUp on 2007-02-25
Very helpful.  If I used the name and not the IP address, I can map to the Ubuntu printer.  But now, the printer status on the WinXP laptop states: 'Access Denied, Unable to Connect..'  I am positive that this is due to permissions set in cupsd.conf.

Which leads me to my next issue:  How do I grant myself permission to edit the cupsd.conf file.  I am logged in as the admin, but seem to be unable to edit this file.  I did just update from 5.10 a few days ago because I thought it was part of my print sharing problem.  Would that have anything to do with this?  Do you have any suggestions in changing my own permissions?


Thanks for the help.

---

### Post by chili555 on 2007-02-25
Open a terminal and type: sudo i hereby give myself permission to do everything especially turn back time. No, just kidding! That's a little too dangerous for noobs.

I am surprised you cannot sudo gedit <anyfile_anywhere>.

When I wrote the post I referred you to, I never had to fool with CUPS configuration. Did you go to System -> Administration -> Printing and drop down Global Settings and check Share Printers? I would be interested if that helps.

---

### Post by cb03BoilerUp on 2007-02-25
I don't even have that as an option..

---

### Post by sadjack on 2007-02-25
I followed the directions in the attached link and its worked perfectly for me on Dapper and Edgy

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by cb03BoilerUp on 2007-02-25
sadjack, this looks promising.  Trying now.

---

### Post by cb03BoilerUp on 2007-02-25
Farther along than I was before.  I can get it to spool to the Ununtu box, and shows up in the printer que, but it will not print.  Doing some troubleshooting..

---

### Post by sadjack on 2007-02-25
I recently had that problem. I tracked it down to DHCP and losing dns setting. Once I gave everything a static IP and disabled dhcp it worked fine.

---

### Post by cb03BoilerUp on 2007-02-25
Good to go!  I think it was a combinatiion of a couple items.  I reinstalled the printer on the Ubuntu box, as I found that I could no longer print from it either.  Then reinstalled the printer on the XP machine and used the generic MS Publisher Imagesetter driver.  Working like I wanted it to.

Thanks a ton sadjack and chili555!

---

