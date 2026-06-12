---
title: "Printing from Vista to Ubuntu 9.04 Printer"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Andyproctor on 2009-09-06
Sirs...

Having spent some time today (hours) trying to solve this, following much advice from these forums and elsewhere I finally give in and ask for help. 

I have recently installed 9.04 (64 bit version) Ubuntu on my main home PC and everything going well on that front. Printer works perfectly as does everything else i've tried. I have set up my other halves laptop (she runs XP) to network print to the printer connected to ubuntu and thats great. My problem is my Vista laptop...

I have tried much advice and am clearly missing something in the vista setup to allow vista to see or print to the printer hanging on the ubuntu box. I have been able to get xp working easily so I know Ubuntu is good. 

Adding printers in vista via the add printer wizard, using any settings or route seems to fail, and often crash the print spooler in vista. This laptop previously used the same printer hung from an xp box. So adding via http://<host ip>:631/printers/<printername> works in xp but not vista. I have anabled LPR in vista (home premium) but to no avail. 

Can anyone give me any more ideas on how to get this to work? 

Thanks

Andy

---

### Post by twright on 2009-09-06
Hi,
I have a similar setup at home so it should be possible at least :D

If you also share some folders on the machine that is printing then you will be able to find the machine and printer in network places on Vista which should be much easier. Simply right click on a folder and go into the share tab of properties to share it over the network - this will install samba which creates a printers share by default which Vista should be able to see and connect to without hassle. Sharing a random folder will also let you test that the networking is working properly - you can delete it again afterwards if you so please.

Good luck

---

### Post by Andyproctor on 2009-09-06
Dear twright,

Many many thanks for the help! I did as you said and shard a folder in my user account on the UB machine and samba installed without issue. I then could not connect to it from vista, although it appeared in "Network and Sharing centre" as a username/password was required but nothing (the correct ones) allowed access. A quick search on the web pointed to the need to put a "hosts allow" line in etc/samba/smb.conf in the networks section. 
I added hosts allow = 127.0.0.1 192.168.1.0/24 (to allow all my dynamic subnet) and the vista unit immediately was able to add the printer and use it, and the shared drive is useful too!

Brilliant, many thanks. I hope this helps others too!!

Andy

:D

---

