---
title: "DHCP Server"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Atlanta-Mike on 2010-04-17
I am VERY new to Linux and Ubuntu (LONG time Windows user) and would describe myself as an above average Windows user.  Windows will most likely be my main OS for years to come, but I am trying Linux in several virtual environments.

What I am trying to do is move DHCP off my router for some time while I do some testing.  I think I have Ubuntu giving out IP addresses but the Client list is horrible in it's design and I am hoping someone can help me with a better program.  Currently, I am using GADMIN-DHCPD as my DHCP software.  If anyone has ever used pfSense for a firewall, I was hoping to get a client list that looked like the nice neat list pfSense provided, instead of a bunch of jumbled text provided by GADMIN-DHCPD.

Thanks for the help;

Mike

---

### Post by -humanaut- on 2010-04-17
Honestly I think you should give SmoothWall or Coyote linux a try Ubuntu probably isn't the best distro suited to Router/Firewall I have Solaris 10 acting as my current router/firewall

---

### Post by HermanAB on 2010-04-17
Howdy,

I would simply use the default dhcpd and configure it in /etc/dhcpd.conf.  It is really no big deal to set up.

---

### Post by Atlanta-Mike on 2010-04-17
I may not have described my setup correctly.  I am still going to use pfSense for firewall, I just wanted to move the DHCP server functions off the router for a while.  The reason is I have pfSense installed on a Xenserver (baremetal VM) and have several versions of pfSense which I may be switching between, plus I may give Smoothwall a try even though my long term firewall will be pfSense.  Having the firewall in a baremetal VM allows me to easily switch between router setups by just turning one off and another on.  However, this can cause problems with the IP addresses given to local machines.  I may be wrong, but I was hoping to solve this by moving the DHCP server off the router from time to time as I do testing.  Once I am done with my testing, I will move the DHCP server back to the router.  My initial testing may last a couple of months and then it should be rare.

HermanAB, where can I find the default DHCP server?  I looked for the file you mentioned, but it was not there.

---

### Post by Atlanta-Mike on 2010-04-20
I got DHCP to work, not a real problem to set up even for a Linux newbie like me.  However, I still think the reporting of DHCP leases is HORRIBLE.  This might have been fine back in the early 90's with DOS, but come on there must be a better GUI reporting tool than the crap text output that this progam is doing.  I want 1 line per DHCP list a a decent table format without me having to write a bunch of code.
 
Maybe I am using the wrong tool or should use something other than Ubuntu.
 
 
Mike

---

