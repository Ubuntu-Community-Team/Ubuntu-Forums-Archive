---
title: "Ethernet Help Please - can't connect to internet"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by 315john on 2009-09-16
I have installed Ubuntu 8.04 on my system and have tried everything to get my internet connection to work.  I am using an ethernet connection to a motorola cable modem.  The most i can get out of it is i can see the MAC ID of the modem.  Please Help!!

---

### Post by LewRockwell on 2009-09-16
> **315john said:**
> I have installed Ubuntu 8.04 on my system and have tried everything to get my internet connection to work.  I am using an ethernet connection to a motorola cable modem.  The most i can get out of it is i can see the MAC ID of the modem.  Please Help!!

were you able to connect while test-driving the LiveCD function?

.

---

### Post by halitech on 2009-09-16
whats the output of
```
lspci
```and ```
sudo ifconfig
```

---

### Post by FreewheelinFrank on 2009-09-16
Enter this address in your web browser: you should see the modem configuration page:

> 192.168.100.1

If not, consult the modem documentation and look for a similar address.

Does the configuration page give you an option for DHCP? If so, enable it.

If not, it should tell you an IP address you'll need to enter in the connection manager.

---

### Post by 315john on 2009-09-17
> **FreewheelinFrank said:**
> Enter this address in your web browser: you should see the modem configuration page:
 
 
 
If not, consult the modem documentation and look for a similar address.
 
Does the configuration page give you an option for DHCP? If so, enable it.
 
If not, it should tell you an IP address you'll need to enter in the connection manager.
 
I get connected to the modem and have some screens i can check out.  I still cannot get online?????

---

### Post by 315john on 2009-09-17
> **halitech said:**
> whats the output of
```
lspci
```and ```
sudo ifconfig
```
 
This will show me my eth3: stuff and my ethernet card

---

### Post by LewRockwell on 2009-09-17
> **FreewheelinFrank said:**
> Enter this address in your web browser: you should see the modem configuration page:



If not, consult the modem documentation and look for a similar address.

Does the configuration page give you an option for DHCP? If so, enable it.

If not, it should tell you an IP address you'll need to enter in the connection manager.

we don't think those motorola cable modems are anything more than modems

in that case it probably won't be serving up DHCP

routers are dime a dozen these days and many provide an important hardware firewall function

if you are connecting your machine to the interwebs directly through a cable, dsl, or phone modem...

then you should have a good software firewall installed and operational!

.

---

### Post by Bartender on 2009-09-17
+1
Get a router and you should be in business.  I know for sure that Comcast cable doesn't work with a Linux PC connected directly to the modem but works great with a router in between.   After you've signed in with a Windows PC.

---

### Post by FreewheelinFrank on 2009-09-17
> **315john said:**
> I get connected to the modem and have some screens i can check out.  I still cannot get online?????

Could you tell us the model name/number of the modem, and also the details of the options displayed?

I'm not familiar with cable modems (I'm on ADSL), but there are a couple of possible solutions in previous forum posts.

Did you have a different computer connected to the modem before this one? If so, you might have to reset the router.

[http://ubuntuforums.org/showthread.php?p=219336](http://ubuntuforums.org/showthread.php?p=219336)

Has your ISP given you an IP address? If so, you may need to turn *off* DHCP and tell Ubuntu Connection Manager to use that IP address.

[http://ubuntuforums.org/showthread.php?t=32211](http://ubuntuforums.org/showthread.php?t=32211)

This is how to tell Connection Manager to use a static IP address:

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/)

---

### Post by LewRockwell on 2009-09-17
> **Bartender said:**
> +1
Get a router and you should be in business.  I know for sure that Comcast cable doesn't work with a Linux PC connected directly to the modem but works great with a router in between.   After you've signed in with a Windows PC.

actually...one time we connected some old laptop running Damn Small Linux directly to a motorola surfboard 5101 connected to comcast broadband via the modem's USB port and it worked

naturally that was just to prove it would work, we would definitely NOT suggest that anyone connect their machine directly in this manner!

.

---

### Post by FreewheelinFrank on 2009-09-17
If it is Comcast, they seem to tie their modems to the MAC address of the 'provisioning' computer. Could cause problems if it's a different computer.

[https://answers.launchpad.net/ubuntu/+question/65307](https://answers.launchpad.net/ubuntu/+question/65307)

---

### Post by LewRockwell on 2009-09-17
> **FreewheelinFrank said:**
> If it is Comcast, they seem to tie their modems to the MAC address of the 'provisioning' computer. Could cause problems if it's a different computer.

[https://answers.launchpad.net/ubuntu/+question/65307](https://answers.launchpad.net/ubuntu/+question/65307)

they only need the mac address of the modem

if you switch modems then you will need to call them and give them the new mac address to activate the new address and re-establish your connectivity

.

---

### Post by FreewheelinFrank on 2009-09-17
> **LewRockwell said:**
> they only need the mac address of the modem

if you switch modems then you will need to call them and give them the new mac address to activate the new address and re-establish your connectivity

.

Just looking at some hits from Google, it looks like the modem will only work with the computer connected at the time Comcast establish (or 'provision', as they seem to call it) the connection. Is this right?

[http://www.trap17.com/index.php/Setting-Wireless-Internet-Comcast_t48617.html](http://www.trap17.com/index.php/Setting-Wireless-Internet-Comcast_t48617.html)

---

### Post by 315john on 2009-09-18
> **FreewheelinFrank said:**
> Could you tell us the model name/number of the modem, and also the details of the options displayed?
 
I'm not familiar with cable modems (I'm on ADSL), but there are a couple of possible solutions in previous forum posts.
 
Did you have a different computer connected to the modem before this one? If so, you might have to reset the router.
 
[http://ubuntuforums.org/showthread.php?p=219336](http://ubuntuforums.org/showthread.php?p=219336)
 
Has your ISP given you an IP address? If so, you may need to turn *off* DHCP and tell Ubuntu Connection Manager to use that IP address.
 
[http://ubuntuforums.org/showthread.php?t=32211](http://ubuntuforums.org/showthread.php?t=32211)
 
This is how to tell Connection Manager to use a static IP address:
 
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/)
 
 
Motorola SURFboard Model:SB5101

---

### Post by FreewheelinFrank on 2009-09-18
> **315john said:**
> Motorola SURFboard Model:SB5101

What's your Internet service provider?

Have you had a computer connected to the modem before?

---

### Post by halitech on 2009-09-18
I've also got an SB5101 from Eastlink in Aliant Canada and at least for me, the modem does not get an IP and there are no configuration pages that I can reach in the modem. I've also been able to connect with no issues using either a router or a direct connection so alot will depend on the ISP and how they are set up.

What IP address are you getting on the computer?

Who is your ISP?

If as  you say there is a configuration page for the modem, what is the IP address that the modem is getting?

---

### Post by 315john on 2009-09-18
> **halitech said:**
> I've also got an SB5101 from Eastlink in Aliant Canada and at least for me, the modem does not get an IP and there are no configuration pages that I can reach in the modem. I've also been able to connect with no issues using either a router or a direct connection so alot will depend on the ISP and how they are set up.
 
What IP address are you getting on the computer?
 
Who is your ISP?
 
If as you say there is a configuration page for the modem, what is the IP address that the modem is getting?
 
It only gives me the MAC for the modem, no IP.  I have roadrunner.

---

### Post by halitech on 2009-09-18
what is the output of
```
lspci
```
```
sudo ifconfig
```

---

### Post by FreewheelinFrank on 2009-09-18
Have you connected this computer or another computer to the modem before?

Is the account set up?

Is Ubuntu set to use DHCP on the wired connection?

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

Try pulling out the power cable from the modem and disconnecting the computer. Wait 5 minutes. Power up the modem. Connect the computer- any luck?

---

### Post by 315john on 2009-09-20
Thanks for the help guys.
 
I did get it to work.  I tried setting all the same addresses as my other computer... nothing.  Then set back to DCHP and with a restart of the computer i was online!!

---

### Post by FreewheelinFrank on 2009-09-26
Glad to hear you got your connection working 315john.

For the record, this information seems to be false:

> **FreewheelinFrank said:**
> Just looking at some hits from Google, it looks like the modem will only work with the computer connected at the time Comcast establish (or 'provision', as they seem to call it) the connection. Is this right?

[http://www.trap17.com/index.php/Setting-Wireless-Internet-Comcast_t48617.html](http://www.trap17.com/index.php/Setting-Wireless-Internet-Comcast_t48617.html)

Spoofing a MAC address is not necessary: a reboot should be enough.

[http://www.dynamicobjects.com/d2r/archives/003257.html](http://www.dynamicobjects.com/d2r/archives/003257.html)

---

