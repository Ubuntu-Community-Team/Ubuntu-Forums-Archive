---
title: "Setting up wireless"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by ryan777 on 2008-01-20
Hi, this may be answered somewhere else, but I wanted to post my specific situation.

I just installed Ubuntu for the first time and am trying to connect to my home network (at the moment).  My wireless card is detected (and is a Intel PRO/W 3945ABG, common I think).  And it shows nearly 100% signal strength, but it doesn't look like I'm obtaining an IP.  I downloaded the Linux driver for this card in case I needed it (but have no clue how to install it, the read-me isn't helpful), but I've read it should work without it upon installation.  Is this right?

I'm assuming it's a simple fix somewhere, but I'm new to the OS and how to configure the wireless settings.  If not, any help would be most appreciated.  Thanks.

---

### Post by Hightide on 2008-01-20
> **ryan777 said:**
> If not, any help would be most appreciated.  Thanks.

Hi
there are some good wireless tutorials that you may find useful

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)   (kevdog)

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)   (gilf)

:)

---

### Post by pytheas22 on 2008-01-20
Yes, take a look at those guides.  You should not need to install any drivers for Intel wireless in Ubuntu; it should just work.  It sounds like you might have a problem with dhcp.  Make sure your /etc/network/interfaces is set up right properly for whatever your dhcp configuration is, and if that still doesn't help, and try connecting from the command line instead of Network Manager.  Post if those guides still don't solve your problem.

---

### Post by ryan777 on 2008-01-20
Hey guys, thanks for the threads/advice.  Here's the results I got from following the first thread:

Blah...
Blah...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Let me know if I should expand on the "Blah..."  And I verified my /etc/network/interfaces file with the second thread, and they were the same.  Still assuming it's something with me not knowing how to connect rather than some misconfiguration.  Maybe not though.

Thanks again.

---

### Post by pytheas22 on 2008-01-20
Yeah, it wouldn't hurt to post the blah.

How is your network set up in terms of dhcp?  Is there any reason that it would denying an IP address to you?  You don't have MAC filtering for instance do you?  Did you try setting your IP statically?

---

### Post by pytheas22 on 2008-01-20
Also another thought, did you try rebooting your router and modem?

---

### Post by ryan777 on 2008-01-20
I don't guess I know how my DHCP is setup.  It's just a Gateway 2WIRE wireless router, and I have 2 laptops connected to it wirelessly just fine operating Windows.  That's why I think it's me not knowing how to configure my card to obtain an IP through Ubuntu.

Again, it seems to show that I'm connecting to the router; but I'm not sending packets, just receiving.  I haven't tried resetting the router/modem yet since I can connect through the other 2 laptops (as I am now) just fine; think that'd help on the Ubuntu end though?

I'll expand more on the "blah" in a few minutes.  Thanks again for your replies.

---

### Post by pytheas22 on 2008-01-20
It sounds like it's most likely not a problem with the router, but restarting it (if it's not too complicated) couldn't hurt.

Another good thing to try would be to plug in your machine via ethernet and see if it gets an IP that way.  That should indicate whether the issue is with dhcp in general or specific to your wireless card.

---

### Post by pytheas22 on 2008-01-20
actually before you do anything else, I just did a quick search and found this thread [http://ubuntuforums.org/archive/index.php/t-518505.html](http://ubuntuforums.org/archive/index.php/t-518505.html) which says that it should work if you use wicd instead of network manager to connect.  The people there have the same wireless card as you; apparently it doesn't work well with NM.  wicd can be downloaded at [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) .  If you have any issues getting it installed, post, but I think you should definitely try that before anything else.

---

### Post by ryan777 on 2008-01-20
Thanks for that suggestion.  I tried it out, but wicd kept getting stuck at "Obtaining IP Address" and failed to connect.  Who knows what could affect that.

I read on that thread though that one of the guys said he'd just decided to go back to 6.10, where it was working fine.  That's what I'm using :) and we have the same card.  Think a clean reinstall would have a shot?  Or maybe there's something I'm missing about wicd.

Thanks again.

---

### Post by pytheas22 on 2008-01-20
Did you try connecting to an ethernet cable?

I'm a little confused: were you originally using 7.10 and are now on 6.10, or do you mean that you will try using 6.10?  If you haven't tried using the most recent version of Ubuntu, I would do that, unless you have a reason that makes you need 6.10.

I will keep thinking about this and get back to you, although I might not get a change till tomorrow.

---

### Post by pytheas22 on 2008-01-21
more thoughts: is your network using WEP or WPA?  If it is, try turning it off and connecting.

---

