---
title: "Ethernet Not Working"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by tonyr1988 on 2007-01-05
I've got a D-Link wireless card on my desktop, and I need to download the drivers for it...but, I need the Internet to do that. I thought about downloading the packages on my laptop and transferring them over, but it would take forever (I only have source, so I need build-essential and TONS of dependencies....not worth it)

So, I figured I'd just do a quick wired connection, download stuff to get wireless working, and be on my way. But I'm having problems getting my wired ethernet connection to work. Here are some facts:

-It's built into my motherboard (chipset nVIDIA nForce 4), not a separate card
-Admin -> Networking has "Wired connection" listed, and it's enabled. But...under the DNS tab, it's got all the right information - I didn't add them, and this is a clean install. How did they pop up with the right DNS servers / search domains?
-My Device Manager has it listed as "CK804 Ethernet Controller"
-Device Manager is saying that info.linux.driver = forcedeth
-lsmod | grep forcedeth outputs:

> forcedeth                       37644                  0

That means the driver should be loaded, right? The 0 in the last column is the "use count," isn't it? Is that bad? :P

I haven't had any problems with wired ethernet before, so I don't really know where to go from here. Then again, I guess something could've messed up with my cable modem - I'll try again in a bit. Until then - any ideas?

---

### Post by Joeb on 2007-01-06
Assuming that your wired connection is set to use DHCP, then the router or cable modem provided the network settings for you automatically (that's what DHCP does).  Does your cable modem have a light that indicates whether your computer is connected or not and if so, is it lit?  You could try opening a terminal window and pinging the address of your cable modem and see if you get a response.  

If you do, then you have a working ethernet connection and your problem is something else (could be on the computer or the cable modem or the ISP).

---

### Post by tonyr1988 on 2007-01-06
Yeah, I'm using DHCP, and I figured the network settings being provided was a good thing. So does that mean that the ethernet driver is setup correctly?

Stupid question: how would I find the address of my cable modem?

My cable modem has a light for PC/Activity - it flashes when there's activity, and stays solid when there's not. It stays solid the entire time when it's hooked into my desktop.

---

### Post by Joeb on 2007-01-06
> **tonyr1988 said:**
> Yeah, I'm using DHCP, and I figured the network settings being provided was a good thing. So does that mean that the ethernet driver is setup correctly?

Stupid question: how would I find the address of my cable modem?

My cable modem has a light for PC/Activity - it flashes when there's activity, and stays solid when there's not. It stays solid the entire time when it's hooked into my desktop.


If you are getting network settings via DHCP then your ethernet card is working.  You won't have a flashing light on the cable modem unless you are actually accessing it or something on the other side of it, which evidently you aren't.

As for the modem's address, most likely, it will be the same as the address for the default gateway that is listed.  If there isn't a default gateway listed, then that's probably the problem.  Actually, it would be a routing problem.  If you don't have a default gateway listed, you can try pinging  aaa.bbb.ccc.1  where the first three ip numbers are the same as your ip address (so if your ip address is 192.168.0.101  try pinging 192.168.0.1).

If you do not have a default gateway, you can add one in a terminal window by entering:  *route add default gw  aaa.bbb.ccc.ddd *  (where aaa.bbb.ccc.ddd is the ip address of your router).  However, you should only do this if you do not have one listed.

If all else fails, do one of these machines you are hooking up also have Windows on them?  If so, can you boot to windows and does it work?  If so, you could always write down the network settings under Windows and then hard code them (instead of using DHCP) under Linux.

---

### Post by tonyr1988 on 2007-01-06
Right now I've got my desktop hooked up (wired) through my wireless router. But I'm having absolutely no luck getting anywhere:

1) I can't ping anything. I can't ping websites, IP addresses, my router, or my laptop that's wirelessly connected.
2) I tried static IP and manually typing everything in (instead of DHCP). I used the same values from my laptop, except IP address (the one I chose is valid, though). Still no luck with anything.
3) ipconfig doesn't even show an IP address at all (except 127.0.0.1)

Any idea what I'm doing wrong?

EDIT: Oh yeah, ifconfig only shows lo listed, it doesn't have eth0 anywhere at all.

EDIT2: In Windows everything works perfectly. I double-checked all the info in Windows, made sure it was the same in Linux (it was). Still no luck. :(

---

### Post by Joeb on 2007-01-06
If ifconfig is not showing an eth0 then your ethernet card is not working.  To be sure, you can try issuing the command:  ifup eth0    and then run ifconfig again to see if it lists it.

When you said, in a previous message that it had the right network settings, how did you determine that?

When you manually entered the settings, if eth0 isn't there, how did you enter them (command line with ifconfig or through a gui)?


EDIT:  In Windows, what does it call your ethernet card?  I just noticed in your sig that you have an AMD 64 and there have been problem reported with certain nVidia ethernet controllers.  Are you using the stock kernel or a 64bit kernel (and if 64bit) can you try booting into the stock kernel or the live cd and see if it finds your ethernet card and works.  If you google for ck804 ethernet controller ubuntu  you will find a match that is very similar to your problem and possible solutions.  Several people have been able to get it to work by not using DHCP, so if you can get the eth0 to show up, that might solve it for you.

---

### Post by tonyr1988 on 2007-01-06
I don't have everything hooked up (I had to drag my modem from across the room for a wired connection :)) - I'm trying to slowly move files over via USB stick to try and get wireless working (rebuilding kernel now), so I may not need to get it working. But I'd still like to see why it's not working.

By it having the right network settings, I meant the DHS servers and search domains. I never entered them, yet they popped up automagically. Sorry for using the wrong terms - I wasn't sure about IP address, subnet, gateway, etc. (since ifconfig never showed anything for eth0)

And I manually entered the settings through System -> Admin -> Networking. "Wired Connection" shows up there (and it's enabled), just not in ifconfig.

---

### Post by Joeb on 2007-01-06
You might want to check out this link: [http://www.ubuntuforums.org/showthread.php?t=312090](http://www.ubuntuforums.org/showthread.php?t=312090)

It was the one I was referring to that had others with similar problems to yours, although I don't know if their etherent card is a match for yours.  If I recall, part way down was another link to another thread about how somebody got theirs to work by using a different driver.  I don't think they had to recompile the kernel, but they did need to compile the driver.

---

