---
title: "[SOLVED] PPTP/NetworkManager problem with latest Gutsy"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by CameO73 on 2007-10-02
I'm running the latest Gutsy for the last couple of weeks (started at Tribe 5 and updated every time), but lately I have some problems with VPN connections using the network manager.

I'm using the network manager with my RT2500-based wireless card. This works fine, until I start a VPN connection. After a while (could be 10 minutes or 1 hour) I either get a crashreport (apport) or a dropped connection. At this point my wireless connection is completely gone. Sometimes I get a 'please enter your WPA key' prompt, but it will never reconnect until I reboot.

Any idea what could cause this? Any place I could look for more information (logs, error output etc.)? This is the first Ubuntu I can use the network manager; apart from this problem it's really working great!

---

### Post by Carl Farrington on 2007-10-03
I am having potentially a similar problem. I establish a PPTP connection through NM, and the connection drops after 1 - 3 minutes. ifconfig shows that ppp0 no longer exists, but the padlock "vpn connected" icon still shows in the network manager gnome panel applet. I have to tell network-manager to disconnect the connection,  then reconnect. I just did this about three times and then gave up.

To compound the problem, it seems that the included tsclient doesn't handle dropped connections very well. My entire desktop became completely unresponsive until I switched to tty0 and killed the tsclient process.

Not a great start to my fresh look at Ubuntu, although I accept I am only on a beta release (25th September 07 release).

Within 10 minutes of installing I have come across a few problems that have kind of frustrated me a bit today.
Firstly, the installer's migration assistant ran without my consent, and failed at 88%, probably because the My Documents folder on Windows is ~20gb and my Ubuntu partition is only 10gb.
Then I was offered some funky 'restricted' drivers which I assumed would accelerate my desktop experience, however they killed the desktop compositing stuff altogether.
As above, PPTP doesn't work properly/reliably through NM (why can't it be standard anyway rather than optional/unsupported?)

---

### Post by PartisanEntity on 2007-10-31
I have a problem with NM and VPN connections when in wireless mode too. I simply cannot connect to the VPN connection through wireless. It only works when I used a wired connection.

---

### Post by lonetree on 2008-01-04
Hi folks,

my problem seems a little similar. I have pptp vpn server installed on my 7.10 box and connects to it is a windows client. It seems that the connection drops after sometime, sometimes the connection only last a couple of minutes. I actually notice this when I was deploying a temporary vpn server for a small project. At this moment while I am writing this reply, my connection just drop again.  Has anyone have this problem at all?

thanks.

regards,

---

### Post by Stepes on 2008-01-10
I have the same problem I believe. I can connect to the university's VPN PPTP network via lan (from where I connect to the internet) but after radom time intervals I just lose connection to the internet(sometimes pidgin keeps on working fine after I'm dropped...). 

The network manager shows that the vpn is still connected but I have to disconnect it and reconnect it again to be able to open webpages.
And sometimes I can't connect to the VPN again after disconnecting. I really can't figure out where this problem comes from

---

### Post by carnaka04 on 2008-01-13
I think my problem is similar.  I'm using VPN on campus, and I have no problems actually getting a wireless signal and connecting to VPN.  I can then connect to everything on our intranet (shared drives, servers, etc), but web pages NEVER load completely.  Part of the HTML loads, Opera tells me that the page is 60% loaded, but it never finishes.  This is the first time I've installed Ubuntu, so I'm not sure if it's just a Gutsy problem, or if Feisty had issues like this, too.  Any solutions yet?

---

### Post by Urik on 2008-01-15
Did anybody find the solution?
I have the similar problems, using the hand0made script for ppp0.
Connecting through usb cable modem, then PAP authentication - also seems ok, receiving the DNS adresses from provider, and then we have chance 1/10 that it will work.
))

---

### Post by CameO73 on 2008-01-25
Well, I 'fixed' the problem by dropping my wireless card. I'm now connected using a 100Mb connection (onboard Marvell Gigabit controller), and have never experienced any VPN drops since. Maybe it's driver related?

---

### Post by PartisanEntity on 2008-01-25
Here is the solution, for me at least:
[http://ubuntuforums.org/showthread.php?t=601671](http://ubuntuforums.org/showthread.php?t=601671)

---

