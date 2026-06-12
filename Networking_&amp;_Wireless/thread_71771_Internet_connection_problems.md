---
title: "Internet connection problems"
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by abdulisse on 2005-10-04
Hi,
    I just installed Hoary on my laptop which i will provide the specs for below and the installation went good. I noticed during the install though that at one point when it was "confiquring connection" or something, i did not get a good look went too fast, the end result was a "Fail", and it gave me options. I click on "setup connection later".

So the rest of the installation went good and everything was installed and confiqured. It booted and i logged in. Everything seemed perfect and okay. Then i pluged in my network wire which is connected to a cable internet modem. 
[img]http://www.jplistings.ca/include/gdthumb.php?pass=../photos/forsale/individual/104188_19827078.jpg&mw=120[/img]

The little computer screens at the top were blinking and i thought it was all good. So i launched Firefox and typed in 'google.ca' which didn't do anything.
I got the usual message of 'cannot find, check name and try again'.

Can anyone help me on setting up my connection? Please and thank you in advanced.

Computer specs : [http://www.epinions.com/pr-Laptops_Hewlett_Packard_Compaq_Presario_2100US_Laptop_DB954A_ABA/display_~full_specs](http://www.epinions.com/pr-Laptops_Hewlett_Packard_Compaq_Presario_2100US_Laptop_DB954A_ABA/display_~full_specs)

---

### Post by odin on 2005-10-04
first of all is it your network interface enabled? and if you have dhcp,do you have it configured so it gets an ip?

well try this(I dont know how much you know about linux so i'll explain like you were a newbie and if you are not and everything I tell you are things you already know then post it and maybe we try something else)

open a terminal and type:

ifconfig

there you should see all your active network devices  and their ips (if they have) and this things.

if you dont have there your device then type:

ifconfig "device" up    (by device I mean eth0 or eth1.In my labtop the ethernet device is eth1 but in yours i dont know)

and finally:

dhclient "device"

this should get it working.And so you dont have to type this everytime time you boot edit /etc/network/interfaces and look where your device is (if it's not there just write what i'll tell you now and if it is there then change everything about that device with this)

auto eth0
iface eth0 inet dhcp

well hope you didnt fall asleep reading this and that it can help you.

---

### Post by abdulisse on 2005-10-04
I think i will try this once i get home, im at school right now.

And to clear up your question I am a newbie at this so i'm happy you took it like i was a novice.

---

### Post by abdulisse on 2005-10-04
I think i will try this once i get home, im at school right now.

And to clear up your question I am a newbie at this so i'm happy you took it like i was a novice.

---

### Post by dbott67 on 2005-10-04
Could you also provide a little more information as to how you connect to the internet?  I take it you're connecting via your local cable company (Cogeco, Shaw, Rogers, etc. --- I'm guessing you're Canadian as you mentioned google.ca)?  Most don't require any special software to connect to the internet (unlike DSL, which typically requires a PPPoE client), but I just want to be sure.

This information will allow people to post more specific details as to what commands to type, etc.

You can also use the grahical tool to check the status of your network interface: **System -> Administration -> Networking.**  Highlight the ethernet card & select **ACTIVATE**.

-Dave

---

### Post by abdulisse on 2005-10-04
Umm i suppose i should have done that. I do live in Canada, Ontario, and my ISP is Shaw Cable. Basically i have that blue modem and i have a blue network cord, those typical normal ones. 

From the network cord it goes straight into my Laptop in the back of it where my PCI card is. 

I hope this helps.

Thanks..

---

### Post by dbott67 on 2005-10-04
According to the [shaw.ca support page]("http://www.shaw.ca/en-ca/CustomerCare/InternetSupport/Residential/GettingConnected.htm"), you should just be able to connect your computer to your modem (and make sure the modem is connected to the cable outlet) and you should be up and running.

Assuming that Ubuntu detected your ethernet card, the 2 areas I'm thinking are:

1. Ehternet interface is not activated or not obtaining IP address (follow odin's instructions above).
2. Cable modem may need to be reset if you can't get an IP address (just turn off power / unplug for a minute or two).

If, however, the graphical display does not show an ethernet interface, then we'll need to load the drivers for your card.

According to the HP site, the ethernet driver is: [National Semiconductor DP83815/816 10/100]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?dlc=en&lc=en&product=375243&lang=en&cc=us&os=228") MacPhyter NDIS 5.0 Miniport Driver (for Windows 2000/XP).  According to [linuxforums.org]("http://www.linuxforums.org/forum/post-164567.html") there is support for this nic, so I think the card just needs to be activated.

-Dave

---

### Post by abdulisse on 2005-10-04
Thank you Dave, i will try all these out.

---

