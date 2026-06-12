---
title: "No DHCP in ubuntu 7.04"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by MrGando on 2007-09-14
Hi guys , I am using  Ubuntu Feisty 7.04 , my issue is that I don't have DHCP...

I have a Gigabyte GA-G33M-DS2R , the integrated ethernet seems to be:

"Network adapter - Realtek RTL8111B - Ethernet, Fast Ethernet, Gigabit Ethernet"

I have tried a solution but I don't know how to access a pendrive via console ( where is the pendrive mounted ) ...

If you guys could help me it would be awesome.


Thanks

---

### Post by eggdeng on 2007-09-14
The command ```
mount
``` will give you a list of all mounted filesystems.

---

### Post by Vagabond102 on 2007-09-14
I have the GA-P35-DS3R with a similar nic. I can't even get the interface to go online...my router doesn't see a connection and the lights on the port are out.  Very interesting.

What solution did you try, and did it work?

---

### Post by Walshy on 2007-09-15
I too have exactly the same problem with my GA-P35-DS3R - the switch in the router doesn't register that it's connected to the PC at all!  :confused:

It's as if the NIC powers down when I boot into Kubuntu.  And I get the same result from both the LiveCD and the installed version.

**Edit:** Ok, a bit more searching of the forums here, and I found [this page]("http://ubuntuforums.org/showthread.php?t=538448") which seems to have the solution!  Have made the change, and am about to reboot into Feisty to see if it works.

**Edit 2:** ...and the good news is, I'm posting this right now from my 7.04 install.  That suggested solution worked perfectly!

---

### Post by Vagabond102 on 2007-09-15
Good news!  I too found this yesterday and it worked.

For whatever reason, Windows shuts down the ethernet port and linux doesn't know how to open it.  Have to go into the NIC properties and tell it to allow wake on lan after shutdown.

---

