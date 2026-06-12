---
title: "Can't connect to university network after restart"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by kirschkern on 2007-10-26
I got my computer to connect to my university's 802.1x/EAP wired network using an FAQ thread on this forum and wpa_supplicant, etc. Now, I restarted my computer for the first time last night, and it won't connect anymore. 

I run the script to initiate it, and I get the error: ioctl [SIOCGIFADDR]: Cannot assign requested address. 

So, I tried taking it up to the computer help desk on campus, and tried it on their ethernet jack and it worked perfectly. The person who helped me suggested trying it on a different jack had sort of reset something in my computer and allowed it to connect, and that in the future, I might try it on one of my flatmates' jacks. 

I brought it back to my room and expected it to work, but I got the same error message as before, and got the same error again trying it in my flatmate's room. 

Any suggestions, or do I just bring it back to the help people on Monday and look crazy when it works fine there...?

---

### Post by staticsage on 2007-10-26
How are you running the script? Are you running it manually? Is it being run using sudo?

I have to authenticate using 802.1x to connect to my university LAN as well.

---

### Post by kirschkern on 2007-10-26
I got it working. It's weird though. For some reason, the script was configured for eth0, when it should have been eth1. I changed that, and it worked fine. But the weird thing is, why did it work at the help desk...?

---

