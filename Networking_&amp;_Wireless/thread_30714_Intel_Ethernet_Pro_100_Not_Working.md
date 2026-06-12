---
title: "Intel Ethernet Pro 100 Not Working"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by snw1972 on 2005-04-29
I had my system set up using the Warty release, which recognized and configured my network card correctly, was able to receive DHCP info ok, could ping to things on Internet, etc.

Then I installed the Hoary release from the ISO on the same system.  During install, it claimed it couldn't get an answer from a DHCP server (which is odd, since there is one), so I configured the networking manually.  

Once the install finished, I go in to start fiddling with networking and see what is going on, I can ping the local interfaces; when I try pinging anything else I get "Destination Host Unreachable".  Interestingly, the lights on my hub seem to blink, so it's doing *something* (I temporarily unplugged other things from the hub to ensure the traffic was from this sytem).

mii-tool eth0 reports the link is ok.

lspci reports it's an "Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 02)".  

When I modify my /etc/network/interfaces to try and switch back to DHCP and do an ifdown/ifup, it again reports it can't hear back from the DHCP server.

Any ideas as to what is going on, and why it went from working to not working?

Thanks!

---

### Post by whzzz28 on 2005-05-01
I also have the exact same problem with this exact same network card, except mine is a rev 05, not 02.
Fearing that the card was to blame, i switched to using the onboard realtek device. Same problem occured. Cannot retrieve an address from the DHCP server and upon assigning a static IP, pings return a destination unreachable message.

Ive done some searching, removed ipv6, changed the dhclient.conf to send a hostname and other things, none have any effect on this.
If i do a ifup eth0, it returns that there were no DHCP offers recieved.

All hardware has been tested, NIC works in other machines, cable works on other machines and the port on the switch is also working. Keeping the existing setup i plugged in a laptop with windows on it, it booted and recieved a DHCP address successfully and had no troubles talking on the network.

Similarly my friend had the same issue, the only common occurance between the us two is that 
A) we are both running the latest ubuntu
B) the DHCP server was Windows 2003's DHCP server.

Still can't figure this one out.
Any help would be greatly appreciated.

---

### Post by agentworm on 2005-05-02
I am also having similar problems with this network card (although it just says 82557/8/9 [Ethernet Pro 100].

The main difference between you guys and I is that I was assigned an IP where I set up this linux box. I can ping the localhost, and the IP address assigned, but I can't ping the Gateway address.

I've done the ifconfig and the dmesg. dmesg didnt report any errors (or if it did, then i wouldnt be sure where to look). It did say that it was unable to "set IRQ for PCI Interrupt Link [LNKB] (likely buggy ACPI BIOS)" for a few things. Could that have something to do with it? 

I don't know what to do! :(

---

### Post by snw1972 on 2005-05-04
I did a little more poking around tonight to see if I could figure out what was going on.  
When I look in /var/log/messages, I see things like this:

kernel: NETDEV WATCHDOG: eth0: transmit timed out
kernel: e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex

Googling that error finds lots of things, but I wasn't able to find advice that seemed to match my situation.

---

### Post by kamsar on 2005-05-05
I had the same problem and managed to solve it by passing the kernel the "noapic" option. I guess it's something to do with buggy interrupt routing on some motherbaords/NICs.

---

### Post by snw1972 on 2005-05-05
Adding the noapic option worked!  Thanks for the help!

---

### Post by Frikle on 2005-08-28
Hi, I'm an Ubuntu newbie and had exactly the same problem as the others in the thread. I was bery glad that there was a solution that worked for someone but I'm not sure when I should pass the "noapic" option to the kernel. Is this during the initial configuration? What command do I use?

Thanks

---

### Post by flyfishin on 2005-10-14
[QUOTE=Frikle]Hi, I'm an Ubuntu newbie and had exactly the same problem as the others in the thread. I was bery glad that there was a solution that worked for someone but I'm not sure when I should pass the "noapic" option to the kernel. Is this during the initial configuration? What command do I use?

Thanks[/QUOTE]

I just installed Breezy.  When the install first starts and on the screen it has the boot: option and is waiting for your response, just type 'linux noapic' without the quotes.  It worked like a charm on my install.

---

### Post by krisOlafsson on 2007-02-22
this sounds like the same trouble I'm having with the network card. [http://ubuntuforums.org/showthread.php?t=365500&highlight=ml370](http://ubuntuforums.org/showthread.php?t=365500&highlight=ml370)
 Now I already have ubuntu installed so where should I put "noapic" in grub? or should I just reinstall the whole thing? there isn't any data onthe system yet so it wouldn't be that bad. 

thanks for any help.

---

### Post by danlaptic on 2008-07-09
So how do you do it?  Where do you have to type in 'linux noapic'?  

do you have to do it during install?

Thanks

---

