---
title: "Unable to Connect to Internet in Ubuntu 10.4"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by mylittledaemon on 2010-06-30
First of all, I know that there are hundreds of these threads already posted, but I've read through lots of them, as well as the help info on Ubuntu's site, and still find myself utterly confuzzled. I have managed to gather a little more information about my situation which I will post below. 

I used to use Vista, then I switched to a recent, but now outdated version of Mandriva, and now, am forced to switch to Ubuntu 10.04. I have a successful instal, but am unable to access the internet. I am working from the Systems Notification area, and am trying to find a wireless network. 

I can access my Wi-Fi on a temporary Mandriva boot, but I can't find a list of detected Networks on my Ubuntu OS. I will give as much info as I can, but I need a very simple way (if possible) to either find out if I need to get a new LAN card, if it's activated, or how to enter the information to get a wireless network accessed, or anything else that will allow me to access the internet. If you could help me, it would be greatly appreciated. 

Information on my system as follows:
My computer is a Dell Inspiron 1525, with which I have a very love-hate relationship. 
On Ubuntu 10.04, I cannot access a list of detected wireless networks. 
 
WHAT I KNOW:
My IP address (there are about 4 which I sometimes use)
My Gateway
My DNS (though what this is, I'm a bit foggy)
Possibly my Wireless card thingy: If Broadcom Corporation BCM4312 802.11b/g is as such.
My SSID
I think my Operating Mode is: Managed
My Encryption Mode is: Open WEP
My Encryption Key: "AAAAA222AA" (where A=variable letter, 2=variable number)
My ESSID (Same as SSID?)
My WEP Key (Same as Encryption Key?)
My WPS Pin
My WAN MAC

And that's not all!

the following is the output to operation: sudo ifconfig

  	 	 	 	 	 	  eth0      Link encap:Ethernet  HWaddr 00:1d:09:60:f4:2d   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:16  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:384 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:384 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:29120 (29.1 KB)  TX bytes:29120 (29.1 KB)  
 



THIS is the output to operation: lspci -v | less


   	 	 	 	 	 	  00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)  
         Subsystem: Dell Device 022f  
         Flags: bus master, fast devsel, latency 0  
         Capabilities: <access denied>  
         Kernel driver in use: agpgart-intel  
         Kernel modules: intel-agp  
   
 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  
         Subsystem: Dell Device 022f  
         Flags: bus master, fast devsel, latency 0, IRQ 29  
         Memory at fea00000 (64-bit, non-prefetchable) [size=1M]  
         Memory at e0000000 (64-bit, prefetchable) [size=256M]  
         I/O ports at eff8 [size=8]  
         Capabilities: <access denied>  
         Kernel driver in use: i915  
         Kernel modules: i915  
 

 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  
         Subsystem: Dell Device 022f  
         Flags: bus master, fast devsel, latency 0  
         Memory at feb00000 (64-bit, non-prefetchable) [size=1M]  
         Capabilities: <access denied>  
 

 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)  
         Subsystem: Dell Device 022f  
         Flags: bus master, medium devsel, latency 0, IRQ 20  
         I/O ports at 6f20 [size=32]  
         Kernel driver in use: uhci_hcd  
 

 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)  
         Subsystem: Dell Device 022f  
         Flags: bus master, medium devsel, latency 0, IRQ 21  
         I/O ports at 6f00 [size=32]  
         Kernel driver in use: uhci_hcd  
 

 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)  
         Subsystem: Dell Device 022f  
         Flags: bus master, medium devsel, latency 0, IRQ 22  
         Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]  
         Capabilities: <access denied>  
         Kernel driver in use: ehci_hcd  
 

 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)  
 :  
 



********
I'm sorry, I'm still not done.
I have a few aditional questions which, if an alternate method is proposed, probably don't need to be answered. However, my current best bet is trying to figure out how to set up a wireless network (From System Notification Area to the connection setup, to edit connections to "Add")


Is the SSID the same thing as an ESSID?
WHen is asks "Mode", what is the difference between Infrastructure and Ad-Hoc
What is the BSSID, and is it necessary?
Is the MAC address entry the WAN MAC number?
What is the MTU, should I leave it at Automatic?
How do I know what kind of security I have? I think it's WEP 40/128 bit key


   	 	 	 	 	 	  Under Ipv4 settings:
 Method: Automatic (DHCP),  Ihave no idea what this means, but do I choose Manual instead?
 What is a Netmask? When it asks for an entry for “Address”, “Netmask”, “Gateway”, do I have to give an entry for all three, are they the same thing?
 

 What do I have to know about Ipv6 settings?
 Space for an entry for: “Address” and “Prefix”
 

Now, for the most important question, of these, if I do figure these questions out, will it result in an internet access? My thought is not. 



I'm sorry for posting all that on such a redundant subject, but I want to give those with the power to help as much info to work with as possible. If it helps, for the past several months, nearly the entire semester, I've been using a temporary Mandriva boot, so I couldn't install anything, so java, no plugins, nothing which would allow me to listen to downloaded music files, oh, and all setting and all files I saved, were deleted after the system shut down. 



Thank you for your time, and hopefully help!

---

### Post by anewguy on 2010-06-30
Well, it appears that the driver for your wireless adapter has not been installed yet in Ubuntu.

The best place to start is:

- temporarily hard wire your computer to the router

- in a terminal window:

sudo apt-get update

- then look in system/administration/hardware drivers and see if there is a driver list, and if so, be sure to enable it.

Wait a couple of minutes, then do the following:

- right-click on the network manager icon and be sure "Enable Wireless" is checked.  If not, check it and close out of network manager and wait a couple of minutes.

- now left-click on the network manager icon and see if any wireless networks show.

There are some things you need to know about the network you are trying to connect to:

- Does it use any type of encryption?  If so, you need to know the type and the password or passphrase.

- Does the router for the network you are trying to connect to have MAC filtering enabled?  If so, your adapters' MAC address needs to be added to the MAC table in the router.

- Does the router broadcast the network name (ESSID)?  If so, you will see the network name as 1 of the networks available to connect to.  If not, you will not see it and will need to manually configure the network in network manager.

There are other possibilities as well, but this should be enough to get you going.

Post back with any questions/results/failures, etc..

Dave ;)

---

### Post by mylittledaemon on 2010-06-30
Dave, thank you so much for you help! I familiarized myself with modems and routers, went out and got a 3 ft. connector, and for $10.41, have Wired internet. I was able to follow you almost all the way through. 

I finished installing all the updates (took about 10 minutes) went to the hardware drivers, and found two drivers which I later installed, Broadcom BCM, I think, and next, Broadcom STA. I restarted, as per it's suggestion, and went to find the wireless connections, and was, as usual, left with a great big empty screen. Actually, it's only a few square inches, but it feels big. 

I then checked the drivers again, and found that only Broadcom STA (the second one I activated) was active. The information I know suggests that I operate Broadcom BCM, so my hypothesis is that I need to refind Broadcom BCM and activate that one instead / in addition to. 

Do you have any tips for that? 

Regardless, thank you so, so very much!! It feels amazing installing Google Toolbar, and knowing that THAT time, will be the last time I do so (probably, at least on this OS).

I'll start my fiddling around searching for BCM, but again, thank you!

---

### Post by mikewhatever on 2010-06-30
BCM4312 works well with the STA driver here. I suspect you got yours confused by installing two drivers at the same time. I want to stress it, you only need one driver.

---

### Post by mylittledaemon on 2010-06-30
DAVE!!!!! If I knew what the word "adulations" meant, I'm sure I'd use it!! I don't think you can quite comprehend the feelings I have toward you right now, though if you can, I'm very happy for you! It's worked! I have Wireless internet! I FINALLY have a fully functioning computer that will still probably make me swear and throw stuff at other stuff, but I will always remember the time I had without it, and apologize. It's been months of battling to reclaim this machine from the grips of crippled functioning! I have something that I can use....normally! And it's a whole new world too! I can finally begin to explore Ubuntu, learn it's ways, and become one with Linux. A wonderful and fantastic summer awaits me (though the greatness of my summer is not due entirely to this, I have several other projects which give me great joy!)

The point is, thank you Dave, thank you very, very much! And I wish you well! 

Also, I very much admire everyone who helps people out on these forums. I've read through a lot of comments, and they're, for the most part, all very intelligent, knowledgable, and helpful. Of course, most impressive, is that a thread like this actually gets responded to, and solved! You're all wonderful for helping us noobs out! 

Thank you all!

---

### Post by anewguy on 2010-06-30
You're welcome - all that matters is that it's working!  Believe me (and *many* people on this forum would be happy to agree) I'm not that great at Linux.  I've just gotten help along the way, learned some things the hard way, learned others just from reading some other posts.  When I see something come up that I *might* be able to help with I try.

You, too, will be there in a very short time.  All anyone around here could possibly ask is that as you learn stuff, pay it forward by trying to help others as well.

Best of luck!

Dave ;)

---

### Post by mylittledaemon on 2010-07-07
I don't know if I'll be there soon, per se, but I am taking computer science, and I've signed up to be a lab tech next semester, so perhaps by the end of that, I'll be familiar enough with the terminology and my own system to be able to contribute to this wonderful forums in some way! I do hope to become able to aid others in the way that I've been aided. Ha, I suppose this forum is a rather anomalous one...anonymity doesn't incite rudeness and obnoxiousness, and doesn't hinder unrewarded (materially) help and other good sentiments. This is, in that regard, by no means unique, but it is rather rare, in my experience. 

I hope you have another lovely day Dave!

---

### Post by anewguy on 2010-07-09
I had this stupid dream to someday be a forum administrator, but I'm just not picking up the stuff I need to in order to even be considered in the smallest way for that.

I've just kind of given up.  I went back to Windows and deleted ubuntu from both my desktop and my netbook.  I still be around the forums sometimes, but I'm just disapointed in myself so I've given up.

Hope things go well for you!  Oh but to be young again!

Dave

---

