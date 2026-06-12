---
title: "VPN two network cards for re-routing? wifi and ethernet via VPN?"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2014-03-17
when travelling, I often end up in a hotel with a lousy wifi. Although working fine for browsing I often encounter repeated interruptions when using the VPN connection to the company network. This makes work nearly impossible. In contrast, my VPN connection at home is completely stable. Is there a way of using this PC as a relay to reroute incoming non VPN connections to the destination requiring VPN? I am thinking of the ethernet being permanently connected via VPN with the target network and coming in via the same router using the wifi on the PC? If this does not work, would it work with two ethernet cards? I could forward the incoming traffic via port 22 and NAT to the IP address of the wifi but how to route the outgoing VPN traffic through ethernet?
Thanks for hints, D_E

---

### Post by SeijiSensei on 2014-03-17
Can the home machine set up a tunnel to the workplace?  If so, you can add a route on that machine to the private subnet at the workplace using the other end of the tunnel as the gateway.  You'll probably also need a route on your client machine that tells it to send traffic for the workplace via the tunnel to your home.  I suspect you won't have DNS resolution for hostnames in the workplace but will need to use IP addresses instead.

The "up" directive in OpenVPN lets you specify a script to be run after the tunnel is started.  This is usually where the appropriate routing commands are entered.

Oh, you didn't tell us what kind of VPN this is.  If it's a [s]crappy[/s] [insecure]("https://www.schneier.com/pptp.html") PPTP tunnel, the concepts still apply, but I cannot help with the commands you'd need to use.

---

### Post by dieter-erich on 2014-03-18
Hi  				 					[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"), thanks!
  unfortunately, since I started working with ubuntu some few years ago I am still feeling a beginner :-) and I do not really understand how to interpret your explanations.

Yes, I can set up a tunnel (e.g. ssh -L 22:localhost:1022 xxx@yyy) to another machine but I still need VPN to enter the company network. So, how can this help? Once the VPN connection established I shall not be able to access this PC from remote without VPN (?)

My laptop is connected via ethernet with the router. I start VPN for access to the company network. I connect via VNC to my PC at work. I now would like to see the screen of this PC from another place without using VPN. It would suffice to have, at the same time, a VNC connection to the PC at home but without the need of VPN. I could imagine that this might be possible in some way by using the ethernet and the wifi on the laptop at the same time for the two different connections. If this is not possible a second network card might help. Maybe even the router could do it????

Sorry, but I have no clue of how to get such a thing to run....

---

### Post by SeijiSensei on 2014-03-18
I'm afraid that unless you are willing to devote some time learning about TCP/IP and routing, you won't be able to do this yourself.  There's no easy cookbook answer for your request.

---

