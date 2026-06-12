---
title: "wireless network configuration"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by diamantis13 on 2008-10-01
Hi,
I have a desktop computer running ubuntu 8.04 and recently I got an old laptop. While I can connect to various wireless or wired connection with the laptop I can't connect it to my desktop. I get the limited or no connectivity error message. I searched through various forums but couldn't find what is the problem
My Desktop runs Ubuntu 8.04 and I connect with a 2wire router. The laptop runs Windows XP (SP3 and all the current security updates) and has a NETGEAR wireless card.
Any ideas for what might be going wrong?
Thank you very much

---

### Post by iponeverything on 2008-10-01
> **diamantis13 said:**
> Hi,
I have a desktop computer running ubuntu 8.04 and recently I got an old laptop. While I can connect to various wireless or wired connection with the laptop I can't connect it to my desktop. I get the limited or no connectivity error message. I searched through various forums but couldn't find what is the problem
My Desktop runs Ubuntu 8.04 and I connect with a 2wire router. The laptop runs Windows XP (SP3 and all the current security updates) and has a NETGEAR wireless card.
Any ideas for what might be going wrong?
Thank you very much


Your question is not clear. What is the goal? NAT through the 8.04 machine?
Access shared drives on the 8.04 machine. Wired or Wireless?

---

### Post by diamantis13 on 2008-10-02
I am interested in the wireless connection for both file sharing and accessing the internet through the 8.04 machine.
Thank you

---

### Post by superprash2003 on 2008-10-02
how can you be connecting to various wired or wireless connections.. you would have to connect to the network where the xp laptop is.. once you do that.. ensure that both pcs can ping each other first.. ensure that no firewall is blocking.. 
  For file sharing you need to install samba on the ubuntu machine and enable file sharing in the xp machine.. 
For reference : File sharing in xp - [http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)
Samba setup ubuntu - [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by diamantis13 on 2008-10-02
I was able to connect with this laptop to the wireless on campus and in other places, so it seems that the problem is not with the laptop. So there should be some problem with my ubuntu desktop (perhaps I have to configure something?)

---

### Post by superprash2003 on 2008-10-03
are you connected to the desktop directly via ad hoc network or through a wifi router.. if through a wifi router, are you able to access the internet.. are you able to ping the desktop machine?

---

### Post by diamantis13 on 2008-10-04
it was through a wireless router but I wasn't able to access the the internet. I didn't try to ping the desktop, next time I bring home the laptop I will try and post the results.

---

### Post by kforum on 2008-10-05
this is still very confusing(or maybe its just me), but on a side note, it was quite easy to get my lan working last time i tried it in ubuntu.
for file sharing i was kinda lost on what to do(even though i had everything 'set'), till i just went inot the file manager and typed the ip i was trying to access(pc n.2) and it even created a link for me i believe(in the desktop), after that it was simple.

hope that hint help, though im really not sure what exactly you want to do/what is your situation, etc...

cheers.

---

