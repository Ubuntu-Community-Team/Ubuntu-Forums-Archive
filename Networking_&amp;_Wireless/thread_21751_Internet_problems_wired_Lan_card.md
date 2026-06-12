---
title: "Internet problems wired Lan card"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by ptsenior2000 on 2005-03-23
I'm having problems connecting to the internet using my wired lan card.  I have a Toshiba 4300 Satellite Pro notebook.  The drivers seem to appear when I do an lsmod (3c574_cs) and it recognizes the eth0 device, but I can't seem to connect to the internet.  Before, I tried a dhcp as my ISP has said that the Cable Modem should automatically assign an IP address.  However, I tried to manually configure it with 192.168.1.0 as the IP and using 255.255.0.0. as the gateway address to no success.  I didn't set up the dsn servers or anything else as I don't know what to put in for those fields.  At the install, it recognized my lan card and installed all the drivers, however like I said, it couldn't set up with DHCP.  Can anybody help me out?

---

### Post by Mr Black on 2005-03-23
are you running any sort of router at home or is your laptop connected directly to the cable modem?  If your not running a router with NAT and DHCP enabled you won't be able to use a 192.x.x.x address.  This address segment is for running private networks and isn't routable on the internet.  

If you want to set the information manually for your eth0 device you will have to contact your ISP to get the correct info that should be in the DNS and Subnet fields.  

I would try to set the device to automaticlly obtain the info via DHCP.  Then try using the *ifdown* and *ifup* commands to restart the connection.

---

### Post by ptsenior2000 on 2005-03-23
How would I go about doing that?  I called my ISP and they said I will be assigned an IP Address automatically.  When I enable DHCP, it will simply deactivate after about 4 seconds.  What I am getting from your post is I should do the following:

1. sudo ifdown eth0
2. sudo ifup eth0
3. enable DHCP
4. It should work

Is that right?

Edit: I forgot to mention that yes, I am using a cable modem connected directly to my lan card on my laptop.

---

### Post by Mr Black on 2005-03-24
if you are going to setup DHCP your should do it in the following order:

1) Go into Computer->System Configuration->Networking and then enable DHCP for eth0

2) Issue the command *sudo ifdown eth0*

3) Wait for a sec for the command to execute and take effect

4) Issue the command *sudo ifup eth0*

5) Wait a sec for the system to attempt to grab the settings

6) Issue the command *ifconfig* to see if it grabbed anything

One other thought that I just had.  I know for a fact that some ISPs only allow you to register two different MAC Address with their system.  I had this issue when I first got Road Runner.  I would switch between my desktop and laptop all the time and then I got a new NIC for my desktop and it wouldn't work.  I spent some time trying to figure it out and then one of my friends, who happen to be working for Time Warner doing Road Runner setups at the time, told me that you only get two registered MAC Addresses with their system.  I called the support line and had them clear their MAC cache and restarted my cable modem and I was up and running.  From then on I have been using a router so this won't happen (as well as the benefits of a router in general).

So if there is anyway that you might have had more than two NICs plugged into the connection you might want to try that as well.

---

### Post by ptsenior2000 on 2005-03-25
Thanks for the response, I'll try that tonight.

---

