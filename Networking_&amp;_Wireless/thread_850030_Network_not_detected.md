---
title: "Network not detected"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by jam1 on 2008-07-05
Hi, two years have passed since I've tried Ubuntu [via LiveCD].
I couldn't stay with it due to hard disk constraints at the time...

Back then my router was automatically detected and configured and I could connect to the web.

Now it won't.

I have a Wireless LAN  (ADSL2+ Broadband router) (Edimax) router.
The PC I am using now though is connected via a wire to the router (so nevermind the wireless part).

How do I make Ubuntu detect my router/network/whatever and make it all work?
Any other information you might need I'll do my best to provide.

Thanks,

:)

---

### Post by diwas on 2008-07-05
Exactly same problem. But the brand of Modem is different. Its TP-Link. But i dont think modem is the problem. Yeah another case: When i connect the same modem in the same box usin same OS(ubuntu in this case) the connection is detected. I want to connect through LAN. BTW my ADSL thing is router...sorry for the word 'modem'.

Thanks.

Edit: Its my 1st time Im using ADSL through LAN or USB so dont know abt the previous versions.

---

### Post by diwas on 2008-07-05
Helps please.

---

### Post by linuxonbute on 2008-07-05
> **diwas said:**
> Helps please.
If your adsl modem/router is set up to provide DHCP then all you should need to do is set up your network card to get it's settings via DHCP.

click on Administration/Network

click on 'unlock' button, enter your user password.
click on wired connection and then properties.
disable roaming mode and then choose Automatic configuration (DHCP)

That should be all you need to do.

---

### Post by slymi2005 on 2008-07-05
I have no internet connection either on a realtek rtl8168c/8111c network card and siemens speedsteam 4100 modem connected to a motorola vonage router. I've tried the above post but that didn't do anything. Internet works fine in vista.

---

### Post by jam1 on 2008-07-05
It's quite strange indeed.
Something has definitly changed in Ubuntu with its Networking these past two years. :P

I know for a fact that it just worked straight forward with zero change. And now it's like the network is not detected.

---

### Post by linuxonbute on 2008-07-05
> **slymi2005 said:**
> I have no internet connection either on a realtek rtl8168c/8111c network card and siemens speedsteam 4100 modem connected to a motorola vonage router. I've tried the above post but that didn't do anything. Internet works fine in vista.

I think this is a different problem to the others.

Please do the following commands and post the output to a NEW thread otherwise 
we will be trying to answer 2 problems here and everyone will get confused.

lsusb
lspci
lshw -C network
iwconfig
ifconfig

---

### Post by diwas on 2008-07-05
> **linuxonbute said:**
> If your adsl modem/router is set up to provide DHCP then all you should need to do is set up your network card to get it's settings via DHCP.

click on Administration/Network

click on 'unlock' button, enter your user password.
click on wired connection and then properties.
disable roaming mode and then choose Automatic configuration (DHCP)

That should be all you need to do.

Under connection tab (manual connection) it shows Wired connection (with a photo of LAN jack and hole) with address dhcp written. But this doesnt solve the problem. The network button (the one on the top panel of desktop) still says no networking device found. The internet runs smoothly with the command "sudo pon dsl-provider", but still no devices found. 

What is the problem?

---

### Post by linuxonbute on 2008-07-06
> **diwas said:**
> Under connection tab (manual connection) it shows Wired connection (with a photo of LAN jack and hole) with address dhcp written. But this doesnt solve the problem. The network button (the one on the top panel of desktop) still says no networking device found. The internet runs smoothly with the command "sudo pon dsl-provider", but still no devices found. 

What is the problem?
Not sure I know what you mean by 'internet runs smoothly' when you have no device found. If you can use the internet then it is working. If you can't then the internet is not working. Could you explain please?

---

### Post by diwas on 2008-07-07
> **linuxonbute said:**
> Not sure I know what you mean by 'internet runs smoothly' when you have no device found. If you can use the internet then it is working. If you can't then the internet is not working. Could you explain please?

Ok i have attached a self explanatory screenshot. The internet is running, but no network devices have been found is shown. 
If u need further information, please feel free to ask.
Thank you.

---

### Post by diwas on 2008-07-08
Help please.

---

### Post by diwas on 2008-07-10
Any suggestions??

---

