---
title: "HP Printer deected but doesn't print"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-23
Have an HP D1600 installed and it is detected but doesn't print Ran lsusb and get these results:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 03f0:7f11 Hewlett-Packard 
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Had it installed in VBox also but deleted it from there. Send it a print. like print test page and it goes thru the steps but then, checking thru System>Admin>Printing>Printer under "Printer state" it states "Idle - ready to print" but never prints.

Am I missing something in here in steps to getting it to print?

Have uninstalled, restarted, reinstalled but cannot get it to print. Any ideas?

Thanks for the assist.

---

### Post by WinterRain on 2010-05-23
If it is a newer printer, you may need to install HPLIP. You can get the latest from hp.com

---

### Post by flyfishingphil on 2010-05-23
> **WinterRain said:**
> If it is a newer printer, you may need to install HPLIP. You can get the latest from hp.com
Just went in and did the sudo apt-get install hplip-gui and reinstalled the printer. Still doesn't do the print.

I have the hplip 3.10.5 run on the desktop but when I click on it I get a pop up box that reads"

[I]Could not open the file /home/flyfishingphil/Desktop/hplip-3.10.5.run.  
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.[/I] 
For character encoding it is set for "automatically Detected"

How do I open and install this?

---

### Post by warfacegod on 2010-05-23
System> Admin.> Printing> right click your printer's icon> put a check next to "Enabled"

---

### Post by flyfishingphil on 2010-05-23
> **warfacegod said:**
> System> Admin.> Printing> right click your printer's icon> put a check next to "Enabled"
Enabled is done. Managed to get the hplip 3.10.5 installed and got the printer to print but now there is another problem/question.

It no longer offers the ability to do 2-sided printing. Can't find that option anywhere. Anybody have any suggestions on how to get that back? (Do quite a bit of multi-page printing and rreally need the 2-sided option)

---

### Post by warfacegod on 2010-05-23
System> Admin.> Printing> right click your printer's icon> select Properties> Printer Options> Double-sided printing

---

### Post by flyfishingphil on 2010-05-23
> **warfacegod said:**
> System> Admin.> Printing> right click your printer's icon> select Properties> Printer Options> Double-sided printing
That option is not offered. System>Admin>Printing shows printer. Right click on printer and click on properties>

Left column offers Settings, Policies, Access Control, Printer Options, Job Options, In/Toner Levels.  

Click on Printer Options > Under General it offers: Media Size, Media Source, Media Type and Print Quality.

No option offered anywhere for 2 (double) sided printing. Could this be a problem with the newest version of hpcups 3.10.5? Do I need to get in and uninstall everything related to the printer, and the printer, and start over? If so, any easy steps to follow?

---

### Post by warfacegod on 2010-05-23
My hplip 3.9.8 driver in 9.10 gives me the option. I've never had a problem with my 7660 printer so I have no reason to believe that double sided printing doesn't work even though I've never used that option.

Try:

```
sudo apt-get install hplip-cups
```

---

### Post by flyfishingphil on 2010-05-23
> **warfacegod said:**
> My hplip 3.9.8 driver in 9.10 gives me the option. I've never had a problem with my 7660 printer so I have no reason to believe that double sided printing doesn't work even though I've never used that option.

Try:

```
sudo apt-get install hplip-cups
```
Nope, that didn't do it either. 

Any way to install from the cd? It's marked Win XP, Vista, 7 & Mac OS v10.4 & 10.5. Maybe open the files and see what's available and "plug it in" from there?

---

### Post by warfacegod on 2010-05-23
The Mac driver *might* work but I seriously doubt it. I'd dump your driver and get the hplip 3.9.8. driver from Synaptic.

---

### Post by flyfishingphil on 2010-05-23
> **warfacegod said:**
> The Mac driver *might* work but I seriously doubt it. I'd dump your driver and get the hplip 3.9.8. driver from Synaptic.
OK, went back and deleted the printer, uninstalled all of the hplip "stuff" reinstalled the hplip "stuff (hplip, hplip-gui, lphpmud0, hplip-cups, hpijs, hplip-data, hpijs-data. some were dependents appartently) All 3.10.02. Didn't see anything with 3.9.8.

Reinstalled printer, it shows it as being there, offered dual option & ok'd that, sent material for printing. Nothing happens. Checked queue and nothing shows.

Now what?

---

### Post by warfacegod on 2010-05-23
Did you remember to re-enable it?

---

### Post by flyfishingphil on 2010-05-23
> **warfacegod said:**
> Did you remember to re-enable it?
It's enabled and shared. Everything is there, I think. When I send a print job it flashes a sending screen but nothing shows in the queue and the printer is silent.

EDIT ADD-IN:

Don't know what I did but I now have the hp icon on the top bar, next to the wi-fi signal icon. Double click on the icon (or single click right to open the choices) and I get HP Device Manager. Under Action page go to Cups-View Printer and Device Info. Click on that and you get a box with four tabs labeled: Model Data (Static), Status Data (Dynamic), Status History and Deskjet_D1600. Click on the D1600 tab and go to line 20 and it reads:printer-make-and-model HP Deskjet D1600 series, hpcups 3.10.5

Apparently it is still using that latest download in there. I thought I had removed that but it appears I didn't. How would I get the 3.10.5 out of there and get back to 3.10.2? 

If I  go System > Admin > Printing > it brings up the "printing localhost" with two hp icons. One has the green check mark the other has a heart icon on it. 

When I right click on the heart icon model and click on properties it shows the make and model as HP Deskjet d1600 Series hpijs, 3.10.2rc1.9. Under printer options this one offers the dual (two sided) option. 

When I right click on the green checkmark and properties it shows the make and model HP Deskjet d1600 Series, hpcups 3.10.5. When I check on the printer options it does not offer the dual (two sided) printing option.

I'll delete the green checked one and see if I still get a print and add in the results.

---

### Post by warfacegod on 2010-05-23
Try rebooting.

If you mean downgrading, its theoretically possible but in reality you'll break your system. You'll need to do a fresh install if you want 9.10 back. I suggest having separate /home folder if you go that route. Makes life so much easier.

---

### Post by flyfishingphil on 2010-05-23
> **warfacegod said:**
> Try rebooting.

If you mean downgrading, its theoretically possible but in reality you'll break your system. You'll need to do a fresh install if you want 9.10 back. I suggest having separate /home folder if you go that route. Makes life so much easier.
Thanks Warfacegod. I'm about to give up and go back to Vista. This is enough to drive a sane man crazy, and a crazy one to suicide. Fortunately I'm still trying to recover from an earlier error when I formatted the entire drive. Maybe I'll just do a reinstall of 10.04 and proceed with caution.

Thanks for the assists.

---

### Post by warfacegod on 2010-05-24
Sure thing.

---

### Post by flyfishingphil on 2010-05-24
> **warfacegod said:**
> Sure thing.
Problem solved! Re-installed the 9.10, did the updates, hooked up the HP D-1600 printer and the Logitech headset/microphone and everything worked as soon as connected. Guess I'll give 10.04 a little longer for tuneups before I try it again.

Thanks again warfacegod for the assists in trying to get everything to work in 10.04.

---

### Post by warfacegod on 2010-05-24
> **flyfishingphil said:**
> Problem solved! Re-installed the 9.10, did the updates, hooked up the HP D-1600 printer and the Logitech headset/microphone and everything worked as soon as connected. Guess I'll give 10.04 a little longer for tuneups before I try it again.

Thanks again warfacegod for the assists in trying to get everything to work in 10.04.

Again, sure thing. I remember switching from Jaunty to Karmic. I didn't have any major issues but I wasn't very comfortable with it. I thought it was a step backward and still think so but I've grown rather fond of it.

With 10.04, the feeling was the same but magnified one hundred fold. Changing an OS, simply for the sake of changing something, is stupid. Nearly everything about using and modifying 10.04 absolutely infuriates me and it's very buggy. It sometimes feels like doing 100 mph on the highway with half your lugnuts and motor mounts loosened a little, you don't know if it's going to fly apart at the seems. I hate it nearly as much as I hate Vista.

Anyway, sorry for the rant and I'm glad you got your printer working.

---

