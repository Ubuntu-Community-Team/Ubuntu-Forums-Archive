---
title: "Printer no longer works"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by jfbooth on 2011-02-03
Xubuntu 10.10.  Brother mfc7440n multifunction printer.  Used to work great.  Quit printing.  Scans just fine.

Xubuntu machine ethernet connected to router.  Printer ethernet connected to router.  One notebook running Windows in front of house .. WIFI connected to router.  That notebook prints and scans fine.

I have messed with the system trying to get it to print again .. so not sure how it was set up before I 'messed' with it.

APPLICATIONS/SYSTEM/PRINTING  opens window titled PRINTING - localhost
There is an printer icon titled Brother-MFC-7440N.  It has a green check mark on it and two vertical blue bars.  The bottom of that window says "Connected to localhost'.  Double click icon.

Window opens titled 'Printer Properties - Brother-MFC-7440N' on localhost

SETTINGS:
Device URI: lpd://BRN0080770794D4/BINARY_P1
Other items look OK except PRINTER STATE:  Stopped - Unable to locate printer 'BRN0080770794D4'!

POLICIES:
STATE:   Enabled is NOT checked.  Accepting Jobs is checked.  Shared is not checked.

Any help greatly appreciated.  Thank you in advance.

---

### Post by ghostborg on 2011-02-03
I had an HP printer that stopped printing from Ubuntu but Windows was ok, for me the IP address on the printer was set to auto which next time I had a power failure the printer got assigned a different IP address.
Ubuntu Printer Properties and then under Settings is Device URL and I could see that the IP was different than the printer's IP. I edited it to match and it worked. I then set the printer to manual IP instead of auto. Have not powered the printer down yet to see what would happen. 
If it is scanning into Ubuntu fine I think it's connecting to the printer ok.
I would would think you would want Enabled checked, since that would be like taking it off-line, and Accepting jobs checked.
Hope this helps.

---

### Post by jfbooth on 2011-02-03
ghostborg

that certainly COULD be my problem .. THANK YOU.  

How do I find out the IP address of my printer?  When I do, what is the syntax for putting it into DEVICE URL ... the literal IP??

Thank you .. soon as I can get that info, I will follow your advice.  Thank you again.

Also, I am wondering if SHARED should be checked.
------
I don't think that is the problem afterall.  I found the printer's IP and it will ping.  I have been through everything that I know to try.  I even reinstalled the printer driver.  Probe finds the network printer. Ping works. Everything looks as right as I can make it out .. but still won't print.  Print Test Page gives PRINT STATE UNABLE TO LOCATE PRINTER 'BRN0080770794D4'! which is part of the device URI that 'find printer' comes up with ... URI is 'lpd://BRN0080770794D4/BINARY_P1'.  Using IP address for URI did not work.

I think I know what the two blue bars are on the printer icon .. they indicate the printer is disabled, which happens every time I try to print a test page and it fails.  If I set it back to ENABLED, the two blue bars disappear.

Any ideas, .. anyone??  Thanks in advance.

---

### Post by jfbooth on 2011-02-04
Got it working thanks to this thread:  [http://ubuntuforums.org/showthread.php?p=10428811#post10428811](http://ubuntuforums.org/showthread.php?p=10428811#post10428811)

thank you ghostborg for trying to help me.

---

