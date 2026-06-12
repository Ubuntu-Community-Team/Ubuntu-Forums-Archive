---
title: "AirLink 101 AWLL3028"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by sqrlking on 2007-10-31
Hi,

I bought this wireless usb adapter specifically to use with ubuntu.  awll3026 was on the compatible list, but wasn't available, so I bought this one.  Unfortunately, i can't make it work.  I'm brand new to ubuntu, so the posts i've found regarding this aren't helping...

I read that ndiswrapper may work for this, but I don't have an internet connection on my ubuntu computer.  I downloaded ndiswrapper from sourceforge, put it on a cd, but when i tried to pull it off in ubuntu, i just got an error message.  

I'd REALLY like to make this work, but like I said, I'm new to linux, and I'm having a tough time figuring out the proper steps to get the usb adapter working.  

Can anyone maybe give me a step-by-step to try?  

Thanks.

---

### Post by JC Casiano on 2007-11-15
I bought a couple of these as well, NDISWrapper is not working very well with them in WEP mode.  I'm going to try to configure one of my routers without WEP to see if I have any better luck, I'll update my post in a few hours.

---

### Post by JC Casiano on 2007-11-16
Ok, you're probably not going to like this, I know I don't, but...

I'm on Feisty, patched up to whatever is in the Kubuntu repository.  NDISWrapper 1.38.  I removed both Network Manager and WICD from my system, so all the wireless monitoring is gone.  I have the line "ndiswrapper" in my /etc/modules file.  My system is setting the adapter up as wlan1, I have it set to do DHCP, nothing else (directly mofidied the /etc/network/interfaces file).  And I have the commandline wireless tools installed.

The second router is set up so that the ESSID is "ANY" and there is no WEP or WPA.  The DHCP server is active.  I put in a MAC address filter so that only my adapter is allowed on this router.

With this configuration I can reboot the workstation and it will automatically attach to the Internet.  Ugly workaround, but it will have to do for now.  My observation so far is that ndiswrapper cannot pass the parameters from commandline tools (as well as knetworkmanager and wicd) to the driver.  It's been erratic, sometimes I can get the essid to show up but can't get the key to set, other times it's the other way around.  If I try to set the parameters via the interfaces file most of the time they look like they're accepted but I'm unable to get a DCHP IP address.  WEP is completely out, even "ANY" plus WEP didn't work.  And if one of the wireless managers then tries to change something everything stops working.

So the only way I can get this to work for the moment is to set it to "ANY" with no WEP.

---

### Post by JC Casiano on 2007-11-16
Sorry, I forgot to add, find the ndiswrapper 1.38 .deb file for the common and utils here:

[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

I don't know that there are other dependencies, I don't have a clean system to do a scratch install.  So you'll have to pay attention to what packages any error messages ask for, and download them to CD as well.

If you have specific questions I'll do my best to answer them, but without that Internet connection directly to you Linux workstation you're probably in for some work.  Can you temporarily install a wired adapter?

---

### Post by pmulgaonkar on 2008-07-17
Does anyone know a workaround, or whether this problem has been solved in later releases of ndiswrapper?

--prasanna

---

