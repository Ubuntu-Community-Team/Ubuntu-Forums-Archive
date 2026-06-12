---
title: "Remote Desktop - Help Instruct Me"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by NoVista on 2008-02-05
Running Gutsy both machines, my desktop and laptop.
Laptop is connected on my wireless network.
I enabled Remote Desktop on my desktop system.
I go to the laptop, open a terminal and type: 
vncviewer MyComputerNameHere:0
(By the way, I know it's a security risk, but for now I just want to get it working. Once I understand more about this, I'll use SSH or something else to secure it).

And it never will connect, as it says something to the effect that the machines host name is not available. Ok. The desktop is on a router. And here I come to the part I need some tutoring. Port forwarding. I just don't understand what I need to enter/change.
Also, the desktop, being on cable, uses automatic DHCP, and the Wide Area network Setting has to be on Dynamic, not Static.
Does port forwarding work with a Dynamic and automatic DHCP setup?
Anyone who has some time to help me get this going, I would appreciate it.

---

### Post by Andrew Stone on 2008-02-06
From your post I can't really understand your network layout at home.  It almost sounds like  the wireless and wired are not connected.  Do you have a singe cable modem/wireless device, or 2 devices?  Can the laptop and desktop share files or communicate in any way?

The reason why I am asking is because if both machines are in your home network you probably don't have to do any port forwarding; generally that is only used in the firewall between your home network and the WAN.

Do an "/sbin/ifconfig" on both machines and post the results if you are a newbie at physical networking.

Assuming that the physical network is all ok, it should not be that hard to get vnc working.

I am not sure what "remote desktop" starts; I am using "vino".  Do a "ps -efwww" on your desktop to see what program is running.

On the laptop, do "vncviewer IP_ADDRESS:PORT".

You find the IP_ADDRESS of the desktop through the ifconfig command I posted earlier.

So it looks like you are using port 0.  I doubt that will work, the default for vnc is port 5900.  So this works for me, for example:

 vncviewer 192.168.1.113:5900

---

### Post by NoVista on 2008-02-06
Thank You.

It's working now.

---

