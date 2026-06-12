---
title: "Netgear XE104"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Sgisler on 2011-02-04
Hi, completely new to Ubuntu. I have a winxp network at home which successfully runs wireless machines and wired. Wired by the Netgear XE104. I have just put Ubuntu 10.10 on an older laptop and downloaded all updates. I can get Internet connectivity and see the other machines from the Ubuntu laptop when connected direct to the router. However, when I try to connect thru the remote XE104 I get nothing. The Xe104's and computer connected to them have not required any manual configuration with the xp machines. 
Does anybody have any experience with such a setup?
Thanks!

---

### Post by shof2k on 2011-02-04
Hi,
Can you be a bit more clear on your set up.

Are you saying the Netgear XE104 is your router?

Can you connect using a cable (wired) and see the internet and other computers

Can  you connect wirelessly (remote?) and see the internet and other computers

---

### Post by Sgisler on 2011-02-04
Sure, thanks
The netgear is a remote connection (Ethernet over powerline). The Ubuntu laptop doesn't have wifi. But connects flawlessly directly cabled into my router (verizon fios). On the Ubuntu laptop, I can access the Internet and shared folders on the other networked machines. When plugged into the XE104, the Ubuntu laptop won't connect at all. Shows autoeth0 disconnected. Autoeth0 is the same connection that works just fine when U laptop is directly cabled to fios router. I'm sure I'm just missing something stupid, just not sure where to begin. I hope I'm being clear enough.

---

### Post by shof2k on 2011-02-04
OK thanks for clarifying that.  So ubuntu is working directly with your verizon router. That proves the internet and your Ubuntu laptop are working :)

This means the connection between the laptop and XE104 has the problem. Do you know the internal ip address of your router? (it's usually something like 192.168.0.1) If so, trying pinging that (open a terminal and type ping 192.168.0.1).

---

### Post by Sgisler on 2011-02-05
Yes, I have that info. So, I can try to ping the router even if U shows the wired connection as 'disconnected'?
I will try that Monday when I'm back in town and report back. Will try to include any error msgs I get.

---

### Post by Sgisler on 2011-02-05
Yes, I have that info. So, I can try to ping the router even if U shows the wired connection as 'disconnected'?
I will try that Monday when I'm back in town and report back. Will try to include any error msgs I get.

---

### Post by cjhabs on 2011-02-05
Do the router and Netgear switch auto sense the RX TX connections? Could it be the cable you are using? There are straight through and cross over cables - and some ports on switches/hubs are specific for connecting to other hubs/switches when cascading them.

Your error sounds like you have no physical connection.

---

### Post by Sgisler on 2011-02-05
Yes, the netgear adapter, when used with a windows machine, allows the computer to auto detect and connect to the router. It's only the Ubuntu machine that won't do so. The Ubuntu machine does think that there is no physical connection. I'm sure it's got to be something I'm doing or not doing. Unless there is some weird incmpatabilty between the netgear adapter and Ubuntu. Which is alot less likely than something stupid that I'm doing. 
When I'm back at home I will try to put together some more info.

---

### Post by Sgisler on 2011-02-07
well, ok. I don't know exactly what I did, but I fixed it. 
The Auto eth0 connection was default and connected automatically when plugged directly into the router. But, it would do nothing when plugged into the remote adapter (Netgear XE104). So, I created a new connection (called Powerline) and copied the MAC address from the Auto eth0 connection and pasted it to the Powerline connection and just like that it was connected. In fact, I'm posting this reply from the laptop on the new connection.
Again, I don't know the how or why, but it works and that's all I care about. (Actually, for knowledge sake, I would like to know the how and why!)
I sure appreciate the time and suggestions and any info on why my blind stumbling worked out for me would be read with relish!
Thanks!

---

