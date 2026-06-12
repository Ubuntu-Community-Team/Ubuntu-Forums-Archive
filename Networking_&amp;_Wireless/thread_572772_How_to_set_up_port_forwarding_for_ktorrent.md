---
title: "How to set up port forwarding for ktorrent?"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by trishacupra on 2007-10-10
Hi,

I'm getting very very slow speeds with ktorrent. From what I've read, I should try port forwarding. I don't know how to set it up with my modem, so I've attached a screenshot of the fields I need to fill out in the form on the port forwarding configuration page.

In case it's useful, here is my ifconfig, too:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:50:33:CF  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe50:33cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:336282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:313141900 (298.6 MiB)  TX bytes:38875990 (37.0 MiB)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:360977 (352.5 KiB)  TX bytes:360977 (352.5 KiB)


Could someone please help me configure my settings?

Thanks,
Trisha

---

### Post by Claus7 on 2007-10-11
Hello,

I have configured port forwarding both for amule and ktorrent. From the attachment you have it seems that you are in custom port forwarding. Is this the only one option? Because in the same picture it has a plain port forwaring option as well. I will provide you with this link, which is for amule. For ktorrent is similar. Also I think that it is similar for the modem you have as well. As far as I can see the options don't differ a lot. 

[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)
For ktorrent you have to use only TCP. 

The ports you have to open in this case are 6881-6889. Either you will do the procedure I'm describing nine times for each port or you will have : as port start the 6881, port end 6889 and port map the 6881 (for the latter I'm not so sure, yet it seems that it is working).

I have to inform you that ip addresses didn't bother me that's why I asked you if you have something else from *custom* port forwarding.  
If you have finally succeed and save your settings, you might have to add the settings in the applied rules every time you boot your computer (I hope that you don't have to do this).

I hope this helped,
Regards!

---

### Post by trishacupra on 2007-10-11
Hi,

Thanks for your help. It does seem to have made a big difference. :)

---

