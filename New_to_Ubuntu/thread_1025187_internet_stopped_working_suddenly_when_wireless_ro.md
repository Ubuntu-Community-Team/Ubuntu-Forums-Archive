---
title: "internet stopped working suddenly when wireless router is used"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by hanzj on 2008-12-29
Hi,


I've had a wireless router that we've used for several months now. It was working fine for all the time (1 year) at our previous residence. And it's been working fine when at the new place since December 1. 

We were able to share the internet connection. One computer is  a friend's Windows XP -- the one I'm using to type this message -- connected via LAN/ethernet cable. The other comp is my Ubuntu computer desktop as well, but getting internet wirelessly.

Then all of a sudden my friend told me that he was not able to surf internet on his computer. I called our ISP tech line and they suggested I try getting the wireless router out of the picture -- plug the cable directly from the modem to the back of the computer. So when I did so, things were working fine.

But when I tried using the wireless router again, we could not access the internet. Please help us. We don't know why the wireless router won't work.

Here's some info that may be relevant to the problem.

How things are right now (internet is ok):
Without dell wireless router and without bridge (in Network Connections)
> 
C:\>ipconfig

Windows IP Configuration


Ethernet adapter Internet:

        Connection-specific DNS Suffix  . : bc.skyweb.ca
        IP Address. . . . . . . . . . . . : 216.18.24.117
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 216.18.24.1


How things were when the wireless router was in the middle of the connection:
(Internet is not accessible)
with dell wireless router and without bridge
> C:\>ipconfig

Windows IP Configuration


Ethernet adapter Internet:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.2.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1------------


Please help. The wireless router did not have a physical crash, so it should still be working. Please help us troubleshoot.

Thanks.


UPDATE: We use Dell Wireless 2350 Broadband Router

---

### Post by ken22 on 2008-12-29
So your WinXP machine is having trouble.

Looks like the wireless router is assigning an address to your machine by dhcp overriding the address that your modem.

Am I right in assuming your modem assigns addresses normally when your directly plug in by cable? 

If so, take the IP data
> **hanzj said:**
> 
IP Address. . . . . . . . . . . . : 216.18.24.117
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 216.18.24.1 

and hardcode it into your network config.

You could also try turning off your wifi routers dhcp function and setting your XP machine to get it's address from the modem.

......OR.....I have to say it..

Use Ubuntu

---

### Post by hanzj on 2008-12-29
Dear Ken22,
Currently, with the Dell Wireless router plugged in, the ubuntu comp also is not getting internet.

---

### Post by ELF_O8 on 2008-12-29
For future reference, I would suggest you not post sensitive ISP information (your IP address and DNS suffix) on the internet. You never know who's out here.

---

### Post by ken22 on 2008-12-29
can you access the wifi-routers web interface?

---

### Post by hanzj on 2008-12-29
I DO use ubuntu. pls read my OP again to understand the setup we have in the residence.

---

### Post by hanzj on 2008-12-29
> **ken22 said:**
> So your WinXP machine is having trouble.
It's my friend's winxp machine. My Ubuntu comp is in another room. It, too, is having problems with internet. Pls read OP.

> 

Looks like the wireless router is assigning an address to your machine by dhcp overriding the address that your modem.

Should I confirm your suspicion? If so, how?


> Am I right in assuming your modem assigns addresses normally when your directly plug in by cable? 
Again, I don't know. How can we confirm this on a winxp machine?

---

### Post by hanzj on 2008-12-29
Dear ken22, 
yes, when wireless router is in the setup, i can access it on a web browser by going to [http://192.168.2.1/](http://192.168.2.1/) .

However, when wireless router is in the setup (plugged in), no other website can be visited.

---

### Post by hanzj on 2008-12-29
pls don't hack us, friends. 

8-)

---

### Post by hanzj on 2008-12-29
> **ken22 said:**
> 

If so, take the IP data

 	Quote:
 	 	 		 			 				 					Originally Posted by **hanzj** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6459054#post6459054") 				
 				[I]IP Address. . . . . . . . . . . . : 216.18.24.117
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 216.18.24.1 [/I]
 			 		 	 	 


and hardcode it into your network config.



how do i do this "hard-coding"?

Thanks.

---

### Post by ken22 on 2008-12-29
I think your network setup is more complicated than you make it out to be. Could you supply a diagram.

---

### Post by ken22 on 2008-12-29
> **hanzj said:**
> how do i do this "hard-coding"?

Thanks.

I no longer think this is the problem. The IP info you get when you use the wifi doesn't look wrong.

Can you ping the router and modem?

---

### Post by louieb on 2008-12-29
Guess you have already reset the router by unplugging the power.  

> Looks like the wireless router is assigning an address to your machine by dhcp overriding the address that your modem.Thats normal - thats what routers do. Each machine pugged into the router gets a different IP address.  The router itself has two IP addresses  one it gets from the modem and another for the LAN side of the router.

Sounds like the router has quite communicating with the modem. Since it has been working for a while I suspect the router has died or something has gone wrong with the firmware. Go to the manufactures website and download the latest firmware for the router. Then plug the router back and go to the web interface. There should be an option to update the firmware. Hopefully that will solve the problem.   

Good Luck.

---

### Post by hanzj on 2008-12-29
Here you go.

---

### Post by hanzj on 2008-12-29
> **louieb said:**
> Go to the manufactures website and download the latest firmware for the router.

Good Luck.

[http://search.dell.com/results.aspx?stag=CZTRD61&s=bsd&c=us&l=en&cs=04&ec=&ira=False&cat=sup&subcat=dyd&rf=all&evl=&nk=f&k=2350&p=1&nf=&rpp=12&sort=K&~srd=False&ipsys=False&advsrch=False](http://search.dell.com/results.aspx?stag=CZTRD61&s=bsd&c=us&l=en&cs=04&ec=&ira=False&cat=sup&subcat=dyd&rf=all&evl=&nk=f&k=2350&p=1&nf=&rpp=12&sort=K&~srd=False&ipsys=False&advsrch=False)

gives about a dozen firmwares for this router. which one should i download? Pls see the link.

---

### Post by ken22 on 2008-12-29
> **hanzj said:**
> [http://search.dell.com/results.aspx?stag=CZTRD61&s=bsd&c=us&l=en&cs=04&ec=&ira=False&cat=sup&subcat=dyd&rf=all&evl=&nk=f&k=2350&p=1&nf=&rpp=12&sort=K&~srd=False&ipsys=False&advsrch=False](http://search.dell.com/results.aspx?stag=CZTRD61&s=bsd&c=us&l=en&cs=04&ec=&ira=False&cat=sup&subcat=dyd&rf=all&evl=&nk=f&k=2350&p=1&nf=&rpp=12&sort=K&~srd=False&ipsys=False&advsrch=False)

gives about a dozen firmwares for this router. which one should i download? Pls see the link.
[http://ftp.us.dell.com/network/R89593.EXE]("http://ftp.us.dell.com/network/R89593.EXE")

---

### Post by hanzj on 2008-12-29
i've tried installing the latest firmware and I think I've just turned the wireless router into a brick. Does anybody have a spare wifi router they'd like to share with me. I can pay for it of course, plus shipping. 

I didn't get any material Christmas present, so your contribution would be the BEST!

---

### Post by ken22 on 2008-12-29
The router should have a small reset button located on it.

---

### Post by hanzj on 2008-12-29
Tried that, to no avail.

---

### Post by ken22 on 2008-12-29
Please explain what happened when you tried to upgrade the firmware.

---

### Post by hanzj on 2008-12-29
The exe file said that firmware updated FAILED.

And now my router is blinking as it has never blinked before.

---

### Post by ken22 on 2008-12-29
> **hanzj said:**
> The exe file said that firmware updated FAILED.

And now my router is blinking as it has never blinked before.

When you tried the reset button did you hold it in for at least 5 seconds?

---

### Post by hanzj on 2008-12-29
Yes, just did the 5-second hold now.

---

### Post by ken22 on 2008-12-29
Can you access the web-interface?

---

### Post by louieb on 2008-12-29
What is the full model and version number on the bottom of the router? When going thought the list did you see an exact match?

---

### Post by hanzj on 2008-12-30
No, can't access web interface anymore. This probably means wireless router is now good for nothing.

---

### Post by ken22 on 2008-12-30
If you did a reset, the wifi router would take on it's original IP address.

Please try this address. It will be located in the documentation of the router.

---

