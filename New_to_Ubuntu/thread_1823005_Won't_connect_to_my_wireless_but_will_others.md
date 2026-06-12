---
title: "Won't connect to my wireless but will others"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by Debra.S on 2011-08-11
I am running ubuntu 11.04.  This morning, I had no problem connecting to our secure network.  I left the computer for half an hour, and came back, and it was disconnected.  It will now not reconnect to our network.  I know the network is working because other computers in the house are connecting fine, and it CAN connect to an unsecured network that is in range.  

I have no idea how to fix this or what to look for... some help please?  I can provide additional information if you tell me how to find it.

Thanks.

---

### Post by thefasterblueone on 2011-08-11
Try this, turn off your computer, then reboot the modem, then turn on the computer and see if it connects.

---

### Post by Debra.S on 2011-08-11
> **thefasterblueone said:**
> Try this, turn off your computer, then reboot the modem, then turn on the computer and see if it connects.
 
No such luck.  
 
When I first installed ubuntu, my husband had me write a file so that the computer would automatically connect to the internet when I start it up.  Would the IP address that it is trying to use be in this file?  If I then compared it to the IP address the other computers are currently using (by using ipconfig in windows) and they were different, could that be the problem?  If that's a possibility, how do I access that file?
 
Thanks again.

---

### Post by grahammechanical on 2011-08-11
The IP addresses will be slightly different. I am connected to my router by both wired and wireless connections. Wireless IP = 192.168.1.65. Wired IP = 192.168.1.64.

Each machine or connection will have a slightly different number. Network manager should do all the work for you. What messages is Ubuntu giving you? Examine the connection settings in Network manager Edit connections, wireless tab. Make sure that the password is correct in the wireless security tab. This is not your login password but the wireless key or pass phrase that network manager needs to access the router.

Regards.

---

### Post by Debra.S on 2011-08-11
That was one of the first things I checked, and it's all normal.  I am just so confused... thank you for your help though.

---

### Post by carverj on 2011-08-12
> When I first installed ubuntu, my husband had me write a file so that the computer would automatically connect to the internet when I start it up. Would the IP address that it is trying to use be in this file? If I then compared it to the IP address the other computers are currently using (by using ipconfig in windows) and they were different, could that be the problem? If that's a possibility, how do I access that file?


If the IP address compared matched any other device on the network, including the router, that would create a conflict and this could be why it does not work.

---

### Post by Debra.S on 2011-08-13
I really am completely clueless.  I was looking up some stuff in the wiki, and it said to run nm-tool to check the network settings.  I did that, but didn't really understand what it said, so I called my husband in, who is much better with command line than I am.  He caught the problem right away - my computer had changed an uppercase letter to a lowercase letter in our network name.  I have no idea WHY it would do that, but as soon as I entered it correctly as the network name, it connected.  Thanks for all your help though, and I did manage to learn a bit.

---

