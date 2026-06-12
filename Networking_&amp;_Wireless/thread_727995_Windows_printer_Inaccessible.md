---
title: "Windows printer Inaccessible"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by ObiWanBenDover on 2008-03-18
I have a 3 computer wired home network.  2 XP boxes, each with an attached HP printer and a box running Ubuntu 7.10 with no attached printer.  On the Ubuntu computer, when I go to System/Administration/Printing/New Printer, I select 'Windows Printer via Samba'.  I then browse the smb:// window which opens and I see my Windows workgroup name.  I click on the workgroup name and the names of my two XP computers appear.  I click on the name of one of the XP computers and the attached printer name appears.  I select the printer name and a Verify button appears on the New Printer window.  Pressing the Verify button gives me the following message:"Inaccessible  This printer share is not accessible".  The HP printer on the XP box is set up to share and disabling my firewall on the XP box has no effect.  I have also enables Print Services for Unix on the XP computer.
What next?

---

### Post by ObiWanBenDover on 2008-03-19
****SOLVED***********
As mentioned by EricDB, replacing the Samba generated' WorkGroup/Computer_Name' with the computer's IP address solved the problem.

---

