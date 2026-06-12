---
title: "Virtualbox not picking up wifi"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by Nick_Ridley on 2014-02-04
Hi

I have just decided that I need to install itunes some how on my machine so decided to go down the virtualbox route with xp.  Windows works fine in virtualbox but it does not want to pick up my wifi network.  Any suggestions would be most welcome.

I have tried the NAT settings under all variants but still to no avail.

I am running ubuntu 12.04.

---

### Post by TheFu on 2014-02-04
Virtual Machines don't see the real hardware, they only see "virtual hardware". Most of the time, the Intel PRO/1000 card should be selected to be emulated for Windows client VMs.  Then ,in the VBox settings for the specific VM, select the physical network card and be certain to check the "cable connected" checkbox.  
I hope that makes sense.  Inside XP, only the PRO/1000 NIC will be seen. .... oh - you are running WinXP?  That sucks - you'll need to get the Intel PRO/1000 driver installed before switching over. It is NOT included in the normal XP.  Or you could use a less capable virtual NIC for XP - all the other choices don't perform very well.

---

### Post by brokenhachi on 2014-02-04
I haven't used vbox in years, but you should be able to use a bridged interface. Basically what that means is that you connect to the wifi on the host machine, then virtually attach the nic directly to the wifi network via the physical NIC, and receive a separate DHCP address, or static if you set it so.

The only way you would be able to physically use the wifi network inside the vm would be if you have a VTd compatible processor, and do virtual passthrough to pass control of the physical wifi card to the vm... though i dont think this is a feature of any type 2 hypervisors.. (type1 can do it).

---

### Post by Nick_Ridley on 2014-02-06
Thanks for the responses.

I think it was te fact that I didn't have the box "cable connected" selected....

---

### Post by TheFu on 2014-02-06
> **Nick_Ridley said:**
> I think it was te fact that I didn't have the box "cable connected" selected....

We've all been there.  Thanks for saying what it was. 
Could you please mark the **thread  as "solved"** so others don't look unless they want the solution?

---

