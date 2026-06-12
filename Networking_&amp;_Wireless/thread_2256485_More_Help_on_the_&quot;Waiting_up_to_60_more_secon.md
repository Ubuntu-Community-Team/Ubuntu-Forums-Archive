---
title: "More Help on the &quot;Waiting up to 60 more seconds for Network Configuration&quot; bug"
date: 2014-12-12
forum: Networking &amp; Wireless
---

### Post by tim81 on 2014-12-12
I've read numerous post on many people having no luck getting the Network to configure on boot up. I've read many work arounds but most don't get the network to configure on bootup and none fix everyones problem.

I thought I would share some observations on when this occurs in my system so those smarter than I might have an epiphany and be able to once and for all figure out how to get the network to configure during the boot. I'm running a server without a display so I need it to boot with network connectivity without outside intervention.

I have 14.04 LTS installed with webadmin, and VNC running on startup.

If I unpower the system for any length of time(physically remove power from the power supply) and then plug the computer back in this problem will present itself. However, if I just issue a reboot command from Webadmin  it will reboot just fine and never lose network connectivity.

When I boot up after removing power from the system, I get the "waiting for network configuration" delay. I had a sneaky suspicion my router wasn't issuing an IP address fast enough and that was messing Ubuntu up. I issued the server a static ip in the router setup and retried with no luck. I still got the  delay. 

I have found that if you let it go thru the entire boot and fail to get network configuration that you indeed do not see the server in the router list of connected clients. It's as if the cable isn't even plugged into the router even though both the server NIC and the Router show a good cable connection on the status lights. Now if you quickly power on and power off the server (just using the power button in front) after you've let it fail to boot with network you can get the system to boot with network configuration.

I hope this jars someones neurons to fire and sparks a solution for so many people dealing with this problem

---

### Post by tim81 on 2014-12-13
To add some more information for others with the same problem to check. When my server boots up and I see a yellow light on the netgear switch port its plugged into (indicating fast ethernet connection) I get no network service. But when it boots up and I see the green port number light up on the switch (indicating a gigbit connnection) I get network connections. 

I wonder if the nic isn't powering up fast enough. Weird. Any smart people got any ideas?

---

