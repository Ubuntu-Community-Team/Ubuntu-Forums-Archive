---
title: "Restore eeprom on notbook nic"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by Stone123 on 2006-09-05
I am getting this bad checksum on eth0 i8***/7/8 notebook card. Since it uses e100 , the developers of driver had made eth0 fail because  of faulty eeprom, but it still works(from windows) ,and i know it worked with older driver with bad eeprom. It even displays error from bios something about netboot PXE-* . Now driver developers have sad that they have made it so that users use ethtool  or eepro100-diag tool to repair it. 

[http://www.penguin-soft.com/penguin/man/8/eepro100-diag.print](http://www.penguin-soft.com/penguin/man/8/eepro100-diag.print)

Ubuntus version of eepro100-diag doesn't support -E flag that is  
  -E, --emergency-rewrite
    Re-write a corrupted EEPROM

Where to go from here?

---

### Post by Haim on 2006-09-05
I'm having the same issues.
Some others with the same on these boards too.

[http://www.ubuntuforums.org/showthread.php?t=238323&highlight=eeprom](http://www.ubuntuforums.org/showthread.php?t=238323&highlight=eeprom)

Though this is a checksum rather than corrupt eeprom error.  Now I can't find the other two or three on ubuntu forums  arrrghh

Some patch available to ignore eeprom check.

I'd like to rewrite also but am also stuck like you...what a useful post huh!

Anyway, keen for any suggestions from people too.

Haim

---

### Post by Stone123 on 2006-09-05
Intresting read :
 And BTW I want to remind the entire world that the last time Intel
cried wolf to all of us about vendors using broken EEPROMs with their networking chips it turned out to be a bug in one of the patches Intel  put into the Linux driver. :-)

But eeprom can be damage from power loss , lightnings and such , so i think i ll see what i can do with ethtool .

---

### Post by Haim on 2006-09-05
Mines on a t20 ibm thinkpad, using an intel mini-pc etherjet.

Having been scanning around intel and lenovo/ibm websites for eeprom updating but what tools they have don't seem to be suited to my hardware....I think anyway.

intel has erupdate.exe for some adapters.

The ethtools stuff and what not is a little over my head, and man pages aren't that easy to glean info from.

Haim

---

### Post by Stone123 on 2006-09-05
Well i have found this  
[http://www.intel.com/support/network/adapter/pro100/bootagent/sb/cs-008212.htm](http://www.intel.com/support/network/adapter/pro100/bootagent/sb/cs-008212.htm)

I ll have to test it , report later

---

### Post by Haim on 2006-09-07
Looks like this guy may have the same issue.

[http://www.ubuntuforums.org/showthread.php?t=251865&highlight=eeprom](http://www.ubuntuforums.org/showthread.php?t=251865&highlight=eeprom)

I'm struggling to find time to look at this sorry, pregnant wife and small kid doens't leave much for mucking about on linux.

---

### Post by Kuma_Pageworks on 2006-09-07
According to my brother, who works for IBM, if an EEPROM is corrupted, it's finished.  He's had to throw away EEPROM cards before that were corrupted.  Intel's solution may work, but in my case I downloaded the firmware update from IBM for the ethernet EEPROM and it said 'BAD DATA' and exited.

So there are definitely times when you can't fix the EEPROM anymore.

---

