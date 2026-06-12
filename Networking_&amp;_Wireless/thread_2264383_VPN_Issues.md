---
title: "VPN Issues"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by Richard_Whittaker on 2015-02-07
Greetings:

I have a site to site VPN setup between my primary location, and an off-site location using OpenSwan. Traffic from here to there seems to work fine for a Windows 2003R2 server, and a CentOS guest that work just fine. I can SSH from the CentOS server to an Ubuntu 12.04 server on my "local" network no problem. 

I am running into issues with connecting anything TCP based from my local network to Ubuntu 12.04 servers on the remote network. These seem to be the only servers I have issues with. 

I can ping the servers no problem, even with large packets. 

I cannot do anything involving TCP to them from my local site. If I am on one of the CentOS guests on the remote site, I have no issue connecting to the Ubuntu servers through SSH or any other TCP protocol. 

I'm really stumped! I would appreciate any help anyone can offer.

Thanks in advance,
Richard

---

### Post by gordintoronto on 2015-02-07
It might help if you were really specific about what you do, eg what commands you use.

---

### Post by Richard_Whittaker on 2015-02-08
I have the following setup:

               [TABLE="width: 700"]
[TR]
[TD]Local network:[/TD]
[TD][/TD]
[TD]Remote Network:[/TD]
[/TR]
[TR]
[TD]192.168.0.0/18[/TD]
[TD][/TD]
[TD]192.168.64.0/18[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]<==VPN over public network==>[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]db1 (Ub 12.04.05)[/TD]
[TD][/TD]
[TD]db2 (Ub 12.04.05)[/TD]
[/TR]
[TR]
[TD]www1 (Ub 12.04.05)[/TD]
[TD][/TD]
[TD]www2 (Ub 12.04.05)[/TD]
[/TR]
[TR]
[TD]dc1 (Win2003 R2)[/TD]
[TD][/TD]
[TD]dc2 (Win2003 R2)[/TD]
[/TR]
[TR]
[TD]mail1 (CentOS 6) [/TD]
[TD][/TD]
[TD]mail2 (CentOS 6)[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

I can ping db2 and www2 from any host on the local network, including with large packets. 
I can SSH from mail1 to mail2 without issue.
I cannot SSH from mail1 to db2. 
I also can't establish a complete MySQL connect from mail1 to db2. 
I can SSH from mail2 to both db2 and www2. 

The issue SEEMS to be TCP traffic from the Ubuntu hosts on the remote network. 

Any insights would be much appreciated. 
Thanks,
Richard.

---

### Post by Richard_Whittaker on 2015-02-12
Some more background on this issue to hopefully zero in on a solution. 

My Ubuntu 12.04 VMs are running Kernel 3.13. 
My CentOS VMs were actually 5.x, 5.10 for one of them, and I just built a brand new 5.9 VM in the 192.168.64.0 subnet, and was able to SSH to it immediately. I notice the CentOS 5.9/5.10 VMs are running kernel 2.6.18, which is admittedly old, but it lead me to wonder what differences might exist in the network settings between 2.6 and 3.13 that might be causing this issue, specifically what TCP options, since I am having issues with TCP specifically.

Am I hitting TCP forgery protection with tunnel traffic? Is there something else afoot?... 

My Wireshark dumps of an SSH session from one 12.04 server to another over the VPN show the connection, and the key exchange, and then everything just stops dead, so traffic is being passed.
When I try a MySQL connection from one 12.04 server, I get the initial dialogue, and can log in (and see that on the Wireshark capture, but as soon as I try to do something like connect mysql, the local client freezes, and nothing happens. 

I'm thinking about trying something UDP based  like NFS next to further narrow down if it's a TCP issue only. 

As per above, I can ping from any server to any server, even with large packets. 

Looking for any thoughts or assistance. 

Thanks,
Richard.

---

### Post by Richard_Whittaker on 2015-02-12
My NFS session over UDP worked, and I was able to transfer a 950KB file from the Ubuntu 12.04 server on the remote network to a server on the local network.

---

### Post by Richard_Whittaker on 2015-02-23
Bump... I guess I will trying random stuff to figure it out.

---

