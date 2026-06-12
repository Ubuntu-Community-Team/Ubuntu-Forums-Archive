---
title: "PPTPD best for this? (Small VPN setup for remote shutdown)"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by Cohh on 2007-10-17
Hello! I am trying to do a specific action through my Ubuntu server at home but am having a little trouble. 

Hopefully someone here has tried something similar and can either help me out or point me in the right direction.

Goal: To be able to access my Windows machine for a remote shutdown procedure through my Ubuntu home server from a remote terminal that doesn't need third party software.

Explanation: I'm experimenting with some software that causes my windows system to need to be shut down, however I cannot do this through RDP. I can, however, go through the management screen of a remote terminal and connect to other computers inside my windows network for a forced shutdown. I move around to many terminals (All XP) and only have access to putty on all of them. 

What I've done so far: I have PPTPD set up, and going through a standard windows VPN screen, I can load my Ubuntu box onto any windows remote terminal. If I then go to a explorer window and go \\UbuntuMachineIP, I bring up the Samba share on my Ubuntu machine. Perfect! If I then go to my putty window, and Ping the Windows machine on my home network, it shows up! 

HOWEVER

If I put \\WindowsMachineIP in the explorer window, I get zero recognition. It doesn't act like the address exists. I feel I'm very close to getting this to work but that I'm missing just one or two settings.

So just to reiterate; I'm trying to make it so I can connect from any Windows Machine remotely to my Ubuntu server through PPTPD and be able to then see my Windows machine on my home network locally (through the VPN, thus enabling me to shut it down through Windows services) on the remote windows machine.

If anyone can help me here I'd GREATLY appreciate it! I can post any file contents as well. 

If you have another suggestion for remotely shutting down a Windows XP machine please let me know that as well!

Thanks guys :)

---

