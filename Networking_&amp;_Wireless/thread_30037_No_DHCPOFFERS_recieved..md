---
title: "No DHCPOFFERS recieved."
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by imaek on 2005-04-27
Earlier today, I had to hook many other computers up to my network and fiddle around a bit with some port-forwarding. I didn't do anything drastic.


During all this, I had to unplug my ethernet cable from the back of my computer (while it was off), and plug it into a different computer.  When I plugged it back in and restarted it (first into windows, then into Ubuntu), the internet wouldn't work.  I watched a bit more closely and I saw that it says "DHCPDISCOVER on eh0 to 255.255.255.255 port 67 interval 6" (first time), and checked my router.  I have a Linksys router, and on the "Setup" page the only number close to 255.255.255.255, is 255.255.255.0.

I wonder if that has anything to do with it, and, if so, how to change it so it DHCPDISCOVERs to 255.255.255.0.


I am currently on a different computer (on the network; running Mac OS X) which works fine.


Also, if I boot into Windows XP, it just keeps going between "A cable has been unpluged", "Aquiring IP address" and "There is limited or no connectivity."


Please help. Any would be appreciated.

Thank you,
imaek.
[email]imaekphp@gmail.com[/email]

---

### Post by ape on 2005-04-27
there are a couple of things to note here:

1. Ignore the difference between the 255.255.255.255 from your computer and the 255.255.255.0 on the router.  These are correct and you don't have to change anything.

2. I'm assuming that your router is the device that is handing out the DHCP leases, correct?  If so, how many computers is it configured to handle?  I'm not sure exactly how many "many computers" is, but if you've connected more than your router is configured to handle, you may need to increase the number.

3. Does the router have any logs that you can look at to determine if it is getting a proper DHCP request from the computer?

---

