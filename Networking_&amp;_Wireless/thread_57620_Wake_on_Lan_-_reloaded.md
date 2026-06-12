---
title: "Wake on Lan - reloaded"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by Anonymaus on 2005-08-17
Hello Ubuntu-community!

As the title states I'm having problems with wake on lan. I've read all threads in this forum about wake on lan and I think I've read every page on WoL that google find by now. I got quite some problems sorted out (read on if you're having similar problems too, I'll try to post my solutions), but what I'm facing now is giving me a headache for days now.
BTW my NIC calls itself a 3COM 3c940 (on the Asus K8V) which actually is a chipset by syskonnect (module is sk98lin), kernel version is the most current 2.6.10 from the Ubuntu repository.

**1. Problem (solved): activate the wake on lan feature of the nic.**
Docs say, you just have to enter "ethtool -s eth0 wol g" and WoL will work. Well, actually the ethtool can't even show status information with the precompiled module.
Solution: download the newest driver from [SysKonnect page](http://www.syskonnect.com/syskonnect/support/driver/d0102_driver.html) . Unpack the file, start the install shellscript. Note that you need to have linux-header and linux-source package installed and unpacked for that. Also, it need a link to the kernel source directory named "linux" under /usr/src. The installation will complain a few things, but they are really easy to solve. However **read the README file** for all the hints I'm forgetting to mention.  :roll: 

**2. Problem (solved): the nic is switched off on shutdown.**
Obviously a deactivated nic can't react on the WoL signal. Most websites I found say that removing/commenting out all "ipdown" or "ifconfig eth0 down" lines from the shutdown scripts will help. Well, it didn't. The lights on the nic and the according light at my switch went out anyway. Somehow I found out, that the halt-command has an option to turn of all nics when called (-i). Funny enough, the -i option is used in **/etc/init.d/halt** on Ubuntu (don't know how other dists handle that). After removing that option, the LEDs of the nic stayed on as the LED on the switch did.
When I now send the magic packet to the computer, I can see the LED of the other (active) Box and the one I want to wake up flash.

**3. Problem (not solved): the computer still sleeps **
Most posting in the web I found have a positive result by now. Well, I don't. I can send as many packats as I want. They seem to reach the nic, but the computer still doesn't turn on.
I've put a "ethtool eth0 ; sleep 5" in the halt script just before "halt" is called, it still states that WoL is set to "g", which should be the right mode. All "Wake up on ..." functions in the BIOS are enabled. APM is active. ACPI is active. The NIC is able to do WoL (*doh*). I even tried to shutdown the computer with the sk98lin module removed (LED went out right after removing the module...), still no go.

So, if anybody knows what exactly problem 3 is or even better how to solve it, pleeeeeease let me know! Right now I have my box running all day just for the case I need some files when I'm at work. This eats up a lot of power that otherwise could be saved  ](*,)  

Cheers!

---

### Post by brundles on 2006-11-01
I've now got WOL working on Dapper with the latest 2.6.15 kernel that's in the repository (-27 I think it was when I let it patch up the box earlier). Probably doesn't help much as you're running 2.6.10.

The only other thing I found that made a difference was the IP address the MP was being sent to. 

If the PC was shut down using Windows then it seemed to work when targetted at the IP address the PC had been using. For Ubuntu however it seems to need to be aimed at the broadcast address for your subnet. e.g. 192.168.1.1/28 that I use needs to be 192.168.1.15.

It might be stating the obvious but I haven't seen many HowTos that specifically state that.

---

### Post by Anonymaus on 2006-11-02
Hi,

thanks for your reply.

By now I'm running Edgy Eft with the most current 2.6.17-10 kernel. The nic is controlled by the skge module (instead of the sk98lin). This module even supports ethtool (so step 1 from my last post has become obsolete). However, my machine is still not waking up when I shut it down with Linux.

The tool I am using for the wake-up call uses the MAC to address the target machine. Which tool are you using to send your MP? I'll give it a try when I get home tonight.

---

### Post by brundles on 2006-11-02
I'm using [this small WOL packer sender](http://magicpacket.free.fr/) although it is Windows based.

You say you're targetting the MAC address rather than IP. What tool have you been using (I couldn't see it in your post)? Most of them still want an IP address as they need to get to the local subnet of the destination PC - and the most effective way for that is still IP.

The MAC address is important because that defines the contents of the MP and what the NIC will be looking for but it's possible that a router or switch is ditching the packet because the NIC (or it's driver anyway) released the IP Address when the OS shutdown. Using the broadcast IP gets around this as it ensures that all routers/switches in the LAN send the packet to every port that has a live connection. 

This also gives the advantage that if done properly you can wake up any singl PC behind a NAT enabled router even though you only have a singe port forwarding on the router.

---

### Post by Anonymaus on 2006-11-03
I tried that tool too. No luck. I tried the IP (192.168.2.21) and the broadcast address (192.168.2.255). All lights on the switch flash when I sen the packet, so the NIC should get it. It just doesn't turn on the machine.

I was using etherwake before, which runs on linux. It's perfectly able to wake up the box when it was shut down with Windows. Any idea what the Windows driver and skge do differently? Perhaps it's not even the state of the NIC that is wrong but some BIOS state? 

Can you post a link to the HowTo(s) you've used? Perhaps I've missed some other thing that should be obvious?

---

### Post by mslonik on 2006-11-04
As far as I understand you, you have tried the same NIC with Windows and Linux on the same computer. In Windows a card works and PC can be booted up, on Linux it can not.

When I wasn't able to boot Linux with WON enabled NIC I tried to test if a card itself is not broken and works as expected. So I've visited a friend who also has a WON ebabled NIC. His was working as expected, my is not. Then I've borrowed his card to be sure that my PC works correctly.

My friend uses Windows on a box. We've found that on his motherboard WON mechanism works only if Windows are shutted down properly. When we push a power button and after couple of seconds switch off the pc before a boot loader starts loading an operating system, it is impossible to wake up a computer with use of WON. It will work again if Windows are booted up and shut down correctly. But it is a case just on his motherboard. On mine it works as expected, so it is pure hardware mechanism.

My suggestions: 
1. Check, if your motherboard works with other WON enabled NIC.
2. Perhaps a BIOS of your motherboard do not support fully WON mechanism as it was a case of my friend. 
3. Try to boot up a system, close it correctly and then try again WON.
4. Try to boot up a PC with wakeonlan Linux program. It is as simple as possible and just works.

Good luck!
Maciej

---

### Post by brundles on 2006-11-07
I think all of the HowTos were linked from here (just searching on "Wake on LAN" and going from those threads. The only changes I've made (beyond the kernel upgrade from the recent Ubuntu patches - see below) are to add the ethtool -s to all run levels and remove the -i from the HALT script. Both of which you've already doen.

[This post](http://www.ubuntuforums.org/showpost.php?p=1572014&postcount=2) was the one that got me thinking that the kernel might be the problem. I don't know what patches are in the different kernel releases but I'm pretty sure that it was the recent kernel upgrade on Dapper to 2.6.15-27 that resolved the WOL issue for my machine. The more I rummage around on Google for WOL and Linux kernel stuff the more I see that it's being tweaked pretty much all the time.

You might need to try googling for stuff specific to your hardware (if you haven't already). I seem to remember another poster on here referring to a bug on the motherboard itself where the MAC address had to be received back to front. (Not applicable in your case as it works from Windows but you get the idea.)

Sorry I can't be more help :(

---

