---
title: "Re-scanning for wireless networks"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by jasbur on 2007-10-20
The WiFi on my laptop is working great but, I can't seem to find a way to re-scan for wireless networks after bringing it out of standby. If I click on the network manager applet it seems to show an updated list about 3 out of 4 times. The rest of the time it just shows the networks from my previous location.

Is there a way to force it to do a re-scan so I can be positive the list is up to date? I use this laptop to diagnose network issues pretty frequently and I hate to have my customers see me boot into Vista to run a quick scan.

---

### Post by Dr. Nick on 2007-10-20
maybe right clicking and disabling wireless, pause a minute then right click and re-enable wireless? 

Just a idea, IIRC ive done that in the past.

---

### Post by jasbur on 2007-10-20
That seems like an awfully hacky way to do it. You would think this would be something built into the applet or at least from the command line.

---

### Post by ubernoob on 2007-10-20
Same problem here, but i haven't had the chance to dig into the problem. Tell me if you find out.

For the record, I have an intel 4965 agn wireless. In case it's a driver issue.

---

### Post by alterKrieg on 2007-10-31
Did anyone ever find a solution to this?  I really hate having to reboot the machine just to switch from a work network to a home network after walking home.  There's got to be a way to force a rescan.

---

### Post by kevdog on 2007-10-31
You can always scan manually at the command line (that is what network manager does in the background)

The command is
iwlist scan

---

