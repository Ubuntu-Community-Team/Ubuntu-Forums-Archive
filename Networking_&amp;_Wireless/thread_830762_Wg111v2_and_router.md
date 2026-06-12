---
title: "Wg111v2 and router"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by jesschen on 2008-06-16
I knew there are many problems with Wg111v2. I had searched the internet for some helps. 

The last version 7.10, I am able to connect to router with  no problem. Since I installed done full installed new version 8.04 and ndiswrapper.  

Wg111v2 allowed me to view the SSID, when I tried to connect to network it does asked me for  key password and authentication. YES i had entered the key password. I also tried Open system or shared key. It wont give ip address the rest of information.

Windows Xp, I am able to connect with Wg111v2.

please advise me what should I do next? I am very newbie about linux.

---

### Post by Peter K Nicol on 2008-06-16
I have the same setup and the same problems. 
I have given up on WEP.
Go to the computer that is wired up to the modem and open Firefox or similar and type in its IP address (it's on the base of the router (192.168.0.1 I think). You might be able to do this through your wireless connection but I haven't tried.
The user name will be "admin" and the password "password" (again on the base of the router). 
This will open the settings for the router. 
Go to wireless settings.
Disable WEP.
To maintain your security read the next bit.
There is also (above this) an access list. If your wireless connection is active the MAC address of your wireless card should be displayed. Click th radio button to add it. (Check the the wireless card's address - it will be displayed somewhere on the card).
Any help? Please let me know if it works.

Peter

---

### Post by Balachmar on 2008-06-18
Just to add to this, just filtering access based on MAC address isn't very secure. MAC address spoofing is (as far as I have heard) fairly easy. (Never tried it myself though)

---

### Post by Peter K Nicol on 2008-06-19
I agree, but in the village I stay in there probably isn't a particular problem. Two neighbours have completely unsecured networks (which I think is unwise particularly as I can access both of them and on one of them I can get into the router settings). I will make them aware of their vulnerability.

Having got the system to work is there any way of improving my security without too much difficulty?

---

### Post by jesschen on 2008-06-19
last time, my next door neighbor have unsecured wireless. It had constant attacked.

So,I must have WEP turn on. Is there way to fix it? I will change modem and router soon. Hopefully it will work.

---

### Post by jesschen on 2008-06-24
I brought a new router.  I still unable to connect with router. 

Since I use windows 98 driver, sometime it allow me to connect and show blue bar and just dont release any address.

I also tried static IP and auto DHCP and there are no luck with connection.

Does anyone have other Wireless USB that work with ubuntu or windows xp?

The last option will be get rid of ubuntu and back to windows?  Which try to not think about it.

---

