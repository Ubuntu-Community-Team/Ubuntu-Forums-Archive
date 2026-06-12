---
title: "ADSL problem"
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by swong1 on 2005-09-26
Dear all,

I have searched this forum and can't find a thread that address my specific problem, so I'm starting a new one. I'm a newbie, perhaps the problem has been addressed but I don't understand the lingo. 

I have a dual-boot laptop (Dell 6000, Windows XP home & Ubuntu Hoary Hedgehog). Recently, I had broadband installed in my home. The service provider also provided an ADSL ethernet bridge/router modem (this is the description on the label underneath the product) which is connected to my network card. The modem works fine with Windows, but doesn't work with Linux.

Here is what I have done so far:

*sudo pppoeconf*

Go through the setup process, no problem here, then,

*pon dsl-provider*

I also activated the ethernet card via:

system->administration->networking

Here's the problem. The network connection icon shows that the connection is up, but firefox can't connect to the internet. Packets are sent to the modem, but none received. What gives? Do I need to download a special driver for the modem?

---

### Post by karuptdata on 2005-09-26
[QUOTE=swong1]Dear all,

I have searched this forum and can't find a thread that address my specific problem, so I'm starting a new one. I'm a newbie, perhaps the problem has been addressed but I don't understand the lingo. 

I have a dual-boot laptop (Dell 6000, Windows XP home & Ubuntu Hoary Hedgehog). Recently, I had broadband installed in my home. The service provider also provided an ADSL ethernet bridge/router modem (this is the description on the label underneath the product) which is connected to my network card. The modem works fine with Windows, but doesn't work with Linux.

Here is what I have done so far:

*sudo pppoeconf*

Go through the setup process, no problem here, then,

*pon dsl-provider*

I also activated the ethernet card via:

system->administration->networking

Here's the problem. The network connection icon shows that the connection is up, but firefox can't connect to the internet. Packets are sent to the modem, but none received. What gives? Do I need to download a special driver for the modem?[/QUOTE]

Inside of your networking tab is your dns ip address set there? There should be 2 address there also do you have any type of router or anything of that nature in between the modem and the machine??

---

### Post by swong1 on 2005-09-27
Dear Karuptdata,

Thanks for your reply. In the DNS tab, there is only one address (192.168.1.1) under the DNS server field. The search domain is "home". Also, I am using dhcp, and the ip address, subnet mask and gateway address fields are all empty, if that helps.

The laptop ethernet port is connected directly to the router which in turn is connected to the phone line.

---

### Post by karuptdata on 2005-09-27
That could be what is possibly causing you this headache...the easiest way o fix this I found was i had to call my isp (QWEST) to get there dns addresses..so all that said to say this contact your isp and ask the for their dns addresses they should give you two a primary and a secondary. When you enter this information into the dns tab keep the 192. address....change those few things and let me know how it goes...

---

### Post by swong1 on 2005-09-27
Sorry for the double post. Please see below.

---

### Post by swong1 on 2005-09-27
[QUOTE=karuptdata]That could be what is possibly causing you this headache...the easiest way o fix this I found was i had to call my isp (QWEST) to get there dns addresses..so all that said to say this contact your isp and ask the for their dns addresses they should give you two a primary and a secondary. When you enter this information into the dns tab keep the 192. address....change those few things and let me know how it goes...[/QUOTE]

Since I'm still able to connect to the internet under windows, I found the DNS server in networking properties. I rebooted into Ubuntu and added the new address into the DNS server tab. Unfortunately, it hasn't solved the problem. Running *plog* gives the following error message, if it helps:

local host pppd [8025] : using interface ppp0
local host pppd [8025] : connect: ppp0 <--> eth0
local host pppd [8025] : couldn't increase MTV to 1500
local host pppd [8025] : remote message: unable to authenticate
local host pppd [8025] : PAP autheticate failed
local host pppd [8025] : connection terminated

---

### Post by sanjose on 2005-09-27
i have the same problem. 
someone in irc #ubuntu help me solve this.
but not sure if this will work on you.

for the solution:

1. sudo poff       #if you are connected
2. sudo mv /etc/dhcp3/dhclient-script   /etc/dhcp3/dhclient-script.bak
                       #this is only temporary you will rename it back to the original           
                       #name
3. sudo pon dsl-provider       #now connect to your ISP
4. ifconfig ppp0                   #check if all is fine
5. ping -c 3 [www.google.com](www.google.com)        #check if you can ping some site
                                               #if no problem then you can follow
                                               #next step
6. sudo apt-get install resolvconf
7. sudo poff
8. sudo mv /etc/dhcp3/dhclient-script.bak   /etc/dhcp3/dhclient-script
9. sudo pon dsl-provider


hope this will help.

---

### Post by swong1 on 2005-09-28
[QUOTE=sanjose]i have the same problem. 
someone in irc #ubuntu help me solve this.
but not sure if this will work on you.

for the solution:

1. sudo poff       #if you are connected
2. sudo mv /etc/dhcp3/dhclient-script   /etc/dhcp3/dhclient-script.bak
                       #this is only temporary you will rename it back to the original           
                       #name
3. sudo pon dsl-provider       #now connect to your ISP
4. ifconfig ppp0                   #check if all is fine
5. ping -c 3 [www.google.com](www.google.com)        #check if you can ping some site
                                               #if no problem then you can follow
                                               #next step
6. sudo apt-get install resolvconf
7. sudo poff
8. sudo mv /etc/dhcp3/dhclient-script.bak   /etc/dhcp3/dhclient-script
9. sudo pon dsl-provider


hope this will help.[/QUOTE]


Wow, what a detailed solution. Thanks Sanjose! I will try it and let you know if it works. Also, I accidently found a similar thread under Warty-Warthog:

[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

---

### Post by swong1 on 2005-09-29
[QUOTE=sanjose]i have the same problem. 
someone in irc #ubuntu help me solve this.
but not sure if this will work on you.
for the solution:
1. sudo poff       #if you are connected
2. sudo mv /etc/dhcp3/dhclient-script   /etc/dhcp3/dhclient-script.bak
#this is only temporary you will rename it back to the original           
#name
3. sudo pon dsl-provider       #now connect to your ISP
4. ifconfig ppp0                   #check if all is fine
5. ping -c 3 [www.google.com](www.google.com)        #check if you can ping some site
#if no problem then you can follow
#next step
6. sudo apt-get install resolvconf
7. sudo poff
8. sudo mv /etc/dhcp3/dhclient-script.bak   /etc/dhcp3/dhclient-script
9. sudo pon dsl-provider
hope this will help.[/QUOTE]
I'm at my wits end. None of the suggestions work. Adding DNS server addresses didn't work.
*ifconfig ppp0* gives the error message:
error fetching interface information : Device not found.
*ping -c 3 [www.google.com](www.google.com)* gives the error message:
unknown host [www.google.com](www.google.com)

---

### Post by sanjose on 2005-09-29
follow the other thread you found it is much better 

[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

---

### Post by swong1 on 2005-09-30
[QUOTE=sanjose]follow the other thread you found it is much better 
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)[/QUOTE]

I'm not sure if the thread I found will help, because I can't even ping google.

---

