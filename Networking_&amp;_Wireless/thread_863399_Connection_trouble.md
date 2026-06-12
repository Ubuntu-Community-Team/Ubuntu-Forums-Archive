---
title: "Connection trouble"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by schizoid90 on 2008-07-18
I have a Peak II wireless LAN usb Adapter. It says it works with linux but in trying to install the device i noticed all the drivers were for windows. I used ndiswrapper to install these drivers and it appears to have installed them fine.

However i still cannot connect to the internet. 

Can someboy/people please help me with this?

I am using Kubuntu version 7.10

thanks in advance
P.S i am using a friends laptop for internet access at the moment with windows Vista on it
connects to the network fine

---

### Post by prshah on 2008-07-18
> **schizoid90 said:**
> 
 I used ndiswrapper to install these drivers and it appears to have installed them fine.
However i still cannot connect to the internet. 


Why not use my step-by-step guide to check if you can get Internet working? Since you have already setup ndiswrapper, you can jump straight to step 9 ("iwconfig") and continue from there.

Post back here with error messages if something doesn't appear to work; you can compare with the expected outputs displayed in that thread to see if something is working or not.

---

### Post by schizoid90 on 2008-07-18
where is you step-by-step guide may i ask?

---

### Post by prshah on 2008-07-18
> **schizoid90 said:**
> where is you step-by-step guide may i ask?

Please pardon my stupidity:](*,)](*,)

It's here: [http://ubuntuforums.org/showpost.php?p=4723545&postcount=1](http://ubuntuforums.org/showpost.php?p=4723545&postcount=1)

---

### Post by schizoid90 on 2008-07-18
destination host unreachable about 300 times so far
and its still going
im guessing thats bad

---

### Post by schizoid90 on 2008-07-19
i am stuck at step 11 i do "sudo dhclient wlan1" and it doesnt find a DHCP server or anything 

it returns the message 
"no working leases persisten database - sleeping"

by the way i dont ave a wlan0 it has been called wlan1 by the machine

---

### Post by prshah on 2008-07-19
> **schizoid90 said:**
> 
it doesnt find a DHCP server or anything 


OK, if your friends laptop is on the same router, then click Start-Run, type ```
cmd
``` and press enter. Then give the command```
ipconfig /all
``` and post the results here. It will give us an idea of what network config is being used, and we can then advise better.

---

