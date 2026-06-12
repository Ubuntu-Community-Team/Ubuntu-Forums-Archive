---
title: "Ubuntu 64 for my Dell PowerEdge 1850 Install problem"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Ross_and_Eye on 2009-12-10
I'm hopeing somebody can help me, I can install windows 95 no problem, but this, WoW!  No idea. What is an argument?  I Ran the Demo on my Wife's Dell Precision 380, it Ran just great, not a problem. Cool, no to install it on the PowerEdge, Oops, I get to the screen which allows me to select from installing it or just running the demo and after that, it goes to a screen with a funny symbol in the middle of it, Runs the CD and drives for 5 minuets or so and then gives a black screen, I caught a Glimpse of deleting some set-up files or something and then blank. 

Can anybody tell me exactly what arguments I must add and where to add them?  The exact text?  I looked at the help page for a long time, it makes no sense at all to me. The stuff under the F6 key, might as well be Greek.

Can anybody confirm that this will run on this computer?  Should be the same as a PowerEdge 2850, do I have to set up the RAID first?  More or less RAM?

---

### Post by mikewhatever on 2009-12-11
Can you provide info about your computer, CPU, RAM, graphics, everything else you know. Try running the demo in Safe graphics mode by pressing f4 at the menu and selecting the said mode.

---

### Post by Geoff918 on 2009-12-11
Sometimes that will happen with the graphics. An *old* system of mine from college runs fine, but it would blackscreen on me.

Try the F6 and then do the "Safe Graphics Install"

That will likely fix you right up! :)

(I also usually turn off the ACPI and all, too. Those are power management extensions that may gum up the works--you could initially try just setting the above, though)

---

### Post by running_rabbit07 on 2009-12-11
Sounds like a 64 bit disk in a 32 bit system. We definitely need more info in order to help.

---

### Post by Ross_and_Eye on 2009-12-11
> **running_rabbit07 said:**
> Sounds like a 64 bit disk in a 32 bit system. We definitely need more info in order to help.

The Dell PowerEdge 1850 is a 64 Bit System with Dual Xeon 2.8 Gig Processors and an 800MHZ FSB, Same like a PowerEdge 2850, Thanks, I wish it was that simple

Item specifics      Brand:  Dell Model:  PowerEdge 1850  Form Factor:  Rack-Mountable 1U Platform:  PC  Processor Type:  Xeon RAM Technology:  DDR2 SDRAM  Chipset:  Intel E7520 Compatible Operating Systems:  Microsoft Windows Server 2003 Enterprise Edition  Condition:  Used Series:  PowerEdge  Number of Processors:  2 Intel Xeon      [See reviews]("http://search.reviews.ebay.com/_W0QQfvcsZ2991QQsoprZ66955558QQupvrZ3")
  
     
     Detailed item info
    [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Product MPN**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]MPN[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]PE1850[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Key Features**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Form Factor[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Rack-Mountable 1U[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Platform[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]PC, Unix[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Processor**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Processor Manufacturer[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Intel[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Processor Type[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Xeon[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Memory**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]RAM Technology[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]DDR2 SDRAM[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Maximum RAM[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]12 GB[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Supported RAM speeds[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]400 MHz[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Hard Drive**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Maximum Storage Capacity[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]600 GB[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Hard Drive Interface[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]SCSI[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Networking**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Networking Type[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]10/100/1000 Network Adapters x 2[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Data Link Protocol[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Ethernet, Fast Ethernet, Gigabit Ethernet[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Technical Features**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Hot Swap Components[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Hard Disk Drives, Power Supply[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Integrated Input/Output Ports[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]RJ45 Lan Port x 2[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Motherboard**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Installed L2 Cache Memory[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]2 MB[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Chipset[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Intel E7520[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Audio / Video**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Installed Video Memory[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]16 MB[/SIZE][/FONT]  
  [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Other Features**[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Expansion Bays[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]2 x 1" Hot-swap Ultra320/160 SCSI[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Power Supply[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Hot Swap Redundant[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Power Supply Output[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]550 Watt[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]System Management[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Intelligent Platform Management Interface (IPMI)[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Compatible Operating Systems[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]Microsoft Windows Server 2003 Enterprise Edition, Microsoft Windows Server 2003 Standard Edition, Microsoft Windows Server 2003 Web Edition, Novell NetWare 5.x, Novell NetWare 6.x, Red Hat Enterprise Linux 2.1, Red Hat Enterprise Linux 3.0[/SIZE][/FONT]  [FONT=Arial, Helvetica, sans-serif][SIZE=2]Other Features[/SIZE][/FONT] [FONT=Arial, Helvetica, sans-serif][SIZE=2]64bit Ready[/SIZE][/FONT]

---

### Post by Ross_and_Eye on 2009-12-11
> **mikewhatever said:**
> Can you provide info about your computer, CPU, RAM, graphics, everything else you know. Try running the demo in Safe graphics mode by pressing f4 at the menu and selecting the said mode.

Cool!!!  That worked, thanks Mike!!!  Now I am to a screen that wants to set up the Partition table, everything is Grayed out and the table is blank, I assume the software cannot see the hard drives?

---

### Post by terroid on 2009-12-28
I have also encounter this same issue when attempting to isntall on the Dell Poweredge 1850.  Is there a resolution available?
Please help
Thanks
Terri
> **Ross_and_Eye said:**
> Cool!!! That worked, thanks Mike!!! Now I am to a screen that wants to set up the Partition table, everything is Grayed out and the table is blank, I assume the software cannot see the hard drives?

---

### Post by Ross_and_Eye on 2009-12-29
Try running the demo in Safe graphics mode by pressing f4 at the menu and selecting the said mode.

---

