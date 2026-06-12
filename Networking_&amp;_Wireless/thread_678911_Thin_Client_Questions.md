---
title: "Thin Client Questions"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by TJCIB on 2008-01-26
I work at a small school.  I'm not the tech guy, we don't have one, so I volunteer my time more often than my wife likes.

I am considering doing thin client installs on the 15 computers in our lab from our "server".  We also have a wireless network with a router and 4 repeaters throughout our campus.

Our ADSL modem is our DHCP client.  Does each thin client get assigned its own IP address, or is it really just accessing the internet through the server? Or both?

Our current setup is like this:
modem>>router with 3 outputs (to server, to a switch for lab computers, to wireless router)
server also connects to the switch to provide login, tracking, etc via CafeAgent.

Ideally, it seems that with thin client install I could go directly from the modem to the server, then with the server's second network adapter go to the switch from which all lab computers as well as the wireless routers (and in turn repeaters) draw their signal.  This would eliminate that first router that distributed the modem's signal.  Is this feasible?
Or do I need to distribute the modem's signal to the server and all clients (including routers) via the initial router?

Thanks in advance from a volunteer =)

---

### Post by einstein on 2008-01-26
Disclaimer first:  I am not any kind of expert on thin server/client setup.

I actually installed Edubuntu on my home network so that I have only to maintain one distro for all the children and Grandma.  It works well.  The only real "hiccup" was that none of my computers have a bootable ethernet card so I had to burn a CD for each computer, chuck it in the CD drive and tell bios to boot from CD.

In a nutshell, from any thin client it will appear, essentially, that you are logged into your server.  In reality, this is really what is going on.  All user accounts are on the server, all applications are on the server and, so, Internet access is from the server.  Perhaps more succintly, you have Client->Server->Router->Internet.

Looking at it a different way, you essentially have all of your client's monitors, keyboards and mice attached to ONE computer - your server.  All the client "computer" does is hold the ethernet card and, if boot CDs are required, a CD drive.

Your big problem may be getting wireless clients to work.  I am not sure that this can be done unless, maybe, the thin clients are hardwired to the local hub.  The problem surrounds issues with the client wireless adaptors.

Three cheers for volunteers!

Best regards,
             Dennis

---

### Post by TJCIB on 2008-01-26
Thanks for the post!  I appreciate the input and realize I should have been more specific.

All the Edubuntu machines will be hardwired in the lab.  The wireless network is because our teachers live on our 15 acre campus and we give them free internet access through the school.  They all have their own computer, OS, etc.  The wireless system is not related to the Ubuntu implementation but I thought I should mention it as a variable in case someone more thoughtful than I saw it as an impediment to the Edubuntu project.

Thanks again.

---

