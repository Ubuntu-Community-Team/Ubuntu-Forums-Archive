---
title: "Home LAN set-up issues"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Cornbreadly on 2008-01-06
I am trying to set-up a home lan with two ubuntu pcs.

I have attempted a few of the methods described and have run into a few issues.  I decided on NFS because I finally have no real reliance on windows.  I believe I have the NFS server portion completed.  I was able to successfully share items with the GUI admin>shared folders.  They are both marked NFS.

I was also able to download, install, and restart my nfs server in the terminal without error.

On the client machine, I still cannot see the network.  I installed the client side stuff needed there, and am still unable to find my shared files.  I should be able to see them without altering fstab right?

I also tried autofs on the client side but that did not produce anything.  According to this [thread]("http://ubuntuforums.org/showthread.php?t=249889&page=20"), i think i have some work todo.

But from what I can tell, most of these rely on a set-up that has static ips for all of the machines.  My router is crap and does not reserve ips for specific machines.  Its either DHCPserver or bust.

I can turn that off I believe and set-up each machine with its own static ips i think, but I like that people who come over with their laptops can just log in with my password, and not reconfigure their connections.  With Vista, you cant do that without navigating about 5 mins of warning screens and turning off the ip6 functions.  Too much hassle.

All i want is for one pc to have read/write to a home folder under an environment where the ip may not be known.

---

### Post by Cornbreadly on 2008-01-06
to add a point...

When I say that i tried some of the above methods, all I am really saying is that i enjoy copying and pasting.  Things with linux have gotten so good that most of the time that is all you really have to do to add some type of specific functionality.

I don't think I would have fooled anyone into thinking I knew what I was doing with the previous post but I thought it might be important.  I may have missed a crucial step.

---

### Post by Cornbreadly on 2008-01-07
Any thoughts on the best way to set up nfs on a home lan with dhcp ip addresses handled by the router?

---

### Post by Cornbreadly on 2008-01-07
I am still no where without assistance.  Please help.

---

### Post by ModelM on 2008-01-07
You should be able to assign static addresses without changing or disabling your routers DHCP service. You simply set up whatever machines you want with a static address and when they connect to the network, they decline an assigned ip.

In my network DHCP is turned on but I have one machine with a static address. It is the machine the printer is connected to & it's locked to 192.168.0.42. So when you bring your laptop over, the network DHCP will assign your machine an ip & make you feel welcome but, if you need to print, you will always know exactly where the printer is.

Anyway, my point is that you should be able to assign static addresses to whichever machines you want without turning off DHCP.

---

### Post by Herman on 2008-01-07
Well, I was looking at your thread yesterday, but I didn't reply because you're asking about how to set up a home network using nfs.
I don't know anything much about nfs, I had a look at a tutorial about it and it looks pretty complicated to me. [Linux NFS How-To]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html").

Would you like to take a look at an easier way to set up your home LAN for now and maybe come back to nfs later if you still need it?
I'm working on a web page that's about SSH home networking. It's a lot simpler to set up, probably it'll only take you an hour or something. 
My page is just s simple page to try to show people how to get it up and running as quickly and easily as possible to begin with.

You'll still need to set static IP addresses, I had a router like that too. 
My new router automatically takes care of assigning a random IP to the mac address of any machine I plug into it and as long as I don't reset the router it'll remember it forever and keep the same same IP for each computer at each startup.
The old router used to allocate IP addresses beginning from 192.168.1.100 in the sequence the computers were booted in. 
Is that what yours is like? Setting static IPs fixed it. SSH doesn't like any changes in the network, if it expects an IP to match a certain details and it doesn't, then SSH will refuse to connect. To fix it you just delete the .ssh directory and make a new connection after a reboot. So it's easier to set a static IP for each computer. If you have that kind of a router.
Apart from that I think SSH is about the simplest to set up.

Take a look if you want. [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")

I understand if you're only specifically wanting nfs for some reason though.

I'm wondering what nfs can do that SSH can't though. I've never tried nfs, so I don't know how they compare. 

Regards, Herman :)

---

### Post by Cornbreadly on 2008-01-10
Finally got around to fixing it.

Thanks for the deeper understanding about the router's DHCP server function.  I was lost while thinking that it was static ips or dhcp.  Everything fell into place after that and a network is up and running.  Thanks

---

