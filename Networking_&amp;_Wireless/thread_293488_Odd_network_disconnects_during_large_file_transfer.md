---
title: "Odd network disconnects during large file transfers (1.2-1.6G) Ubuntu 6.10"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by tonttu on 2006-11-05
Hi,

I installed Edgy Eft on my laptop last night. Works good otherwise, but I'm facing a strange network disconnection problem now when I'm trying to copy my files back to the newly installed machine.

The particular "problem file" is a 6GB file on a Windows SMB share. Trying to copy it through scp, sftp and Samba results in the network connection to be disconnected when the transfer is proceeding around 1.2-1.6 gigabytes.

I have tried smbclient gets from the Ubuntu machine (also through the Edgy network places explorer), scp push from the Windows machine, etc.

Copying the file with scp to /dev/null fails just like copying it to my home directory. Idle SSH session logins seem to prevail as normal, but something is cutting the file transfers.

It's always around the same 1.2-1.6 gigs when this happens, about five minutes in time perhaps. I haven't noticed any other networking problems so far. The connection is wired through the laptop's integrated NIC.

Hopefully someone has some clue about this ;) Thanks!

Tuomas

---

### Post by Marvil on 2006-11-05
Hi Tuomas , 
What kind of hardware are we talking about in the Ubuntu ,is this a new marvel NIC built in the Laptop. 
I have been having similar problems , my network connection is dropping with the new Edgy after a while. :-k 

Have been looking around on the net and there seems to be some problem with the drivers for gigabit cards that are built in the hardware and haven't found a solution on this yet. 
I have removed the IPV6 on the Eth cards. Didn't help me with solution. 
The only help i get is to restart the network after 1-2 hours :???: 

Are you able to borrow an PCMCIA card to test if the connection is holding? 
I will test with an old 3Com nic later tonight see if this helps me.

Cheers Marco

---

### Post by tonttu on 2006-11-05
Hello Marco and thanks for your reply,

No, the hardware is not blazingly new. It's a couple of years old compaq/hp presario 2500 with some national semiconductor adapter, device mgr shows device identifier DP83815. And its only 10/100, 100fdx negogiated.

Probably don't have any pcmcia ethernet cards anymore, but I can try via wireless lan connection tomorrow.

Light traffic connections are not disrupted, they seem to last for hours (ssh sessions sitting at the prompt). The connection survival time for high use connectins appears to be close to 10 minutes, the amount of data transferred by then varies slightly. But the throughput is not much, average 1.3 gigabytes per 10 minutes... Yes the laptop is slowish, 2.4G P4 or something, but still.

I have done my googling too, but haven't found anything appropriate so far.

Tuomas

---

### Post by tonttu on 2006-11-07
HEH! Now I am really amusing myself.

Finally took the time to start testing this file transfer through the wireless link. In effort to find the WLAN parameters I started to open the WLAN router's web based management only to realize that I had "randomly" chosen the same wired lan IP address for my ubuntu laptop as was  being used for the wireless base station. How professional is that ;)

Now after changing the laptop IP to something more unique, the file transfer is already at 2GB and climbing...

Not much of an Ubuntu problem after all.

Sorry for the confusion, -tuomas.

---

