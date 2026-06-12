---
title: "Network with Windows XP and Ubuntu"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by mosquetero on 2009-09-10
Hi!

I want to connect one Ubuntu machine to one Windows machine. I use an ethernet cable to connect both. My Windows XP computer gets an IP address but my Ubuntu machine does not get any address in the eth0 interface. Why?? Can you help me please??

Thanks

---

### Post by Zzl1xndd on 2009-09-10
Could you elaborate on how you have these machines hooked up, Are you using a Router or are you plugging the Ubuntu machine into a second Ethernet adapter on your Window machine?

---

### Post by LowSky on 2009-09-10
you cannot just plug an ethernet cable directly into another machine it will  not work... for that you need a crossover cable or a router

---

### Post by mapes12 on 2009-09-10
As LowSky says you need to connect the machines in that configuration. To check they have valid IP addresses then in Ubu Terminal ```
ifconfig
``` and in windoze ```
Start>Run>cmd>ipconfig
``` and you should see the IP addrsses assigned usually starting with 192.x.x.x The numbers must be different. What they are is irrelevant.

When you have done that you need to go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan" 

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

EDIT - If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

---

### Post by mosquetero on 2009-09-10
Thank you everyone. I am connecting directly both computers and that can be made since when I was running WIndows XP on both it worked perfectly. I had 192.168.0.1 in the first one and 192.168.0.2 in the other one. The problem appears when I change to Ubuntu. It can't take any IP address, which is quite logic since there is no router doing that job (using DHCP, ARP or other protocol). My question regards why can I do it with WIndows but I can't with Ubuntu??? Is it any possibility of connecting both computers in Ubuntu without having to use a router or HUB or switch??

ThAanks

---

### Post by Zzl1xndd on 2009-09-11
Do you have Internet connection sharing set up? (Or is your intent to even share an Internet connection?) If it is the this might be of use.

[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

---

