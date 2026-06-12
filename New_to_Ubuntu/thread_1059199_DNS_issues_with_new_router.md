---
title: "DNS issues with new router"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by mafiacooper on 2009-02-03
Hi,

I just switched broadband providers and was supplied with a new router. Since I connected my network machines to it I have not been able to connect my Ubuntu box to the internet.

If I look at the devices page in the router's admin, I see this:

```
O2WirelessBox 192.168.1.254	 

--
Inactive Desktop
Unknown-00-13-d3-c6-58-cd 192.168.1.5	
Ethernet Interface	
ethport1
--
SCHNORBITZ 
192.168.1.66	
Ethernet Interface	
ethport3
--
Inactive Desktop
holly	
192.168.1.64	
WLAN Interface	
WLAN
--
Active Desktop
holly	
192.168.1.65	
Ethernet Interface	
ethport2
```

The Ubuntu box is the first device, "unknown" - it is actually called "Hal" and worked perfectly on my previous setup.

Another issue that I think is related is that my local development websites now don't work 100% of the time, and I have to restart bind to get them up again - sometimes I need to restart a few times before things work "properly" again.

Yet another related issue (this is all obviously DNS) is that, when I log into a shell to this box, there is a ten second lag before the password prompt appears.

I have rebooted Hal and the router several times, no dice. Can anyone suggest what might be the problem and the fix? 

Appreciated,

Matt

---

