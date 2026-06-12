---
title: "Another annoying networking problem"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Catsworth on 2007-06-25
Ok, my laptop is currently connected wirelessly to router#1 and everything is working fine.  If I browse to 192.168.1.1 I am taken to the admin config page for router1.

Now I disconnect from router#1 and then connect via ethernet to router#2, my ethernet is set to obtain an IP via DHCP and the router is set to supply one.  When I connect I get a valid IP address, and the gateway and DNS settings are right.  When I now browse to 192.168.1.1 I should get the config page for router#2, instead I just get a 404 error (eventually).  If I try to ping the router I get a 'destination_unreachable' error.

So, I give up with the wired router, disconnect the ethernet, and turn the wireless back on.  Then I realise that I now cannot connect to the wireless router, when I do my CPU usage jumps to 100% and the connection simply fails.

I reboot the laptop, and immediately upon logging in the CPU usage jumps to 100% and I still can't connect.

This continues through every reboot.

The only way to solve it is to physically disable the wireless card while the laptop boots, and once it's finished booting and everything has settled I can turn the wireless card back on and everything works ok.

I would like to be able to switch seemlessly between the ethernet connection and the wireless connection, disabling one and re-enabling the other, but every time I do this I get the problems I'm describing above.

Does anybody have any idea what might be causing any of this?

Thanks.

---

### Post by PgR on 2007-06-25
Sorry - no ideas just yet, just some questions to help get a better idea.

1) Do you really get a 404? (Or does it just time out?)

2) Are they two different routers? Or are you connecting to the same router via wireless and ethernet? Does the ethernet router have a firewall preventing ping replies?

3)  What's the ip address / mask / gateway you're given by DHCP on the ethernet?

4) Once you've got an address via ethernet, what's the result of "route"? (open a console and type route)

---

### Post by p_quarles on 2007-06-25
I can only think of a couple things, and I doubt either of them will help much: 1) Is the laptop in roaming mode when you make this switch? 2) Have you doublechecked that router #2 is using a category D (or whatever it's called) IP address range? I ask just because I can easily imagine something like that happening if it's looking for a 192 address and the router is actually at 172.

---

### Post by Catsworth on 2007-06-25
> **PgR said:**
> Sorry - no ideas just yet, just some questions to help get a better idea.

1) Do you really get a 404? (Or does it just time out?)

Ok, I'm using Firefox, so I actually get an 'Unable to connect' message

> **PgR said:**
> 2) Are they two different routers? Or are you connecting to the same router via wireless and ethernet? Does the ethernet router have a firewall preventing ping replies?

Two different routers.  The router does have a firewall, but it doesn't prevent ping replies.

> **PgR said:**
> 3) What's the ip address / mask / gateway you're given by DHCP on the ethernet?

192.168.1.100 / 255.255.255.0 / not sure to check what the gateway would be

> **PgR said:**
> 4) Once you've got an address via ethernet, what's the result of "route"? (open a console and type route)

```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

> **p_quarles said:**
> I can only think of a couple things, and I doubt either of them will help much: 

1) Is the laptop in roaming mode when you make this switch? 

It's in whatever mode it would normally be in.  I don't think it has a 'roaming mode' specifically.

> **p_quarles said:**
> 2) Have you doublechecked that router #2 is using a category D (or whatever it's called) IP address range? I ask just because I can easily imagine something like that happening if it's looking for a 192 address and the router is actually at 172.

Yep, it's definitely using a 192 address.  I've reset the router to default settings so the address on the router should be 192.168.1.1..


Thanks Guys :D

---

### Post by PgR on 2007-06-25
Hmmm... You say your IP address for the ethernet connection is 192.168.1.1, but the route table shows that as a gateway for both connections.  What's the output of ifconfig? (start a console, and type "sudo ifconfig") I suspect that your machine's ip address isn't in fact 192.168.1.1.

As I understand it, you have two different routers, with the same IP address, but obviously different MAC addresses, connected via different interfaces. That would explain the problem connecting to the router/internet. You could try ```
sudo ifdown eth1
``` or ```
sudo ifdown eth0
``` to bring down the interface you're no longer using when you switch them over. Bring them back up with "ifup"

But that doesn't explain why the wifi interface won't connect to the network...

Try ```
sudo tail /var/log/syslog -f
``` when you try to reconnect the wifi (use ctrl-c to finish it) that will show us what's going on a little more.

Of course, there may be a simpler way. As both interfaces are obviously connecting to different routers with the same IP address, it may be worth thinking about why you have two networks around with the same IP range.... Would it be feasible to use 192.168.<something_other_than_1>.x on one of them? Then I suspect this wouldn't be an issue.

---

### Post by Catsworth on 2007-06-26
> **PgR said:**
> Hmmm... You say your IP address for the ethernet connection is 192.168.1.1, but the route table shows that as a gateway for both connections.  What's the output of ifconfig? (start a console, and type "sudo ifconfig") I suspect that your machine's ip address isn't in fact 192.168.1.1.

Nope, the IP address of the web based administration page for the second router (and the first one) is 192.168.1.1.  This is the IP address of both routers.  Typing this in a browser when connected to the router should bring up the web page.

> **PgR said:**
> As I understand it, you have two different routers, with the same IP address, but obviously different MAC addresses, connected via different interfaces. That would explain the problem connecting to the router/internet. You could try ```
sudo ifdown eth1
``` or ```
sudo ifdown eth0
``` to bring down the interface you're no longer using when you switch them over. Bring them back up with "ifup"

Tried that.  With only the one interface up I still can't connect to (or ping) the router on the ethernet connection.  

> **PgR said:**
> ]But that doesn't explain why the wifi interface won't connect to the network...

Nothing wrong with the wifi interface.  The problem occurs when I disconnect from the wireless connection and plug into a different router via ethernet.

> **PgR said:**
> Try ```
sudo tail /var/log/syslog -f
``` when you try to reconnect the wifi (use ctrl-c to finish it) that will show us what's going on a little more.

I'll give that a go a little later, thx.

> **PgR said:**
> Of course, there may be a simpler way. As both interfaces are obviously connecting to different routers with the same IP address, it may be worth thinking about why you have two networks around with the same IP range.... Would it be feasible to use 192.168.<something_other_than_1>.x on one of them? Then I suspect this wouldn't be an issue.

This is part of the problem that I'm trying to solve.  I would like to put some custom firmware on the second router, but to do that I need to be able to connect to the admin page.

Thanks for the help.

---

### Post by PgR on 2007-06-26
> **Catsworth said:**
> Nope, the IP address of the web based administration page for the second router (and the first one) is 192.168.1.1.  This is the IP address of both routers.  Typing this in a browser when connected to the router should bring up the web page. 

Well if your IP address and the IP address of your router are both 192.168.1.1 then that explains why you can't connect to it.

I'd check your IP address; if it's genuinely 192.168.1.1 then that's your problem.

---

### Post by Catsworth on 2007-06-27
> **PgR said:**
> Well if your IP address and the IP address of your router are both 192.168.1.1 then that explains why you can't connect to it.

I'd check your IP address; if it's genuinely 192.168.1.1 then that's your problem.

..........but my IP address _isn't_ 192.168.1.1

Both routers have this address for the administration page, and I'm not attempting to connect to them both at the same time, I'm disconnecting from one and then connecting to the other before attempting to access the setup page.

My IP addresses are:

eth0 (ethernet): 192.168.1.104
eth1 (wireless): 192.168.1.64

---

### Post by PgR on 2007-06-27
Ah, sorry... I thought you said your IP address was 192.168.1.1.

Oh, yes... you did ;^)
> 
Quote:
Originally Posted by PgR View Post
3) What's the ip address / mask / gateway you're given by DHCP on the ethernet?
192.168.1.1 / 255.255.255.0 / not sure to check what the gateway would be

Once you've disconnected your wireless and connected the LAN, we need to check your routing and arp tables. Could you post the output of 
```
route
``` and ```
arp -vn
```

---

### Post by Catsworth on 2007-06-28
> **PgR said:**
> Ah, sorry... I thought you said your IP address was 192.168.1.1.

Oh, yes... you did ;^)


Once you've disconnected your wireless and connected the LAN, we need to check your routing and arp tables. Could you post the output of 
```
route
``` and ```
arp -vn
```

Bugger, typo, sorry :(

Will do those tonight (if I don't get sent away with work) when I get home.

Thanks for the help :)

---

### Post by crashovaride on 2007-06-28
If it does help, try changing the ip address on the primary router. Sometimes forwarding on the router will also display the secondary network device / hardware firewall. If this helps. Had a similar problem.

---

### Post by Catsworth on 2007-07-04
Sorry it's taken me a while to get back to you, been busy with work.

Here are the outputs from the commands you asked for:

```
catsworth@laptop:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

catsworth@laptop:~$ arp -vn
Entries: 0      Skipped: 0      Found: 0
```

Any thoughts?

---

### Post by Catsworth on 2007-07-05
.....gentle bump.....

Anybody got any ideas?

---

### Post by PgR on 2007-07-05
Well that looks like it's all correct. How terribly odd.

If you're using DHCP and getting an address from 192.168.1.1 and that' being set up as your default gateway/route then I don't see why you can't ping it.

I take it that this second router doesn't have something silly going on; like an usual port for its web interface?  Can you access it from another machine? What model is it?

Try using wireshark (it's in the repos') to see what traffic you get when you attempt to connect over the LAN. I wonder if you're getting anything back at all... And have a try at telnet / ssh to the router too.

You've certainly found a good puzzle, if nothing else.

---

### Post by Catsworth on 2007-07-05
If I switch the router to DHCP, and run a LiveCD on this box which gets its IP from DHCP, then I can access the control panel without any problems.

This would seem to completely rule out any configuration problems with the router, or any hardware problems with the router/laptop.

This can only be a configuration problem within Ubuntu, and I'm starting to think I've got little choice left but to tear it down and start again.

---

### Post by PgR on 2007-07-05
Yep, I think you're right - it must be a config problem....

...Though as we've checked everything and it seems right, I can't think where to go now, beyond sniffing the traffic to see where it's going.

Good luck!

---

