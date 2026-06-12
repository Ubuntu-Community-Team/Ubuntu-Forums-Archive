---
title: "etho not connecting to firefox"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by mtedad on 2006-09-30
need a way to test this interconnect----pings all day. third try at trying to raise a guru.] thanx

---

### Post by kipeloff on 2006-09-30
Actually, I cannot understand the problem from your description, probably you can provide more detailed information about the current issue.

---

### Post by mips on 2006-09-30
disable ipv6

---

### Post by mtedad on 2006-09-30
need mo info..... system 2gig proc. asus a8v-mx motherbd. unbuntu 6.06 breezy==install  eth0..active propertys--connection enabled, static ip, ip add=74.135.68.74 subnet 255.0.0.0 , gateway =192.168.0.1   dns servers 74.135.68.74,   hosts 74.135.68.74.1   n/w tools shows devices --ip info-- ipv4 74.135.68.74 netmask=255.0.0.0  brdcast =74.255.255.255 under scope  there is no link........ the link is onthe ipv6 protocol
interface info hw add.00:15:f2:30:73:dd ,,...blah blah....
state active. ping ippdovider  100%return can't seem to ping my router today.sudo dhclient reinitalized router...... in terminal sudo dhclient returns can't ping router ,,,no working leases ----=sleepi if you would like more info just ask this linux is just a wealth of info...thanx

---

### Post by chele on 2006-09-30
Dude, this is Linux for Human Beings.  Forget the terminal, that is so redhat last century. You have lost your connection to the Internet, right?

Just click System > Administration > Networking. Enter your normal user password in the prompt. 

Select the connection you want to use, then [Properties] 

Make sure it is set to DHCP. Click [OK] then [OK] again. 

There will be a pause while the system sets up the network connection to your router. 

Now open Firefox and browse the World Wide Web to your heart's content. :)

---

### Post by mips on 2006-10-01
Please paste your responses a bit better, they are hard to read.


What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.
[I]
If you are dual-booting install the **ext2ifs** driver in windows and access your ext2/3 partions in linux from windows if you want to transfer data across in order to paste here. Alternatively use a usb memory stick or stiffy disk.[/I]

---

### Post by mips on 2006-10-10
You never came back, gave up ?

One of your other posts mention you have a D-Link router which might be part of the problem.

---

### Post by dannyboy79 on 2006-10-10
Mips may be right, we dealt with another user who couldn't figure out why he couldn't get online when he was actually getting an ip from the router. well it was because the router was handing out invalid ip addresses. it was weird cause breezy had worked with this invalid ip as well as winxp worked with this weird ip. so when in doubt, make sure your router is handing out 192.x.x.x or 10.x.x.x ip addresses to your lan. also try disabling ipv6 like mips says.

---

### Post by mips on 2006-10-10
The D-link issue sometimes extends beyond IP address issues. In some case a upgrate to V2+ firmaware is required on the router.

---

