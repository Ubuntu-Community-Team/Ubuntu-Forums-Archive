---
title: "A basic networking question"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by BobSongs on 2007-12-06
I'm being asked to look at a series of older computers that an owner wants to network together. I'm going to suggest Ubuntu as a replacement O/S for these Windows 2000/Windows 98 machines. (I haven't yet seen them.)

I just thought I'd ask about how difficult it is to network these machines together for file sharing. Linux tends to be a lot more secure than, say, Windows XP. I've occasionally shared folders under XP... but never under Ubuntu since I don't have a set of boxes to test this with.

Anyone have a quick link to a "How To" pointing out how to allow for network sharing? I suppose the idea of sharing a single or several printers is not as easy as it is under Ubuntu? I'm thinking of going with Feisty Fawn... or possibly as far back as Dapper Drake. I have yet to see these machines to offer an estimate.

Thanks guys!

---

### Post by tact on 2007-12-06
First thing to save headaches later will be to ensure that the hardware is supported adequately under any of the varieties of ubuntu you mentioned.  

Once over that hurdle, networking (ubuntu to ubuntu or ubuntu to windows) is pretty straight forward - moreso with later varietals like Feisty and Gutsy.

I know a lot of people have had problems with Gutsy but on hardware thats supported it if fantastic.  At least give it a shot.  The reasons being:
- better printer setup and config
- easier file sharing

Under Feisty and Gutsy ... once you have done the install - to share folders/files just right click on the folder and select "sharing".   As this is the first time you attempt to share a dialog will come up advising you that you have to install SMB or NFS.  Leave both boxes selected and intall both.

Couple of points.  The default setup is one that:
-  requires username/passwords to access shares.  i.e For user fred to access a share on PC-B from PC-A he must have an account on PC-A and also PC-B 
-  appropriate permissions set on the files/folders shared

You can change the default and toss away these increased levels of security with a simple edit to the /etc/samba/smb.conf file to set security level=share

---

### Post by BobSongs on 2007-12-06
> **tact said:**
> First thing to save headaches later will be to ensure that the hardware is supported adequately under any of the varieties of ubuntu you mentioned.  

Once over that hurdle, networking (ubuntu to ubuntu or ubuntu to windows) is pretty straight forward - moreso with later varietals like Feisty and Gutsy.

I know a lot of people have had problems with Gutsy but on hardware thats supported it if fantastic.  At least give it a shot.  The reasons being:
- better printer setup and config
- easier file sharing

Under Feisty and Gutsy ... once you have done the install - to share folders/files just right click on the folder and select "sharing".   As this is the first time you attempt to share a dialog will come up advising you that you have to install SMB or NFS.  Leave both boxes selected and intall both.

Couple of points.  The default setup is one that:
-  requires username/passwords to access shares.  i.e For user fred to access a share on PC-B from PC-A he must have an account on PC-A and also PC-B 
-  appropriate permissions set on the files/folders shared

You can change the default and toss away these increased levels of security with a simple edit to the /etc/samba/smb.conf file to set security level=share
Thanks, **tact**! Just the basic sort of answer I was looking for.

Yeah; I appreciate that Gutsy Gibbon or Feisty Fawn will have a bit more under the hood. And while Gutsy does not need all the hardware MS Vista requires ("Ask not what Vista can do for you... ask what you can buy for Vista" -- Mac Ad "Podium") I get better performance from Feisty on my AMD Athlon XP box.

According to my client, these machines were purchased for corporate reasons about 6 to 7 years ago. I'm sure they had a lot under the hood **then**. But now? Well, I guess I'll see in about 10 hours or so what I'm up against. ;-) And I will report back.

---

