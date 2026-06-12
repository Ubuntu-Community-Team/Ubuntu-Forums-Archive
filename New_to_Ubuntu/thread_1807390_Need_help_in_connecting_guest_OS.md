---
title: "Need help in connecting guest OS"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by ItBala on 2011-07-19
[SIZE=2]Hi

I'm running  ubuntu 10.10 in as host OS and installed two virtual machine [/SIZE][SIZE=2]via Virtual box 4.0 [/SIZE][SIZE=2]with CENTOS 5.3 running on it 

if i'm configuring Network Adaptor as "NAT"...I'm able to ping my host machine from guest os and vise versa .... also Internet is working fine from guest os when the network Adapter is running in this mode.
But i'm not able to ping the other virtual machine from the first one and vice versa...

If the network adaptor is configured as "Bridged Adaptor" .. I'm able to ping the between the virtual machines but the connection to host os and Internet are not working ...

I want to ping between virtual machies also i should be able to connect to host machine as well as to the internet from any of my guest os....

Please help me in achieving the same... [/SIZE]

---

### Post by Cybie257 on 2011-07-19
Virtual-box has been having issues with Bridged Networking, so NAT is the only thing available for internet sharing (on the latest releases). There are some 'hack' fixes on Google, but they seem a bit advanced if your not familiar with certain aspects of networking and some coding. I heard that people are reverting back to the first release or two of the 4.xx version and that Bridged networking was functional. It's the latest releases with this problem. Apparently Oracle doesn't seem to fully test their new releases to well, in my opinion, and it makes things difficult. But, how much can we complain, as it is free and works almost as good as VMWare, which costs a bundle and also has it's issues. 

So, for now, if you want to try to use bridged networking, where you can ping across and use internet at the same time, I would suggest getting an older copy (say V4.0.2). This was one version I recall with working Bridged Network via some forum talk. It might be a trick to find this particular one, but check the archive section of virtualbox.org and see what you can find. 

-Cybie

---

### Post by linuxman94 on 2011-07-19
Did you set the adapter you want the connection to be bridged to?

> To enable bridged networking, all you need to do is to open the Settings dialog of a virtual machine, go to the "Network" page and select "Bridged network" in the drop down list for the "Attached to" field. Finally, select desired host interface from the list at the bottom of the page, which contains the physical network interfaces of your systems

For more info about networking in virtualbox, see here:
[http://www.virtualbox.org/manual/ch06.html]("http://www.virtualbox.org/manual/ch06.html")

---

### Post by ItBala on 2011-07-19
Thanks for the reply ...

So you mean say this might work with older version of Virtual box right...

Actually i'm trying to simulate the oracle 10g R2 rac setup with these virtual machines setup....

here i need to  create a shared disk storage via virtual box on the host machine and it should be accessible by both the guest machines at the same time ....i think creating shared disk storage is not available with previous version virtual Box ... :-(

---

### Post by Cybie257 on 2011-07-19
> **ItBala said:**
> Thanks for the reply ...

So you mean say this might work with older version of Virtual box right...



Yes, from what I have been reading, that is the case. I found that out (but, yet to test it) after I came across the non-working bridged networking, which is something I need, but can get away without having until I get further in my project, so hoping another release comes out that fixes the problem.

> 
here i need to  create a shared disk storage via virtual box on the host machine and it should be accessible by both the guest machines at the same time ....i think creating shared disk storage is not available with previous version virtual Box ... :-(

Interesting, I will have to look into this. If what you mean by shared is that the disk is 'mounted' in each VM, then I'm not sure how that would be possible because it would create a conflict with the read/write operations. If it's sharing them like in a virtual NAS environment, I can see that working. I'm going to have to look into that. :)

-Cybie

---

