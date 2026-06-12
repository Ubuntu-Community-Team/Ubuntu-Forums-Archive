---
title: "More Installation Problems"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by grpphoto on 2009-08-16
Well, after Wubi failed, I tried the text-based installation. It could not find my IP address. So, I booted up Windows in safe mode (the only way it will run right now) and ran the ipconfig program.
 
The "all" option is supposed to show me my IP address. There isn't one.
 
The "release" option says "No adaptors bound to TCP/IP are enabled for DHCP."
 
The Device Manager says that I have a Davicom 9102/A PCI Fast Ethernet Adapter. The General tab for it says that no drivers are installed. The Driver tab shows two drivers; one by CNET and one by Davicom. The Advanced tab shows:
Connection Type: Autosense
PME: All
Receive Flow Control: Disabled
Store & Forward: Enabled
Transmit Flow Control: Disabled.
Transmit Threshold: 512 bytes.
 
My problems started when Verizon installed FIOS and loaded some software on my PC. I have been unable to use it since then.
 
Any ideas?
 
George

---

### Post by nhasian on 2009-08-17
windows safe mode does not have networking enabled.  unless you choose safe mode with networking during startup...

anyways back to ubuntu.

how are you connecting to the internet?  I know you have verizon's FIOS.  are you connecting to the cablemodem directly to your pc?  or is there a router in between?  are you using an ethernet cable from your pc to the router or cable modem?  or are you using wireless?  

most importantly,  have you installed ubuntu successfully and are able to reach the desktop at all?

---

### Post by grpphoto on 2009-08-17
So, if I start up in safe mode with networking, maybe I can find out my IP address? I'll try that.
 
I connect to the internet via a router that was provided by Verizon. It works with other computers (that do not have Verizon software installed on them). I use an ethernet cable for the connection. There are separate cables, and I could switch them, but I think it won't do any good.
 
The ubuntu install was not successful. Ubuntu could not detect an IP address and prompted me for one. That's what led me to try the ipconfig program under Windoze.
 
Thanks,
George

---

### Post by trilobite on 2009-08-18
> **grpphoto said:**
> So, if I start up in safe mode with networking, maybe I can find out my IP address? I'll try that.
 
I connect to the internet via a router that was provided by Verizon. It works with other computers (that do not have Verizon software installed on them). I use an ethernet cable for the connection. There are separate cables, and I could switch them, but I think it won't do any good.
 
The ubuntu install was not successful. Ubuntu could not detect an IP address and prompted me for one. That's what led me to try the ipconfig program under Windoze.
 
Thanks,
George

Hi George - 
 
 I would just say that if you really want to install Linux, I think your best bet is to do it the usual (non-Wubi) way, with a CD. 

 It may *seem* easier at first, installing Linux from Windows, but if you have any problems (and it looks like they're starting), then Windows just tends to get in the way. I say that as a Linux user of eight years or so.

 I've only dropped in to help a few beginners here in the last couple of days, and this is already the second Wubi post that I've seen. I suspect that there will be many more.... 

 Anyway, about your net connection. Since you connect via ethernet, I'd say you have a "fixed" IP address (in other words, DCHP should not be used. That's a protocol (usually used for dialup) which assigns you a different IP address each time you connect). 

 I also connect via ethernet, but when I had the modem dropped off, they gave me a bit of paper with the IP address on it. I'm surprised that you don't seem to have that bit of paper. You could try ringing your internet provider and seeing if they have a record of your IP address. 
- trilobite

---

### Post by grpphoto on 2009-08-18
[quote=trilobite;7805330] 
>I would just say that if you really want to install Linux, I think your best bet is to do it the usual (non-Wubi) way, with a CD. 
 
That's what I'm now trying to do. That's the program that asked me for my IP address.
 
>Anyway, about your net connection. Since you connect via ethernet, I'd say you have a "fixed" IP address (in other words, DCHP should not be used. That's a protocol (usually used for dialup) which assigns you a different IP address each time you connect). 
 
Well, ipconfig says that DCHP is enabled, so that's probably why it won't tell me what my IP address is. If I figure out how to disable it, maybe it will give me a fixed address? Worth a try.
 
>I also connect via ethernet, but when I had the modem dropped off, they gave me a bit of paper with the IP address on it. I'm surprised that you don't seem to have that bit of paper. You could try ringing your internet provider and seeing if they have a record of your IP address. 
 
I'll have to call them up. I never had a dial-up connection. Started out with Comcast, switched to Verizon DSL, now FIOS. I don't see anything about IP addresses in the FIOS documentation.
 
Thanks for your help. I only get about an hour every day to play with this problem. Even less tonight.
 
George

---

### Post by mapes12 on 2009-08-19
Hi George

If you're installing from a CD then when it gets to the part about asking you for info about your network select the option that says something like "install without networking enabled". I remember my install CD trying to find an IP address via DHCP from my router which it couldn't do because it was connected to one. So I selected the option I just mentioned. Ubu loaded fine. I then hooked up an ethernet cable from my router to my PC and network manager configured itself without me having to do a thing. The PC was correctly assigned an IP address from the router. About five mins later Update Manager popped up telliing me what updates I had for my system and away it went to install them.  

Hope this helps.

Mark

---

