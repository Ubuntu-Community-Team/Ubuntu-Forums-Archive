---
title: "Help with connecting to internet with windows bridge"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by DigitalHighlander on 2008-06-27
Ok, I know a bit about linux in general, used Fedora, SUSE, and now Ubuntu Hardy Heron...  my issue is this...  I connect to the internet through my laptop's WiFi to a router connected to cable ISP.  The laptop runs Vista, and I have a network bridge setup to supply internet access to my other devices (XBOX 360 and the Ubuntu box)  so... heres the issue.  I can ping the laptop, and the ubuntu box and they can both see the "Gateway" router (The one connected to the internet), but I cannot get the ubuntu box on the net.  the system is connected like this:

Internet-----Laptop via WiFi-----router---- Ubuntu

I am using a router but only the 4 internal ports.  basically a hub with DCHP.  I assumed that since I could ping all respective ssytems from the ubuntu box, it would go on the net, but no such luck.
I tried ICS with the windows box.... didn't work, and the XBOX didn't have access to laptop's files anymore.  This setup had worked previously when I had SUSE, but I didn't like SUSE very much.  Any help is greatly appreciated.

---

### Post by superprash2003 on 2008-06-27
are you able to ping your router in ubuntu? also type ping google.com in the terminal and post output here

---

### Post by SubCool on 2008-07-05
I have been dieing to know the answer to this. I have been doing the same thing. I switched it up recently because of hardware failure. but i am 
Internet -- XP -- Hub or Router -- Ubuntu 

I have gone to a static network, but Dhcp is a click away. 
Same issue, i can ping the gateway, but no internet. I had to open up my firwall to get most of that to work. But its like its not forward the DNS information. I ahvent pinged an IP out of the network yet tho. Guess i should.

---

