---
title: "Wireless card on 7.10"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by rbsis on 2007-10-27
Hello, I have been using Ubuntu 7.03 on my PC for a little bit now and I wanted to install 7.10 on my old Omnibook 6000. Right know it is installing the base system. I just want to know how I would get my wireless card to work with it, it is a Zonet Wireless Cardbus Adapter 54 mps. Model #: ZEW1502.

I heard of ndiswrapper could someone help me understand this better?

---

### Post by rbsis on 2007-10-27
Anyone?:(

---

### Post by rbsis on 2007-10-27
It's almost finished installing and I downloaded ndiswrapper 1.48, should I put it on a disk and run it?

---

### Post by rbsis on 2007-10-27
C'mon guys, please help me. It's "Cleaning Up" the installation (97%) Please help me :'(

---

### Post by rbsis on 2007-10-27
It's done and I have no idea what to do, please help me I really need it. :(

---

### Post by kevdog on 2007-10-27
Please post 

lspci -nn
lshw -C network

A little bit of reading or searching on the forums would also help.  I dont know if you need ndiswrapper or not, however there are a ton of ndiswrapper threads in the forums.

---

### Post by rbsis on 2007-10-27
THANK YOU FOR POSTING!!!!

I looked at the other topics but none of them had my wireless card.

Are you saying I should type that in the terminal?

---

### Post by Condoulo on 2007-10-27
what is the chipset of your wireless card?

---

### Post by kevdog on 2007-10-27
yes

---

### Post by rbsis on 2007-10-27
I put them in the terminal and I got a lot of stuff, I can't copy and paste it cuz I don't have internet on it yet. What should I be looking for?

---

### Post by Condoulo on 2007-10-27
try looking for anything that will relate to your wireless card
if you can find anything similar to this:
 wireless=RT2500USB WLAN
driver=RT2500USBSTA 
it would be really helpful 
(I checked [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/), and it seems like Zonet uses Ralink chipset a lot.)

---

### Post by rbsis on 2007-10-27
Okay I will look for that and post my results

---

### Post by Condoulo on 2007-10-27
ok. :) I do know that as far as my D-Link goes, it has the Ralink chipset, and works with no driver installation or anything, and my guess is that Ubuntu has Ralink chipset support by default.

---

### Post by rbsis on 2007-10-27
I could find what you wanted me to...

How would I scan for connections then?


Thanks you for baring with me and being a great help!:)

---

### Post by Condoulo on 2007-10-27
yup, your card is Ralink chipset
System > Admin > Network 
highlight Wireless Connection
Click properties
disable roaming mode
and enter network name, key, select DHCP
or, if you tend to roam between wireless networks, on the sys. tray, click on the network icon, and it should bring up a list of networks.

---

### Post by rbsis on 2007-10-27
I found out it uses a Marvel chipset...
So that means I will have to use ndiswrapper any idea how to get that working?

---

### Post by Condoulo on 2007-10-27
I found out it uses a Marvel chipset...
So that means I will have to use ndiswrapper any idea how to get that working?

Marvel? hmm... I thought you said it had the same results as me for chipset.
well then umm..... lemme check

---

### Post by rbsis on 2007-10-27
Oh sorry, when i said it "could" It was a typo I meant to put "couldn't" I'm soo sorry!'


Also when I goto network there is only "Wired Connection" and "Modem Connection"

---

### Post by Condoulo on 2007-10-27
Well unfortunatly, all the wireless cards with Marvel chipset on that site don't work
so the next step would be to try ndiswrapper

---

### Post by Condoulo on 2007-10-27
do you have MSN or AIM? and a flash drive/way to transport files between the laptop and your current machine?

---

### Post by rbsis on 2007-10-27
I'm using blank disks right know, I have a ton left.

Yes, my MSN is 
[email]cyborg_2424@msn.com[/email]

---

### Post by Condoulo on 2007-10-27
Ok, I should have sent a request.

---

### Post by rbsis on 2007-10-27
I'm on and I accepted you, Tyler?

---

### Post by Incarnadine on 2007-12-07
I have the same exact card as you rbsis and I really don't have any idea of how to get it to work. Do you use Jabber by any chance? Maybe you could help me out with this "ndiswrapper" that's needed to run this card. My Jabber account is [email]Incarnadine0@gmail.com[/email]

Or if anyone else could tell me what I have to do that would be great! Thanks guys:popcorn:

---

### Post by rustybronco on 2007-12-07
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by Incarnadine on 2007-12-13
Thanks for the link to the guide, but with it I still couldn't get my card to work. I installed "ndiswrapper" properly through the terminal, but I couldn't figure out the part where I have to install the .inf file. So I resorted to downloading the graphical program off of the Add/Remove... files for installing Windows Wireless Drivers and tried installing my .inf file with that, but still nothing. I selected the .inf file on the Zonet CD with the program and hit install, but it did nothing. To be honest I really don't know what I'm doing and I never thought installing a wireless card could be so hard. If anyone knows any shortcuts or hints please let me know. Thanks for the help and sorry for my noobness.

---

### Post by buccaneere on 2007-12-13
> **Incarnadine said:**
> Thanks for the link to the guide, but with it I still couldn't get my card to work. I installed "ndiswrapper" properly through the terminal, but I couldn't figure out the part where I have to install the .inf file. So I resorted to downloading the graphical program off of the Add/Remove... files for installing Windows Wireless Drivers and tried installing my .inf file with that, but still nothing. I selected the .inf file on the Zonet CD with the program and hit install, but it did nothing. To be honest I really don't know what I'm doing and I never thought installing a wireless card could be so hard. If anyone knows any shortcuts or hints please let me know. Thanks for the help and sorry for my noobness.

This thread got me connected with two stubborn wireless machines...

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

...and will probably get me through with 3 more yet to be configured. The OP seems frequently online to help too...

---

