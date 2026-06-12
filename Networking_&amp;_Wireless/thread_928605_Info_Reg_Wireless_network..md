---
title: "Info Reg: Wireless network."
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by sekarapp on 2008-09-24
Hi,

I'm new to ubuntu. I have installed the Ubuntu 8.04 - *the Hardy Heron* in my laptop. I have configured the wireless network in my laptop with the help of the informations that i gathered from this forum and it is working fine now. I have few doubts, could anyone please clarify my doubts?

1) In Windows, the network connection will automatically scan the Wireless networks around the signal area and lists them seperately. We can choose any of the available network as we wish. But in ubuntu, i cannot find such feature available to my naked eyes. Can anyone please give me a information about the wireless networking feature of UBUNTU?

2) Today, i configured the Wireless connection to my laptop manually. If i need to work on other wireless connection, do i need to configure that connection manually? Is there any option available in ubuntu to automatically select the connection?

Could anyone please give the informations for the doubts i mentioned above?

Sekarapp.

---

### Post by Idefix82 on 2008-09-24
You should have an icon in the top right corner of the screen on the menu bar, called the Network Manager. If you left click on it you should get a list of available wireless networks. You can then just click on one to connect to it.

---

### Post by shanix on 2008-09-24
1.
Go to System> Administration> Network and enable roaming mode on your wireless device.[1]

2. Left click on the Network Manager icon located at the right hand top corner, you should see a list of network AP that is available around your house.

3. If you did not see any wireless network AP, you should check:
  a. If the wireless switch has been switched off.
  b. Right click on the Network Manager and see if Enable Wireless has been unchecked.
   

[1] If you did not find your wireless device from there, please open a terminal from Applications> Accessories and type the following:

lspci -vvnn | grep Wireless

and copy the output here.

---

### Post by sekarapp on 2008-09-24
Thanks for your information. I could able to see the available networks now in the Network manager. 

And in the terminal window command goes "lspci -vvnn | grep Wireless" to the next line once after executing the keyword. No output has been displayed in the terminal.

As I'm new to the LINUX Environment, could you also please tell me from where I can learn the LINUX commands?

---

### Post by mailtwogopal on 2008-09-24
Hi Sekar,

  Nice and welcome to ubuntu forums. Lot of sites and materials you can get on learning linux commands, also [Here]("http://linuxcommand.org") you go for linux commands. I am learning thru this and is fine.

---

