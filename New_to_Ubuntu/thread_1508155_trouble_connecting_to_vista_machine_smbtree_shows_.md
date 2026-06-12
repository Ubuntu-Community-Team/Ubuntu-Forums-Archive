---
title: "trouble connecting to vista machine smbtree shows shares can't setup printer!"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-06-12
i messed up big time.  i need a sample script that's right out of the box.  I believe I messed this part up: edit >> i solved this and i guess this doesn't matter!!

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.1, 192.168.0.31/24 eth1

where I put "eth1" should there be a "=" or anything else of that sort?

the problem is that when i use smbtree I get this printout which shows the printers on my moms computer (ellen pc) however when i go to the printer setup from system>>> admin>>> printer>>>> i can then "see" the workgroup and all pc's BUT when i select her computer the only thing that comes up is primopdf!!! She's running norton on the damn thing.  I'm thinking that if smbtree is showing the shares then i should be able to run the print setup wizard or whatever ubuntu is calling it i am sure you understand what i'm sayin. anyways let me know !! ps i am currently listening to music off that pc (bethoven symphony #3 it's not my choice i just wanted to see if everything is working) so i'm guessing that norton is not a problem and the vista machine says printers are being shared on the network sharing gui!!!

brad@brad-laptop:~$ smbtree
Enter brad's password: 
WORKGROUP
    \\ELLEN-PC               
        \\ELLEN-PC\Public             
        \\ELLEN-PC\prnproc$           Printer Drivers
        \\ELLEN-PC\print$             Printer Drivers
        \\ELLEN-PC\PrimoPDF           PrimoPDF
        \\ELLEN-PC\IPC$               Remote IPC
        \\ELLEN-PC\HP Photosmart 7760 series    HP Photosmart 7760 series
        \\ELLEN-PC\D$                 Default share
        \\ELLEN-PC\C$                 Default share
        \\ELLEN-PC\Brother DCP-8040 USB Printer    Brother DCP-8040 USB
        \\ELLEN-PC\ADMIN$             Remote Admin
    \\BRAD-LAPTOP            brad-laptop server (Samba, Ubuntu)
        \\BRAD-LAPTOP\IPC$               IPC Service (brad-laptop server (Samba, Ubuntu))
        \\BRAD-LAPTOP\print$             Printer Drivers

---

### Post by bradmayne04 on 2010-06-13
i figured it out after i came home tonight.  I had to update to kernel 2.6.31-22-generic!!!! There were 246 other update I did as well so that may have played a part also.  I'm not sure I'll investigate tomorrow.  So, I guess I can mark this thread solved.  btw i have now connected a hp photosmart printer which is a 7760 series but i used a driver for the 7750 which works perfectly.  I also have a brother dcp 8040 printer and i tried the regular script but that gave an error on the paper during the test page so I had to use the alternative one which is also located in the printer setup wizard in system >>> admin>>> printer. it then printed perfectly as well. i only had 1 tray so i had to follow the wizard and change the two to one in the setup but it was perfect!!! So, I guess the moral of the story is if the driver you need isn't there then try another one !!!  I still don't understand why the printers didn't show up in the printer setup wizard before the update but showed up when i ran a smbtree command but it's water under the bridge now!

---

