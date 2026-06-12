---
title: "connect to ftp server over lan"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by aaronp on 2008-05-10
All,

More of a networking problem than anything specifically Ubuntu.

I have a DLink DI-524 wireless router connected to a Belkin wired internet DSL router which is connected to my ISP. I have my desktop PC (running Ubuntu 8.04) connected to the Dlink via ethernet cable and a laptop running WinXP Pro which connects to the Dlink wirelessly.

I have the desktop assigned a static IP (192.168.0.166). The laptop obtains IP via DHCP (currently 192.168.0.191)
I can ping both ways with success.
 
I have used Samba to set up a share folder on the desktop PC but cannot map a drive to it on my Windows laptop. Assuming I had not set up Samba properly I used vsftpd to set up a simple ftp server and verified that it was functional by typing [ftp://192.168.0.166](ftp://192.168.0.166) into the desktop PC (the PC it is running on)
It opened up the ftp site no problems.

Trying the same thing on the laptop finds nothing. Is there something fundamental I am missing which is stopping the two machines from talking over the LAN?

thank you
Aaron

---

### Post by superprash2003 on 2008-05-10
are you using firestarter or anything of that sort? it could be blocking the connection

---

### Post by aaronp on 2008-05-10
yes firestarter was the problem. can't believe i didn't think of that!! :lolflag:
thanks very much.

can i add some rules to firestarter to allow connections from the lan whilst still maintaining the same security on the wan?

thanks
Aaron

---

### Post by aaronp on 2008-05-10
ok i worked out that if i just assign a static ip to the laptop and add this to the rules for firestarter i can still connect.

my next questions - samba.
ftp is a bit restrictive (having to connect and log in all the time) so i was hoping to actually map my linux partitions as network drives on the laptop.
on the first attempt i changed my laptop settings to create a workgroup and i lost access to my work domain which is very undesirable! (i fixed it by using system restore!)

wondering if i can just set up samba shares and then map them on windows like this: ```
//192.168.0.166/share
``` or if I actually need to configure samba's conf file correctly? I obviously can't use a workgroup for this so how would i get around that?

thanks again
Aaron

---

