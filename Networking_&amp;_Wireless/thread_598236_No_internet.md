---
title: "No internet"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by normva on 2007-10-31
I installed ubuntu 7.10 and now i dont have internet. I didnt have internet in Live CD too. And there is a LED next to my network cable but its switched off. I  had internet in 7.04. Please help!!!

---

### Post by magordoom on 2007-10-31
i am having the exact same peoblem! did you check the help files,  to set up the network again? (didnt help me may help you)

---

### Post by normva on 2007-10-31
i checked info but no help
I think i dont have any proper network drivers. 


Still waiting for help

---

### Post by wirechief on 2007-10-31
I found that my /etc/resolv.conf file was not created even though I used the Network setup on the menu
it acted like it was doing something but it fails to do so also i had to put in a static ip, my essid, my gateway,
and broadcast ip's  what is with this gutsy, why after all this time it is unable to setup basic networking ?
I have a sony vaio pcg-v505EX that uses intel ipw2200 firmware.  I do not have this trouble when using
other debian distros like kanotix, sidux, or even rpm based distros like victor linux, it should not be this hard for users to connect to the internet.
I verified the md5sum on the download along with burning the cd using DAO and at 8x then i  checked the media again using md5sum /dev/cdrom all give the correct md5sum code so it is not the burn that is faulty.
Having to manually edit the /etc/network/interfaces  file and enter the information for the ip address's is re-diculous also having to edit the /etc/resolv.conf and put in the correct information for my dns servers
is something a newbie should not have to do.
Can someone explain this ?

---

