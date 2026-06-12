---
title: "Wicd gets stuck obtaining IP Address."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by wernotalone on 2008-06-04
I recently got my wireless card drivers installed and working. I was able to connect to my wireless at home twice, but after rebooting/disconnecting, I am no longer able to connect via Wicd, the program gets stuck at "Obtaining an IP Address"

Any help would be welcome.

---

### Post by superprash2003 on 2008-06-04
Ensure that DHCP is ON in your wifi router

---

### Post by wernotalone on 2008-06-06
DHCP is enabled on my router, I just checked.

When I turned on my computer today, it connected to my network without any problems.

---

### Post by wernotalone on 2008-06-06
on restart, it would not connect to my wireless network.

---

### Post by wernotalone on 2008-06-14
WOndering if anyone has found a solution. I am still unable to connect.

---

### Post by wernotalone on 2008-07-06
Three weeks later and I am still having this problem. When it will connect, it does so on its own.

If it does not connect and I try to connect to my wireless network, I get the following message:

default: Obtaining IP Address...
None: Obtaining IP Address...
default: Obtaining IP Address...
None: Obtainign Ip Address...

and so on until Wicd says it isn't connected. "default" is the name of my network at home. DHCP is enabled.

Can anyone help?

---

### Post by xcesarfrancox on 2008-07-06
Do you have the same problem with network-manager?

---

### Post by wernotalone on 2008-07-06
i was never able to connect using network manager, so I switched back to wicd.

---

### Post by xcesarfrancox on 2008-07-06
I had a few issues with network-manager so I tried wicd, but I couldn't even get through wired connection, so I did it with the command line:

Take a look at this:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Also, have you checked that the issue has anything to do with your wifi encryption?

---

### Post by imdano on 2008-07-06
You might want to try out the [release candidate](http://www.wicd.net/latest) for the new version of wicd.  It's much improved over 1.4.2, and you may find it connects more reliably.

---

### Post by wernotalone on 2008-07-06
Thank you, I will check out the new release and post back.

I am unhappy connecting to the internet through the terminal. Internet should be something that just works in my opinion.

---

### Post by kaervos1024 on 2008-11-27
I'm having the same exact problem in 8.10. WICD works most of the time, especially when autoconnecting. If I happen to get disconnected, try to connect by clicking the connect button in WICD client and it will hang at Obtaining Ip Address...

If I put my interface up/down with ifconfig, and try connecting a few more times, it connects eventually.  

Gnome network manager never showed any problems.

lspci:

06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by run2far on 2009-02-25
I was having the same problem with the IP address. Not sure if my solution will help, since I don't know why it worked, but here it is. On my router I had cloned the MAC address from my laptop (probably the same address for both eth0 and eth1). But wicd was still picking up the original hardware/MAC address of the router. Not knowing what else to do, I finally just reset the router to factory settings and voila, wicd connected! :p I now have WPA working and everything. Hopefully it doesn't drop off in 5 minutes....

---

### Post by hobo on 2009-02-25
Enter this command: 
iwlist (yourwirelessinterfacename) sc 
Then find your wifi hub and look at the _Quality line_. Do this when it is working well and when it isn't and compare. Then post both, good and bad here.

---

### Post by hobo on 2009-02-25
Also see this thread for some good troubleshooting commands and tools: 

[http://http://ubuntuforums.org/showthread.php?t=1049065]("http://http://ubuntuforums.org/showthread.php?t=1049065")

---

### Post by musicmatt on 2009-03-11
I had this exact problem on my wired network.  restarting my router was all it took to fix mine.

---

### Post by kouchris on 2011-01-09
Any solution to this? 
Same problem here.. 
1)When i open my computer wicd is automaticaly connected.
2)After a while, Connection is always lost. Although the router doesnt appear to be losing connection.
3)When i try to connect to wired network i get stuck at obtaining ip.
4)Only solution is to restart computer.
5)I had the same problem with network manager.
6)I have a dualboot and the problem goes as fast as the other boot. difference is it doesnt happen often (although i use ubuntu 95% of the time, so that can be inacurate), when it happens, using troubleshooting fixes the problem.

---

