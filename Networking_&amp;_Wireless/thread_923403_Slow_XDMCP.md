---
title: "Slow XDMCP"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Kingmilo on 2008-09-18
Greetings,


I recently setup an Ubuntu Desktop, stock standard installation, installed all the updates pending and enabled remote login via XDMCP. What I have been experiencing is slow/unstable connections to the Ubuntu Desktop via XDMCP which I find rather odd.

I have used 2 different Thin Client technologies to make the connection via XDMCP.

1.) Wyse S50 Thin Client ([www.wyse.com](www.wyse.com))
The Wyse is able to make a connection via XDMCP, I am able to login and see the desktop as expected. However the general movement around the desktop is sluggish, there is a distinct delay when trying to open folders or applications.
An attempt to open up an Office document with OpenOffice results in the session being kicked out and taking me back to the Wyse default desktop.


2.) IGEL 3210LX ([www.igel.com](www.igel.com))
The IGEL is not even able to produce the login screen, it attempts too and one can see the 'Ubuntu' cursor spin for a second but then it reverts back to the classic 'X' cursor with grey/black background, it continues to do this until killed.

I have a lot of experience with the above Thin Clients and the XDMCP protocol and currently run 4 Intel Xeon Servers on gentoo with the KDE desktop, and between these 4 servers they provide fully functional desktops for +200 of our staff, so my point is I know the Thin Clients work correctly and can be used in this sort of setup, XDMCP, both the WYSE/IGEL run flawlessly and connect first time without any of the above symptoms. I have also set the desktop for minimal effects as well as reducing the resolution to 1024x768 @ 60Hz which my monitor is quite capable of handling.

Having said that I have installed and used Ubuntu 8.04 (Hardy), on a desktop machine (Intel Dual Core, 1.8MHz, 1Gig RAM, 160Gig Samsung HDD, Intel Graphics Card, Intel 100/1000 NIC), and it runs beautifully if I login locally. From my experience and having run +-50 people on a workstation of similar spec I know that the current hardware can handle at least 2 simultaneous connections, 1 local & 1 remote via XDMCP. I also want to use Ubuntu because I feel it is the best distro out there and with it's constant/steady development is the way forward for our company, not to mention that we are South African and take pride in knowing that Ubuntu roots are South African as well.

The goal of Ubuntu is to work right out of the 'package' which i feel it does and can soon compete with Micro$oft for a good share of the desktop market. So it's very appealing for us because we believe it will save us a lot of admin, especially with the Launchpad Web application which I am very excited to try out. To cut a long story short I believe it is the only way forward for us, so even though we are working well now with our current setup I need to start migrating to Ubuntu but the above problem is a bump in the road that I am struggling to get over.

I have done a lot of research and trawling online to see if anyone has a smilier setup or has experienced the same problems but to no avail. 
I would greatly appreciate advice/suggestions from the community.

I hope I have outlined my problem and goal in a way that it is easy to understand but please let me know if I have left any info out.

Kind Regards,
Dyllan

---

### Post by strollerdude on 2009-01-10
Hi Kingmilo,
I connect to a similar spec laptop running Ubuntu Intrepid 8.10 via xdmcp from a laptop running Ubuntu 8.04 and it works fine, but also a bit sluggishly. Games are not playable, but openoffice works fine. I do have 3GB of ram on the laptop and approx 650MB are used when both machines are connected and doing very little. For what it is worth, I found that running Xfce on the host computer works slightly faster.

I would also be interested in hearing of ways to make Xdmcp run faster.

Strollerdude

---

### Post by strollerdude on 2009-01-11
Whoops!
Ethernet cable was unplugged and I was doing it over wifi. Things working much more smoothly now. Would work even more smoothly with 100/1000 NIC.

---

