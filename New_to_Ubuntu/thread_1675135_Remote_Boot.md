---
title: "Remote Boot"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by klossor on 2011-01-25
Hey all, hopefully once again the guru's out there can help an Ubuntu/linux rookie out ;)

So I have a machine on one of my local networks running Ubuntu desktop 10.10, and I have remote desktop enabled on it. I got it setup to run Rdesktop on the local network fairly easily, and with some basic port forwarding etc on the gateway its enabled from remote networks also, no problems there really (Though for some reason Firestarter, or more to the point IPTables took some cajoling) 

However with this machine not up all the time, How would I go about bringing it up remotely from an external network and then login to my user account?

(At this point I'm assuming I would simply use remote desktop to login to the machine as I have been doing? Or is there a less cumbersome (more all in one) solution to this?)

---

### Post by robsoles on 2011-01-25
Hi, just in case you've made 21 posts and nobody has welcomed you: Welcome to UF.


I am not an expert in all matters of networking and computing but I know of no Operating System that can offer to cause the machine that runs it to "switch on" just because somebody tries to access it remotely - coming back from standby shouldn't be impossible to arrange but only by relying on something in BIOS+Mobo+NIC can you cause 'power on'.

Some BIOS, of some motherboards, offer 'Boot from LAN' under a section/menu named along the lines of "Power" - I haven't seen one that offered further configuration but I haven't really pressed into it that hard on any system I have seen it in the BIOS of.

It is very probable (to me at least) that the port and protocol being used are meaningless to the mechanism powering the system up when this is used and, I reckon, to make it work you will need something that will purposefully refer to the MAC address of the network adapter of the system being woken up.

I think it unlikely that it joins a network (acquires an IP address from a DHCP server) or has option to set a fixed address but just trying it in a system that has the option in it's BIOS could easily prove me wrong ;)

Can you find such an option in any menu of the BIOS of the machine?

---

### Post by klossor on 2011-01-25
Hey, thanks for the welcome ;)

> **robsoles said:**
> 
It is very probable (to me at least) that the port and protocol being used are meaningless to the mechanism powering the system up when this is used and, I reckon, to make it work you will need something that will purposefully refer to the MAC address of the network adapter of the system being woken up.

Yes it has occured to me that that network layer protocols won't have any impact on a machine that's down, as all this has to happen at the physical/data-link of course. Though this requires I imagine another machine on the local network, which can be logged in to, and have at least tftp running. (Another set of problems hehe)

> **robsoles said:**
> 
I think it unlikely that it joins a network (acquires an IP address from a DHCP server) or has option to set a fixed address but just trying it in a system that has the option in it's BIOS could easily prove me wrong ;)

I imagine once the machine POST's / BIOS' and bootup have occured the dhcp server will assign an address normally (A reserved dhcp address that is, to keep the IP static) 

> **robsoles said:**
> 
Can you find such an option in any menu of the BIOS of the machine?

Yeh I've enabled PXE boot on the machine and Ive even tried to use wakeonlan in the bash shell from another machine on the network for testing, still no joy :(

I suppose this is more of a networking quesiton, but peeps are decent around here it seems and always try help out, so I thought i'd throw it out there ;)

---

### Post by themusicalduck on 2011-01-25
You need to look into Wake On LAN. Although that works fairly simply over a local network, I think using it over the internet is a bit more complicated.

This guide claims to describe how to do it [http://art.ubuntuforums.org/showthread.php?p=9826626](http://art.ubuntuforums.org/showthread.php?p=9826626) although it talks about doing it using a router running DD-WRT.

[http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=wake+on+lan+over+internet+ubuntu](http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=wake+on+lan+over+internet+ubuntu) might have some more useful results.

---

### Post by klossor on 2011-01-25
> **themusicalduck said:**
> You need to look into Wake On LAN. Although that works fairly simply over a local network, I think using it over the internet is a bit more complicated.

This guide claims to describe how to do it [http://art.ubuntuforums.org/showthread.php?p=9826626](http://art.ubuntuforums.org/showthread.php?p=9826626) although it talks about doing it using a router running DD-WRT.

[http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=wake+on+lan+over+internet+ubuntu](http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=wake+on+lan+over+internet+ubuntu) might have some more useful results.

Yeh I've given wakeonlan a go and as you say, its more the use from an external and the setup of a machine on the network with tftp running.

Thanks for the links, ill have a flick and see if anything stands out.

---

### Post by robsoles on 2011-01-25
Look harder in the BIOS for an actual "Wake on LAN", specifically. It is easier than trying to make a "thin client setup".

Unless I've just read the wrong wikipedia entry for it, "PXE Boot" is looking for a way to start an OS on the machine from a networked source after it is booted up close and personal, such as you are looking to avoid - I think you will set up your server and find you still need to find "Wake on LAN" and enable it to make the system start-up due to remote access.

Enable "Wake on LAN" in BIOS, disable pxe boot, if you get to enable "Wake on LAN" without getting to configure an IP address or anything then get the MAC address of the local NIC (while OS is booted get a terminal and 'ifconfig -a' will list a "HWaddr", should be the MAC address, look for eth0) and then look for 'gWakeOnLan" in Ubuntu Software Centre and try it out.

How does this work out for you?

---

### Post by klossor on 2011-01-25
> **robsoles said:**
> Look harder in the BIOS for an actual "Wake on LAN", specifically. It is easier than trying to make a "thin client setup".

Unless I've just read the wrong wikipedia entry for it, "PXE Boot" is looking for a way to start an OS on the machine from a networked source after it is booted up close and personal, such as you are looking to avoid - I think you will set up your server and find you still need to find "Wake on LAN" and enable it to make the system start-up due to remote access.

Enable "Wake on LAN" in BIOS, disable pxe boot, if you get to enable "Wake on LAN" without getting to configure an IP address or anything then get the MAC address of the local NIC (while OS is booted get a terminal and 'ifconfig -a' will list a "HWaddr", should be the MAC address, look for eth0) and then look for 'gWakeOnLan" in Ubuntu Software Centre and try it out.

How does this work out for you?

Ok so now pxe is disabled, and removed from the boot list also. I have On board LAN boot enabled. I installed gWakeOnLan on a local Ubuntu system.

However I think the problem is with my NIC on the machine, I just ran ethtool and while WOL is supported the wol state was set to "d". I ran "sudo ethtool -s eth0 wol g" and it seems to be up now. So I ran wakeonlan from another machine with both gWakeOnLan and the command line wakeonlan version, unfortunately there was no success. Using the gWakeOnLan I was unsure if the magic packet was being sent as there as no confirmation. Using the command line tool I used the command "wakeonlan 00:00:00:00:00:00" (Zero's replaced by actual address here) which was confirmed by "Sending magic packet to 255.255.255.255:7 with 00:00:00:00:00:00" I also tried port 9 on the broadcast address.

So I've tried all I can think of with this issue ,even after properly configuring WOL on the NIC no luck :( , thanks for all the help so far n all :D Well back to it I suppose, perhaps if I just keep at it I'll work it out lol

---

### Post by robsoles on 2011-01-25
I wonder if the local router is blocking the 'magic' packet for some silly reason or other. Difficult to check, I wonder if you could packet sniff both ends to make sure it's (1) being issued and (2) getting past the router(s).

If interested then have a look in software centre to see if you can find a packet sniffer to like. I don't mind EtherApe.

---

### Post by klossor on 2011-01-25
Hmmm it seems the packet is getting through fine :confused:

I decided to go with your advice and check, so I started on the box I'm hoping to wake itself, I fired up Wireshark and sent the packet from another machine and got this output on eth0:

32    24.978731	 192.168.1.102	255.255.255.255	WOL MagicPacket for AsustekC_00:00:00 (00:00:00:00:00:00)

The actual MAC address' matched up fine too, now I'm really confused.... lol

---

### Post by robsoles on 2011-01-25
Do connect/activity light(s) remain lit on NIC of machine you are trying to wake when you tell the OS to shut the system down?

---

### Post by klossor on 2011-01-25
Yeh the connectivity light seems to still stay active, this may actually be one of those times where a box has a defective NIC lol

Anytime I've ever heard that from someone before I always think to myself "Sigh.... theyve got something mis-configured and now they think they need to be a new nic....."lol

This time it may actually turn out to be the case. Later on when I get a chance I'm going to pop a new NIC into the machine and see if that once and for all solves this issue lol

Thanks for all the help thus far, much appreciated, and I'll let ya know how it goes ;)

---

