---
title: "Attaching to Active Directory and Sharing Print Drivers"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by kublah on 2008-05-27
I have been trying to setup samba to share network printers through ubuntu server to our existing active driectory. Right now I am at a dead end, I can view the shared printers on the windows client machines using \\server\printers\, But active directory will still not acknowledge the printers. further when I try to attach to the domain, sometimes I lose all access to my server and have to recover.

Also I would like to setup samba to have the client printers available for when they are linked to a windows machine. i.e. once active directory works correctly with the ubuntu server, I would browse out and find the printer. Then attach it and the correct drivers will automatically download from the samba printer driver repository.

Please help!

---

### Post by kublah on 2008-05-30
bump

---

### Post by kublah on 2008-06-03
succeeded with flying colors!

now i need to setup the driver share ( [print$] )

can anyone help with this?


i have mainly 3 printers to worry about, HP 4350s, 4240,s and 4250s.

what I am aiming for is to setup that print driver repository so that when a new printer is connected to a windows machine the windows will automatically select the available print driver from the linux server and install it. (this is what i understand the [print$] subconfig is for, please correct me if I am wrong)

---

### Post by IddyBittyBugs on 2008-06-07
I think I'm stuck with the same problem as yours.  My Windows boxes can see the printer on the network, but won't install it because Windows reports that the incorrect driver is installed on the Ubuntu box.  This happens even though my Ubuntu box prints fine, and the Windows box has the printer driver installed on it as well.

I've scoured the forums and have yet to find anything helpful with this.

---

### Post by kublah on 2008-06-10
No thats not quite my problem. My windows machines, once installed with the correct print driver from HP, can print just fine. I just would like to automate the installing of the print driver on the windows machines. The plan is to use active directory to assign printers for groups of users, and when the users are added to the groups, the printers show up automatically and install. (in theory this mostly works...except the driver part.)

From what i have read the [print$] share in smb.conf can be used by windows machines to find their driver. unfortunately no one ever explains how to set this up. I have put the drivers im using in that folder but apparently they need to be in some sort of configuration script.

---

