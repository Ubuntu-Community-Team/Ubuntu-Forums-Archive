---
title: "Connection problem between 2 pc's."
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by AceRimmer on 2006-11-09
Hey guys, hopefully someone can help me. I have two Edgy machines networked with both set to static IP's on the same subnet and all that stuff.  All of a sudden one machine cannot connect to anything on the network other than the Internet, via a coyote Linux router PC that connects to my DSL. The other night I enabled MAC address filtering and IP filtering from my side on the router, and then I lost connection after awhile, though I'm sure I had connection for a couple hours after I had reloaded the firewall.  It was after I rebooted the Edgy PC's that I lost connection I think. I managed to remove the filters from the router which got my net connections working, but I this computer still shows "No Network Connection" via my little applet or whatever you call it that runs in the top bar.  I can ping the other computer via the terminal but that is it.  The setting in Network show static IP and the host names and subnet mask and all that stuff, but when I open Network Places I get nothing.  One Edgy box can connect to the other though, but it seem to be a dodgy thing as it doesn't seem to always work after I reboot that machine.

My network setup is DSL-> DSL Modem -> Linux Router -> Switch -> PC's. 

Would router settings have an effect on the networking via the two switch connnected computers?

---

### Post by AceRimmer on 2006-11-09
It's weired.  Now I can't get the shared folder of my systems to show up in Network Servers, but occasionaly I can go into the Windows Network Icon and find entries for both servers and access the files, yet it comes and goes.  

When I boot the one system into XP it shows the network fine.](*,)

---

### Post by AceRimmer on 2006-11-10
Screw it.  I am dumping Edgy and going back to 6.06 and trying to see if that works better.

---

### Post by AceRimmer on 2006-11-11
Damn.  Re-installed Dapper on my secondary PC, then reinstalled Edgy on my main PC.  No help.  When I open Network Browser I have an icon WINDOWS NETWORK, which I click then it shows the Workgroup MSHOME, then if I click that it shows two empty page icons with my two system names.  But they are not folders or system icons, they are like blank page icons. The funny thing is that the first time I do this after I boot I will get system icons at the end and can access folders on the other system, but if I close the window and reopen I get the blank pages again. I went and redid my Coyote Linux Floppy router next, as I thought maybe it was the problem. No dice, same problems. 

](*,) 

Any help?

EDIT:  I went in and tried to change the folder sharing to NFS from SMB.  No luck.  Now I can't change it back, or delete the shares.  NO matter what when I go back into Sharing I have two shares, one shows NFS and one SMB, but both show NFS when I open them.  Oh well, I'm taking Ubuntu off this system and just turning the Ubuntu drive into a secondary Windows drive.  I'll leave Dapper as is on the other system since I don't have much choice... 
](*,)

---

