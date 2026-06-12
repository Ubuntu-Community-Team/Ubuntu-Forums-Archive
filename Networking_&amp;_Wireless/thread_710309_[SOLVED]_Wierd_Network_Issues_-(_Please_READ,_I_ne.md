---
title: "[SOLVED] Wierd Network Issues?? :-( Please READ, I need help"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by neurostu on 2008-02-28
So I currently have 7 machines running Gutsy. One is setup with two ethernet cards. one card is plugged into the gigabit ethernet of my building, the other is plugged into a gigabit switch.

I have setup internet sharing across the two cards.  The 2nd card has an ip of 192.168.1.100 and subnet of 255.255.0.0

I then have 6 machines plugged into the gigabit switch. they all have an assigned IP ranging from 192.168.1.111 to 192.168.1.116.  

they were all setup correctly and running great. I had this setup going for well over a month without any problems.

Yesterday I started doing some network benchmarks. I was sending  UDP packets from one machine to another, broadcasting  UDP packets onto the subnet from the main machine ( I was sending 1 million packets of 600 bytes at about 16K packets/second)  it was working great but then after an hour or two of on and off testing the network just stopped working. 

Now I can only ping 3 of the 6 machines from my main machine. All 3 of those machines can ping each other. The other 3 machines are completely isolated from the network. I can't ping into them our out of them...  I've reset my main machine, I've reset the switch (several times), and swapped which ports the computers are plugged into. I've reset the 3 bad machines... but to no avail.  They don't seem to be on the network at all...

Also I checked all the network settings in with ifconfig and they are all setup correctly

I have no clue as to how to troubleshoot this situation, any advise? :confused:

---

### Post by neurostu on 2008-02-28
It was an issue with my switch. I replaced my switch and the problem went away.

---

