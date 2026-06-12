---
title: "Server 10.04"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by keithgroben on 2011-01-10
Hello there, I am an absolute beginner to configuring a server. I need to know exactly how to configure my server to connect to the Internet. I have static Ip service from my ISP. I have read forums, sites, etc. And followed the instructions, but still cannot get my machine to connect to the Internet. I think at the most confusing thing is that different posts advise configuring different files.

Any help at all is highly appreciated. I hope to use my server so I can run big blue button.

---

### Post by mcduck on 2011-01-10
Have you tried with the official Ubuntu 10.04 Server guide?

[https://help.ubuntu.com/10.04/serverguide/C/index.html]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

From the Network Configuration -section:
> Static IP Address Assignment

To configure your system to use a static IP address assignment, add the static method to the inet address family statement for the appropriate interface in the file /etc/network/interfaces. The example below assumes you are configuring your first Ethernet interface identified as eth0. Change the address, netmask, and gateway values to meet the requirements of your network.

auto eth0
iface eth0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.1

By adding an interface configuration as shown above, you can manually enable the interface through the ifup command.

sudo ifup eth0

To manually disable the interface, you can use the ifdown command.

sudo ifdown eth0


---

### Post by keithgroben on 2011-01-10
Thank you for your help. This is what I was looking for. It will take a lot of reading, but that's ok!

---

### Post by keithgroben on 2011-01-10
Thank you for the link. I've been reading the entire server guide through. My question wold be, do i need to set up server-side DNS?

I had to set this upon my router, but am thinking I will need to set this up on my server as well. I am only asking,because the guides a logical outline of what can be done. Are there other resources available thati can read to find this out?

---

### Post by drdos2006 on 2011-01-10
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by keithgroben on 2011-01-11
Thanks for your help on this. This is really helpful information.

---

### Post by drdos2006 on 2011-01-12
No problem. Please use the Thread Tools and mark this as solved. It helps others to see [SOLVED].

regards

---

