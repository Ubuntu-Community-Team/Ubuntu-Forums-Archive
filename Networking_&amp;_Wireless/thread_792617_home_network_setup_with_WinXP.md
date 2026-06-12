---
title: "home network setup with WinXP"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by zrs3 on 2008-05-13
I have and love Gutsy and now Hardy, but my parents are still stuck on WinXP. I want to have their internet access on my desktop in my room. The Dell with main internet connection is in basement and I'm on 2nd floor of my house with phone cord jack and 10/100 ethernet card. How can I get internet all the way upstairs and into my computer? I really don't want to give up ubuntu to go back to XP just for internet. Any advice on how to get internet on my Hardy desktop?

---

### Post by helgman on 2008-05-13
It depends on what kind of connection you have to the Internet (dial-up, DSL ...) and how you would solve it in XP (or would you just use the computer in the basement?).

Regards,
Helgman

---

### Post by superprash2003 on 2008-05-13
If you have DSL.. then you could get a wifi router and connect it to where the windows pc resides..THen get a wireless LAN card for your ubuntu pc and connect wirelessly to the router for internet access..

---

### Post by Shiv Prakash on 2008-05-13
First you have to share that internet connection in windows XP...that can be easily achieved by going to connection manager and right clicking on the connection you want to share (i am a bit rusty about the specifics but this is the general way to go about it)

You will then have to setup static IP on your ubuntu machine
1. Uninstall Network Manager (this created a lot of problems you are better of without it)
2. Edit your /etc/interfaces and setup your static IP and your default gateway should point to the XP macine on which internet is shared.
3.You should be up and running in no time  :)

BDW i too am doing this so i know it works

lemme know what happens you could maybe PM me or something

---

### Post by zrs3 on 2008-05-15
I am still at school, so I haven't been home to try any of these things, but I will keep you all updated as I make progress. I appreciate all the help/advice, tho.
In response to questions...my parents have cable internet through the same company as our cable television. I have both a telephone jack and a cable hook-up in my room, and I have a 10/100 ethernet card in my ubuntu PC already. Is there anything I can do with any of those?

---

### Post by zrs3 on 2008-05-17
I'm home and everybody that I've talked to locally has just said to put a wireless card into the ubuntu pc and a wireless router for the WinXP pc to send it upstairs...if there's any other suggestions, I'd appreciate it.

---

### Post by helgman on 2008-05-17
If your cable-hockup is anything like mine you need a modem to be able to connect your Ethernet card to the cable-outlet (unless you are going to use dial-up but my guess is no) and if your cable company is anything like mine they won't let you have more then one public IP-address so that solution wouldn't be any good anyway.

So ...

Solution A: Involves a cable that runs from your upstairs computer to the basement XP room where ... 1) it goes into a home router/switch that connects both computer to the Internet or 2) it goes into a spare Ethernet card in the XP machine. If you go for two, all traffic will go through the XP machine AND the XP machine must be powered up for you to have Internet access. Also note that you sometimes need a crossover-cable for this setup ... depending on the Ethernet cards ability to auto sense.

Solution B: Do the wireless setup that has been suggested to you. It seems simple enough but make sure that you place everything so that you get the most out of your wireless ... it all depends on obstacles, distances, network cards, radio frequency and the bouncing of radio signal.

To bad I can't come up with a constructive Solution C ...

Regards,
Helgman

---

### Post by zrs3 on 2008-05-27
helgman,
thanks for the advice. i think i'm going to go with the router/switch option, but it's just a matter of finding the cheapest effective option...again, I'll keep everyone updated as I try different options. Thanks again.

---

### Post by Iowan on 2008-05-28
> **helgman said:**
> To bad I can't come up with a constructive Solution C ...
Solution C: power line NIC - you'd need two.  At $70/ea, they are a pricey option.

---

### Post by zrs3 on 2008-05-29
I just spoke with a guy from my cable company (who provide the internet). He said the USB port on the back of the modem will provide internet, just through a USB port on the computer instead of ethernet port...anybody know anything about the effectiveness of a set-up like that?

---

### Post by zrs3 on 2008-05-31
well, I tried the USB option, and it didn't work very well at all. So I'm buying a wireless router from newegg.com, and setting that up with ethernet cable. I'm going to dual-boot ubuntu with XP on the new computer (I need iTunes for my 6G iPod classic). If I get the networking figured out in XP on my computer, could I still access internet and networking on the ubuntu side of the PC?

---

### Post by julianna on 2008-06-10
Greetings from Muskegon, the non-tech way is to get one of those jacks that plug into any wall outlet and plug the phone cord into that.  Roughly 39.99 at any store. Or, if you have DSL add an ethernet adaptor to the phone jack and run a hardline to your PC.  Now, if your parents have gone wireless, and your pc doesn't have that built in, a standard USB wireless adaptor should pick up the established network.  Mine did.  Best of Luck.

---

### Post by helgman on 2008-06-12
> **zrs3 said:**
> I'm going to dual-boot ubuntu with XP on the new computer (I need iTunes for my 6G iPod classic). If I get the networking figured out in XP on my computer, could I still access internet and networking on the ubuntu side of the PC?

Do you that if you reboot into Ubuntu, will you still have Internet access? The answer to that question should be yes, unless you set up the network in some Ubuntu-unfriendly way (whatever that could be).

Good luck!

Regards,
Helgman

---

### Post by linux6994 on 2008-06-12
You can run XP on your Ubuntu via wmware-player or Innotek Virtualbox. If you are looking for itunes use via XP the best bet would be vmware-player. The procedure for installing it is here: [http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710](http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710) . Its says gusty but it I used it for Hardy. It works fine. So once you use a wireless or wired router you will have the XP machine up and running as well as your Ubuntu. You will be able to share files, printers and the net without any troubles. Just look at this post [http://ubuntuforums.org/showthread.php?t=818061](http://ubuntuforums.org/showthread.php?t=818061)

Good Luck

---

### Post by zrs3 on 2008-06-14
I have the new computer built, with the help of a friend working in Tech Support for a college. 500GB SATA HDD, 2.4GHz AMD processor, 2GB DDR memory, and a "help desk" copy of XP for $20, so I'm dual booting with Windows and Ubuntu 8.04. I got a Netgear Wireless G Router, and have it connected via ethernet to my computer, the modem, and the original XP computer. they're networked fine, and I am having no problems beyond a weak internet signal, but that's a provider issue. Thanks for all the help, and just ask if there's questions about how I set it up.

---

