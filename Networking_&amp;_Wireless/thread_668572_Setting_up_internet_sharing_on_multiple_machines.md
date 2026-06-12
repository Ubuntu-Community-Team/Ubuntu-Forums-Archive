---
title: "Setting up internet sharing on multiple machines"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by neurostu on 2008-01-15
So I am trying to get internet sharing up and running on multiple machines. I have one central machine that has one ethernet card plugged into my institutions ethernet and then I have another ethernet card set up and plugged into a gigabit switch.

I have 6 shuttles all plugged into the switch.  I installed Gutsy on all of them and 2 of them worked and the other 4 didn't.  of the 6, 2 are the same, and the other 4 are the same. The two that are the same are brand new shuttles [(SN68PTG5)]("http://us.shuttle.com/barebone/Models/sn68ptg5.html") .  When I ping on the shuttle that doesn't work it just says Network is unreachable.  I can't ping itself, the other machines, or the internet server.

Of the 4 machines that are the same I can only get internet on one of them. I have set them all up (all 6) exactly the same:
 - I gave each a static IP
 - I gave each a unique IP 192.168.1.10X     [X = 1-6]
 - I set up the subnet mask as the same as it is on the ethernet card that is sharing the internet
 - I set up the gateway address all the same

So again I have 6 machines trying to connect to one central internet server that is set up and working.
2 machines can connect and share internet correctly but 1 is 1 of 2 new machines and the other 1 is 1 of 4 old machines.

I have no clue what to do please help!

---

### Post by mips on 2008-01-15
Show us the eth configs of the main(router) pc.

The easiest way to do this is to install firestarter if you are using a desktop environment for the main/router pc.

Here is another great alternative:
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

### Post by neurostu on 2008-01-21
The problem was I had the wrong bios installed on the shuttles. I had to update the bios when I upgraded the cpu's and I didn't select the proper bios. Once I reflashed the BIOS the network cards worked perfectly.

---

### Post by mips on 2008-01-22
> **neurostu said:**
> The problem was I had the wrong bios installed on the shuttles. I had to update the bios when I upgraded the cpu's and I didn't select the proper bios. Once I reflashed the BIOS the network cards worked perfectly.


That is interesting to know thanks. Might come in handy for other shuttle owners.

....
Keywords: Shuttle, Shuttle PC, LAN, LAN Card, Dead, Not working, BIOS

---

