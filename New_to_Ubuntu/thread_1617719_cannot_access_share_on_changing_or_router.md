---
title: "cannot access share on changing or router"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by yankysunny on 2010-11-09
Hi,
I recently shifted to a new house. I was using a netcomm wireless router before with a laptop running Ubuntu 10.04 and a PC runing windows XP.
My ISP told that we have to change the router and then they installed netgear wireless router. The only thing wonders to me that a new black color thick cable runs from the router to the wall. I surely know it is not a cable connection
But anyways the problem is that I use to share folders on my XP .
But now I can only view the workgroup(MSHOME), and when I go into it. It says failed to retrieve the mount after taking about 5 min.

---

### Post by spiky001 on 2010-11-09
Do both machines have ip address can you ping them? can you acsess internet with both

---

### Post by yankysunny on 2010-11-09
yes i can ping them..
can access internet from both of them

---

### Post by spiky001 on 2010-11-09
I,ve not got a win machine connected at moment but can you type in nautilus adddress bar smb:// ip address ( if i,m wrong someone correct me)

---

### Post by yankysunny on 2010-11-09
Thanks but it shows nothings..
is its "smb" related to samba somehow because i have not installed samba in my ubuntu

---

### Post by SuaSwe on 2010-11-09
So to clarify, are you able to ping PC A from PC B and vice versa? Did you have any network configurations (bridged connections and so on) that relied on both PC's being on a certain subnet, say 192.168.1.1? NGs are usually 192.168.0.1 so that will need to be changed should that be the case. 

You should also be able to connect your old router to this new NG contraption - I too was given one of those and managed to link it up to my Linksys originally, although in the end decided to surrender and just go with the NG. :D

---

### Post by yankysunny on 2010-11-09
> **SuaSwe said:**
> So to clarify, are you able to ping PC A from PC B and vice versa? Did you have any network configurations (bridged connections and so on) that relied on both PC's being on a certain subnet, say 192.168.1.1? NGs are usually 192.168.0.1 so that will need to be changed should that be the case. 

You should also be able to connect your old router to this new NG contraption - I too was given one of those and managed to link it up to my Linksys originally, although in the end decided to surrender and just go with the NG. :D
Yes u r right. my netgear is on 192.168.0.1.(But does this makes any difference?)
I will try to change it to 192.168.1.1
How do I connect them to each other(ethernet cable?)

---

### Post by SuaSwe on 2010-11-09
You won't be able to change the IP of the NG, if it's the same as the one I have (sadly - I tried this myself but no joy!); what you need to do is adapt the rest of the network to sit on the subnet 192.168.0.0/24 instead of 192.168.1.0/24, which is quite possibly what it was at before. 

To connect your old router to the NG you want to disable the wireless on the NG (might as well!), then connect the two using an ethernet cable between the WAN port on the old router to one of the LAN ports on the NG, if I recall correctly. I do believe I also had to jump on the NG and the Linksys to fiddle with things like NAT and DHCP to get it to work, although I can't remember exactly what I did! The easiest solution would probably be to keep the NG as the only routing device.

---

### Post by yankysunny on 2010-11-12
i tried changing the subnet to 192.168.0.0/24 but still i cannot access the network share.
Nautilus display the workgroup and when i double click on it. it says failed to mount
"Unable to mount location"
Failed to retrieve share list from server"

---

### Post by yankysunny on 2010-11-16
I got one way around
from terminal I run nautilus smb://192.168.0.10/ and here we go... I can open the share.
But I wonder why it does not work directly from the network

---

### Post by pricetech on 2010-11-16
You probably have the old IP address cached somewhere as belonging to that machine name.  I quit using names for that very reason.

Your router should allow you to reserve IP addresses according to the MAC address of the computer.  The feature is quite handy and I suggest using it.

---

### Post by yankysunny on 2010-11-16
> **pricetech said:**
> **You probably have the old IP address cached somewhere** as belonging to that machine name.  I quit using names for that very reason.

Your router should allow you to reserve IP addresses according to the MAC address of the computer.  The feature is quite handy and I suggest using it.

That may be the reason, so where should I go to update that value.

Yes I think reserving the IP would be a nice option but every time I have to write that same command naultius (IP address)

---

