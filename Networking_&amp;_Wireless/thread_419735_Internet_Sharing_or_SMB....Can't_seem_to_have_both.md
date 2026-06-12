---
title: "Internet Sharing or SMB....Can't seem to have both at the same time."
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by JungMin on 2007-04-23
Hi, i just installed Ubuntu 7.04 (coming from Suse 10.2).  Must say its pretty nice....

ANyways, I am trying to share my internet connection and share some folders using SMB but its not working out.

I used 'FireStarter' to get the internet sharing going as I couldnt find anywhere else to turn it on (found that idea in a thread somewhere).  So, if firestarter is running then YES, the other computer can access the internet.

I added SMB as a policy (default ports are 137-139, 445) and just opened them on the LAN.  But even with this, I cant access the shares when FireStarter is running.  I have to click STOP to access the share, but then so does the internet sharing!!!

Am I not opening the correct ports??  I searched around and it seems like 445 is the right one....

---

### Post by JungMin on 2007-04-23
Have tried deleting the shares, and readding them.  Reinstalled FireStarter......Nuthin works.

---

### Post by JungMin on 2007-04-29
I understand that Firestarter is just a frontend to iPTables.  So, why am I having this problem???  It is really annoying!!

Any ideas??  Thanks

---

### Post by koenn on 2007-04-29
Possibly iptables is blocking your smb traffic. 
To troubleshoot it, you'd have to post your iptables ruleset, and explain in detail what your network looks like. eg; from your posts so far, i can't make out which computer (the one with the internet connection or the other) does the filesharing.

---

