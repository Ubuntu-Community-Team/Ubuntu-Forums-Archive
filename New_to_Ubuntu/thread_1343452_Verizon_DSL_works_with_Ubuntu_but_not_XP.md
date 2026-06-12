---
title: "Verizon DSL works with Ubuntu but not XP"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Malizia on 2009-12-01
I got DSL up and running on Ubuntu about a month ago. But i had to Install Windows XP recently, and can't get DSL to work on that OS. I have the verizon CD to do the windows installation, but my graphics in XP are messed up. And it's hindering what i can see in order to follow the directions. I get to the part where it checks my connection, but it doesn't detect anything. Which is obvioulsy frustrating since I'm good to go on Ubuntu. Can't fix the graphics problem, because i can't connect and update the driver. Plus when i go the control panel, it will only allow me to use the lowest possible pixel setting, no clue why. I think XP originally came on my machine, or atleast that what the specs online say. Anyone had a similiar problem, or could possibly point a newbie in the right direction.

---

### Post by bsharp on 2009-12-01
Sounds like you need to install graphics drivers in XP. Search for the model of your computer on your manufacturer's website in Ubuntu and save the drivers to your XP partition. Boot to XP, install the drivers, and you should be good to go.

---

### Post by Malizia on 2009-12-01
How do I save something into my XP partition from Ubuntu?

---

### Post by teward on 2009-12-01
Mount your XP partition, save into your XP partition, then unmount.  Assuming that its FAT32.  If its NTFS, you might need to install a few packages to make it work (don't ask me, I don't know what they are, mine just worked once I installed Ubuntu),

---

### Post by Malizia on 2009-12-01
It's NTFS

---

### Post by bsharp on 2009-12-01
It should just appear as a XXX GB Partition under Places. Just open it and it will mount automatically.

---

### Post by Malizia on 2009-12-03
Thanks bsharp. 

I found my monitor's driver update (Gateway EV730) on gateway's website. XP_Montior(2),exe. But when i opened it on my windows partition it just turned into XP_monitor.txt

[COLOR=Red]Windows XP Plug and Play Monitor and Driver Information 
 
Monitors associated to this information file do not need an updated driver. Microsoft(r) Windows(r) XP automatically detects the type upon startup. In Windows XP, the monitor type is set to Plug and Play Monitor for the monitor driver. [/COLOR]

Every blog i read about people having this problem they say to just upload the new driver, this says there isn't one??

---

### Post by electricFan on 2009-12-03
Malizia, I have spent many hours tracking down drivers for Windows XP computer reinstalls.  Sometimes the manufacturer does not offer the drivers directly and they may redirect you to another site (this happened for me with Gateway).  Whatever you do, be extremely cautious when downloading drivers online.  Make sure they are from a respectable reputable source.  I have downloaded drivers only to find out that they were viruses before.  Make sure your driver downloads are from a trusted source.

---

### Post by electricFan on 2009-12-03
> **Malizia said:**
> Thanks bsharp. 

I found my monitor's driver update (Gateway EV730) on gateway's website. XP_Montior(2),exe. But when i opened it on my windows partition it just turned into XP_monitor.txt

  Interesting, maybe you should download the driver, burn it to a cd, and then load it onto your Windows XP?

---

### Post by halitech on 2009-12-03
sounds like you need the video card drivers and the NIC drivers (not to mention probably sound card drivers as well) in order to get things going. I keep a folder of all the drivers I download on my system plus on an external drive so I have them.

---

