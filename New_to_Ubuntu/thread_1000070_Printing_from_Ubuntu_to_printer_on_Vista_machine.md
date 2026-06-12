---
title: "Printing from Ubuntu to printer on Vista machine"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by mothraman on 2008-12-02
I have been working on this on and off for a while.  All the solutions I have seen and tried are great, except that they do not work for me.

Here's the situation: 
. hp officejet 4100 series attached to a lenovo thinkcentre A57 (core 2 duo 2.4mhz 4G RAM) with windows vista ultimate
. ubuntu 8.10 on IBM netvista 2263-31U 2.0ghz processor, 1.5G RAM
. able to see and access files to and from the vista machine and another laptop running XP on the same network
. can print from the XP laptop to the vista machine

When I go to add the printer (system/administration/printing) I can find the printer. I select the driver from the list. Downloading the ppd file from the HP website yields the same results.

When I print a test page (or anything else), the printer clicks like it is going to print but goes no further.  The job shows up in the print queue vista as "remote downlevel document" and stays there until I kill it.

I've also tried "gksudo hp-setup"--it can find no devices attached to the vista machine, even when I used "find manually" and give it the workgroup and computer name.

This can't be this hard. What am I missing?

---

### Post by phidia on 2008-12-02
Open synaptic and search for and install the hplip-gui package.
When that completes use it to set up the printer.

---

### Post by mothraman on 2008-12-02
done that...see op for results

---

### Post by philinux on 2008-12-02
You've obviously set it up as windows printing via samba?

I had to use smb//:192.xxxxxxx 

with no workgroup mentioned at all as ubuntu could not find the printer using the search function.

---

### Post by mothraman on 2008-12-03
> **philinux said:**
> You've obviously set it up as windows printing via samba?

I had to use smb//:192.xxxxxxx 

with no workgroup mentioned at all as ubuntu could not find the printer using the search function.
Thanks. I tried that before, too...tried again, same result.  I also renamed the printer to take spaces out of the name...same results.

When I click on "verify" during printer setup, it comes back verified (same before and after renaming).

Cannot find the printer using "browse" but that's the same for file shares on Vista--need to supply server (with or without workgroup--no difference). That may be why hp-setup can't find the printer (or not).

Again, the printer makes noises but does not print.  The job is in the print queue on vista and stays there until I kill it. This is a constant in everything I've tried.  I've even tried alternate printer models in driver setup.

Any other suggestions?

---

### Post by philinux on 2008-12-03
Maybe something in here might help your situation.
[SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

Have you tried temporarily disabling the vista firewall etc etc.

---

### Post by mothraman on 2008-12-03
> **phidia said:**
> Open synaptic and search for and install the hplip-gui package.
When that completes use it to set up the printer.
see above...I've done that

---

### Post by mothraman on 2008-12-07
Yes I been through all of that.  

I am able to share files, and I am able to verify the vista printer share, I just can't see it and can't print to it, and hp-setup can't find it.

---

### Post by organica on 2008-12-07
> **mothraman said:**
> Yes I been through all of that.  

I am able to share files, and I am able to verify the vista printer share, I just can't see it and can't print to it, and hp-setup can't find it.

Yes, I have the same printer with the same setup you have.  I just noticed this problem today.  Several weeks ago, I was able to print without any problems.  Since I had swapped out my router, I had to reinstall the printer.  Well, I ran into the same problem today.  

I wonder if the recent cups update has caused this issue.

Anybody have any ideas?

---

### Post by organica on 2008-12-07
> **mothraman said:**
> Yes I been through all of that.  

I am able to share files, and I am able to verify the vista printer share, I just can't see it and can't print to it, and hp-setup can't find it.

SOLVED:  Un-install then Re-install Windows XP printer.  This solved the problem for me.

---

### Post by mothraman on 2008-12-07
I'm glad for you. However, that's another thing I have done that produced no results.

---

