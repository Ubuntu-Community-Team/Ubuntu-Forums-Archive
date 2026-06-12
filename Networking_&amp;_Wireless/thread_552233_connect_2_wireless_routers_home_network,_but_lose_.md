---
title: "connect 2 wireless routers home network, but lose admin page"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2007-09-16
The issue is

I have a netgear wgt624 and I have a gateway wgr250
cable modem then wgt624 then wgr250

So I 
Reset the wgr250 to defaults
Set the wgr250 so that DHCP is turned off. (That means the wgt624 is assigning all the IP's.)
And plug the cable from the wgt624 into one of the 4 LAN ports of the wgr250.

This works, wireless and lan 
BUT I can not access any of the wgr250 settings from a web browser if DHCP is turned off on the wgr250.

It shows up as an attached device on the wgt624. And I have an IP adress to the device, but I can not ping it or open a web page to it. SO, I cant make any changes unless I then reset it using the little button on the back.

I would like to be able to gain access to it without having to a hard reset.
.
So, if anyone has an answer, Thanks!

---

### Post by sdowney717 on 2007-09-16
[http://www.dslreports.com/faq/12231](http://www.dslreports.com/faq/12231)

I found this, although I cant access the setup screen from the computer hooked up to router B and I dont have another cable long enough to reach. I assume most people can see access page from computer hooked up to router B

18. One problem though, and that is, any computers connected to Router A will not have access to the setup screen on Router B. Here’s how to fix that.

---

### Post by kevdog on 2007-09-16
I did the same configuration as you, except the second router in my chain was a wired router and not a wireless router.  What I had to do: was to set the local IP address of the first router (that would be the wireless router to 192.168.1.1) and the local IP address of the second router (the wired router to 192.168.2.1)

This was off course a little tricky to do, so when connecting from my computer to each router, I assigned my computer a static IP address within each respective subnet.

Ive always wondered if this would work for two wireless routers in series rather than a wired/wireless.  Im not sure if it will or not but at least its worth a try.

---

### Post by kevdog on 2007-09-16
Hmm, I just read your link -- wonder if that would work also!!

---

### Post by sdowney717 on 2007-09-16
I figured out something here.
put the ethernet cable from wgt624 to port 1 of the wgr250
plugged ethernet cable from computer to port 2
I set the wgr250 LAN to 192.168.1.50
I set the wgr250 DHCP to disabled

And it is working, I can bring up the admin web page off the computer that is attached to wgr250.
And I dont see the wgr250 as an attached device in the admin pages for the wgt624

Sine the wgr250 is no longer assigning IP, is it doing any routing such as If I set up port forwarding or blocking or is it now only a switch?

There is another setting under advanced where I could choose for the wgr250 to act as either a gateway or a router, should it be set to router and set RIP to enabled?

---

