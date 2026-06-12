---
title: "Wireless printing."
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Cenbuntu on 2008-06-12
As a final project for computer engineering, my friend and I were in placed in charge of setting up a printer on a linux system. The purpose of the project is to print a document on the linux system wirelessly via another computer (most likely windows). 
However, I am not particularily fond of linux since it is a nuissance to learn text interface, I depend on windows. It was advertised that Ubuntu is more "user friendly" than previous linux operating systems, so naturally it was selected. (v8.04)
The printer we were provided was **Epson Stylux CX4600**, the cartrige nozzles are clogged and the black cartrige has no fluid, so at this point it is more or less a matter of being able to queu a job to the printer.
_The first problem:_We have selected the printer from Ubuntu's list of printers, however the printer does not react in any form when attempting to print test documents. So we are not even sure Ubuntu recognizes that the device is connected, My laptop seems to have recognized it, so the printer is fully functional.
_The second problem:_Because I am dependant of Windows I do not know how to connect wirelessly, I have no clue on how to allow a system send jobs to the printer wirelessly. The school has a network, so at this point my options are peer to peer or via network, wither will do. The wireless device we are using is a **TrendNet TEW-424UB 54 Mbps 802.11g Wireless USB 2.0 Adapter**.
Please suggest solutions, it would be greatly appreciated. Thanks.

---

### Post by Turkey Pwner on 2008-06-12
You will have to set up your wireless driver via ndiswrapper, and set up SAMBA.

Don't ask me how to set up SAMBA.  I've tried with no positive results whatsoever.

Install ndisgtk to help set up ndiswrapper, and select the Windows ME driver. ;)

---

### Post by Cenbuntu on 2008-06-12
Alright, I've downloaded all 3 suggested programs. I do not currently have the Ubuntu system in front of me as I am at home. Any special notes anyone would like to add, or better yet a step by step walthrough to these programs?

---

### Post by Turkey Pwner on 2008-06-12
> **Cenbuntu said:**
> Alright, I've downloaded all 3 suggested programs. I do not currently have the Ubuntu system in front of me as I am at home. Any special notes anyone would like to add, or better yet a step by step walthrough to these programs?For ndiswrapper, or more specifically, ndisgtk, one needs only to open System> Administration> Windows Wireless Drivers, click "Install new driver", and select the Windows ME drivers for your wireless card (downloaded from Trendnet's website).  This is only necessary if your wireless networking is NOT already working.  I was also assuming that you would have installed the programs via Synaptic using an ethernet connections... because ndisgtk has dependencies.  As for SAMBA, see below:

Actually, scratch the SAMBA necessity.  I read on a SAMBA guide that you only need CUPS (preinstalled with Ubuntu) to print through a Windows machine.  Refer to [this ubuntuforums.org thread](http://ubuntuforums.org/showthread.php?t=268245).

Please let that work. >_<

---

