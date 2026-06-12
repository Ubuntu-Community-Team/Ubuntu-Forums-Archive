---
title: "Need Help To Setup Bsnl Broadband"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by greycloud2 on 2016-06-07
Hi, 

I've a Dell Desktop Pc running W10 and Ubuntu 14.04 LTS. Today I formatted my Ubuntu partition and installed a clean copy of Ubuntu 16.04 LTS x64. Everything went on smoothly and after I logged in for the first, I switched ON my ancient Nokia Siemens C2110 Modem provided by my service provider and Ubuntu automatically established an Ethernet Connection. So, I clicked that network icon > edit connection > add > chose DSL from the drop down menu of that dialog box>clicked create and entered my user name, password provided by my service provider. The problem is that whenever I click to connect this DSL Connection my Ethernet automatically disconnects. What shall I do now? 

Thankyou.

---

### Post by greycloud2 on 2016-06-08
Please help guys!!!

---

### Post by X-RED_Tech on 2016-06-08
You don't need to create the DSL connection. Such modems connect by Ethernet and that's it as you noticed. Then you need to open Firefox or any other web browser and access its web interface where you'll input the authentication data.

[http://www.corenetworkz.com/2010/10/setup-internet-in-nokia-siemens-bsnl.html](http://www.corenetworkz.com/2010/10/setup-internet-in-nokia-siemens-bsnl.html)
Please contact your service provider for further instructions.

---

### Post by greycloud2 on 2016-06-08
> **X-RED_Tech said:**
> You don't need to create the DSL connection. Such modems connect by Ethernet and that's it as you noticed. Then you need to open Firefox or any other web browser and access its web interface where you'll input the authentication data.

[http://www.corenetworkz.com/2010/10/setup-internet-in-nokia-siemens-bsnl.html](http://www.corenetworkz.com/2010/10/setup-internet-in-nokia-siemens-bsnl.html)
Please contact your service provider for further instructions.

So, the setup process in 16.04 is not same as 14.04?

---

### Post by X-RED_Tech on 2016-06-08
There's no special setup even in Windows. Please read the instructions from your own provider and if in doubt you already know who to contact.

---

### Post by greycloud2 on 2016-06-08
> **X-RED_Tech said:**
> There's no special setup even in Windows. Please read the instructions from your own provider and if in doubt you already know who to contact.

Hi, the url that you shared has details about configuring modem so that it automatically connects as soon as the modem is turned on. In Ubuntu 14.04 LTS I created a dialer like one does in Windows and that's what am looking forward to do. Like I said, Auto Ethernet Connects without any issue, its just that when I try to connect "DSL Connection 1" Ethernet disconnects on its own and what am unable to figure out why coz I configured my wired connection the same way with previous version and it was working fine.

---

### Post by Rick St. George on 2016-06-08
> **greycloud2 said:**
> So, the setup process in 16.04 is not same as 14.04?

Hi GreyCloud,

I believe you're missing the point from "X-Red-Tech". You don't modify your "Network Connection" within Ubuntu. 

You login to your Modem via a Web Browser, then follow the steps outlined on that Webpage at;
[http://www.corenetworkz.com/2010/10/setup-internet-in-nokia-siemens-bsnl.html](http://www.corenetworkz.com/2010/10/setup-internet-in-nokia-siemens-bsnl.html)

After you completed those steps, including Rebooting the Modem, you're good to go.
DO NOT change the Network Connection settings in Ubuntu. The Modem will provide your IP Address via DHCP.
The Modem is your "Hardware Firewall". Personally, I still like to connect a Router to the Internet Provider's Modem.
That will provide a second layer of protection. Regardless, you may also want to install GUFW (sofware firewall) via Ubuntu Software Center.
More info here - [URL="https://help.ubuntu.com/community/Gufw"]https://help.ubuntu.com/community/Gufw
[/URL]Helpful YouTube video here - [https://www.youtube.com/watch?v=zp0tg6popQ0](https://www.youtube.com/watch?v=zp0tg6popQ0) 
Once installed, open it and select the following, then close it:
Profile : Public
Status : ON
Incoming : Deny
Outgoing : Allow

Hope this helps!
Rick

---

