---
title: "Wireless Issues"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by llothos on 2008-04-28
I have 8.04 dual booted with WinXP pro and a dlink dwa-542 wireless card, has the atheros chipset or whatever. Well the other night i got the wireless working but as soon as i restarted the computer it stopped. I am fairly new to linux, i've only played with it on occasion and my problem has always been getting the wireless working so I was pretty excited when I did. I have tried the madwifi drivers (didn't work) and using ndiswrapper (thats actually how I got it working) using version 1.0 of the net5416.inf driver. (i've also tried 2.2 version of both winxp and vista both didn't work)
My question is:
How do I completely remove the drivers so I can start from scratch and try it over again?

I am having another problem as well, after the wireless stopped working in kubuntu I tried rebooting into winxp and now the wireless stopped working in there as well, I have a laptop right beside the computer as well and the wireless signal is Excellent so I know theres a signal there but the dwa-542 wont detect the signal at all, even when I change it from invisible to visible.
also:
what does 'sudo ndiswrapper -a' do?
or 'sudo ndiswrapper modprobe' (cant remember if there was anything else in that)
and 'sudo ndiswrapper -m'
I don't remember exactly if this is correct and I'm at work right now. and i'm sure i'll get a response quicker on here then if I look them up. i know sudo is meant for root tasks...

Any help would be appreciated.

---

### Post by mapes12 on 2008-04-28
I also had wireless problems with my Thinkpad T23 using a PCMCIA wireless card that wasn't supported with native Linux drivers. I installed the windows drivers for the card with ndiswrapper but after a while it refused to connect to the network at boot up. So I bought myself a wireless PCMCIA card (about £10) supported with native Linux drivers (see the sticky list) and it's worked fine ever since. Don't know why XP doesn't see your card though. Maybe a hardware problem, not software.

---

### Post by llothos on 2008-04-28
WinXP does see the wireless card but It just doesn't detect a signal and I checked to see if the signal light was flashing on the card and it is.

---

### Post by mapes12 on 2008-04-28
Does your card see the wireless network? 

To check right click the wireless icon (should be in bottom right hand corner in the taskbar) and then View Available Connections. If it does then you need to check that your machine is connecting to the DHCP server within your wireless router. Call up the command prompt (Run "cmd"). At the prompt type ipconfig. You should then see your private address on the network which should be 192.168.1.xx where xx is your dynamically assigned part of the address. If that shows up ok then try releasing then renewing your DHCP session. At the command prompt type:

ipconfig /release

then

ipconfig /renew

---

### Post by llothos on 2008-04-28
thats what the problem is. the card does not detect any wireless networks, even if i change the router to being visible it still does not detect a signal.

All the settings are in the wireless manager and i even tried deleting them and creating a new connection! Still didn't work!

---

### Post by mapes12 on 2008-04-28
What I would do is:

1. Shut down your PC
2. Unplug your router and leave it for 10 mins. Disconnect everything inc any ethernet cables etc.
3. Plug in the router and let in run its configuration routines. Until the lights become stable
4. Start the PC and see if the wifi card can connect to the router

I had a Realtec router that needed this restart routine reasonably frequently. I now have a BTHomehub which requires a restart sometimes but not as often as the Realtec device.

---

### Post by llothos on 2008-04-28
i'll try that tonight when i get home. 

What exactly are those commands that I was asking about?

---

### Post by mapes12 on 2008-04-29
Once you're happy your router is working OK then you might like to use the command prompt to check connectivity. First off is to make sure your network card in your PC can handle data packets OK. At the prompt type:

ping 127.0.0.1

You should get 4 replies back, each on a seperate line. If you get a failed result your network card is either broken or isn't configured correctly. If you get 4 replies then type ipconfig again and see if you get an IP address as stated previoulsy. If you do then ping the IP address returned from the ping request. If you get 4 replies from the router then your network card is connected.

---

