---
title: "Nic"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by paul-miller on 2006-09-08
Just loaded ubuntu and it appears does not see NIC where are drivers?  System worked fine with windows, put in a different NIC that I know works and still nothing.  NIC's are plain Intel ISA.  Thought I knew something about computers until this.  Even Novell & Red Hat seem to be easier to grasp.
How can I get this to look for new devices?  ](*,) 
Thanks in advance for hints / clues.
-Paul

---

### Post by tbonius on 2006-09-08
-Forums acting up- read post below

---

### Post by tbonius on 2006-09-08
Novell's SUSE and RedHat are still Linux.  When you say the network card is not recognized, do you mean there is no "eth0" device detected?  Do you mean that the kernel module is not loaded?  Does the "eth0" device show up in the kernel boot messages?  What does "lspci -v" show for the detected PCI devices in the system?

---

### Post by paul-miller on 2006-09-08
You are correct, I also have a red hat server in actual production here.  I was trying to show I knew something and have used more than Windows.  I didn't realize ubuntu didn't work with ISA, I put a PCI card in and it works fine.  Now If I can only figure out how to get a command window open like Red Hat!  
Thanks again for the tip there.
-Paul

---

### Post by tbonius on 2006-09-08
Ubuntu works fine with ISA cards.  Its just a matter of sometimes hard setting the IRQs and IO settings on some cards and loading the module with the correct arguments.  The older ISA cards were a pain.. and with maodern PCI buses it becomes too much of a hassle considering that most PCI cards are 10 dollars a pop.  When you say a command window.. I assume you mean a shell?

If you are in the Gnome window manager.. I believe the terminal shell is located somewhere under System Tools.. or whatever the first folder is under the Gnome App menu.

T

---

### Post by jamesr on 2006-09-09
What is the ISA card /NIC that you are having a problem with?

---

