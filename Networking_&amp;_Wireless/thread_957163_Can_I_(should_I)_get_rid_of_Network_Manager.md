---
title: "Can I (should I) get rid of Network Manager?"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by 5circles on 2008-10-24
As I read it, one of the causes or confusions of a network problem I'm having may be the Gnome Network Manager applet, so I'd like to get some device on how to deal with it.

Background.  My development machine has a problem with the onboard wired Ethernet.  It also no wireless.  When I figured out the problem (it was intermittent), I added a NIC.  I want this machine to have a static IP address, so I set it up that way.  But I can't disable the onboard NIC, and both show up as Roaming (looking at System | Admin | Network).  

I read that these kinds of issues are caused by the Gnome Network Manager Applet which is designed to be easy for laptops.  Can I just remove this applet?

I'm going to try to disable the onboard NIC in the BIOS, but I'd still like to get rid of the Roaming.

Thanks

---

### Post by theDaveTheRave on 2008-10-24
5circles,

have you been able to get the statip IP addressing to funcion?

I know that when I set up my laptop, and local server with static IP's I had real problems due to the Linux boxex piciking up different netmasks compared to the Mac OS and Windows (XP and Vista) that are in the office.

You can get the netmask from the <ipconfig> command, my issue was a change in this from 255.255.255.0 on other terminals to 255.255.255.128 on my Hardy Laptop and server!

I don't understand the reason for this but ?? hey

the underlying files that need to be worked on are:

/etc/netwok/config - the network manager directly adjusts this.

Copy the original file (which is basically just a list of the potential netorking interfaces and how they behave, there should be a copy of a "basic" one on the forums somewhere, unfortunately mine is all working and I never bothered to save the original! - not that I had any problems.

Once your new settings are good, make a backup, then de-install the "gnome network applets" via synaptic, if everything breaks (which it shouldn't) you'll just need to re-load the original backup, possible with a re-start of the pc in the "recovery" mode and then everything should be back to normal.... he says!

with regard to your NIC problem.

if you do the <ifconfig> it will show up all the avialable interfaces and how they are connected (I suspect that the on board card will be eth0, and your newly added card should be eth1.

you should be able to get  this information from an <lshw> then grep for network card or simliar (sorry I'm not very hot on "grepping" I tend to put the details into a file then open in Gnome and search in that way, not very clever by.... if works!

 If the onboard NIC isn't connected to anywhere it shouldn't cause you an issue.

from what I understand
If you use this terminal as a server, you can have it headless and then allow root access only via this particular ethernet port - forces the admin task to occur localy to the machine (good practice).

I don't know if this infor will help solve your problem? but good luck either way.

Dave.

---

### Post by 5circles on 2008-10-24
Dave,
I am able to get Static IP to work.  I was also able to disable the NIC in the Bios, so I've finessed the issue.  I would like to clean this up on this machine because I've had too many unresolved issues in the past, and end up rebuilding.  But I probably won't be able to go through all of your instructions for a few days.

Just to make things more complicated, I'm also trying to set up a laptop.  I think the Network Manager applet will be useful for this because it should run DHCP and has wireless.  But maybe not - the applet doesn't seem very capable.  I had no idea there were multiple apps involved until I started to investigate.

Thanks
Mike

---

