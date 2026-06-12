---
title: "Wireless Problems with Ubuntu 9.04"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by TerryD15 on 2009-09-09
I have just installed Ubuntu 9.04 on my HDD but now problems with my Wireless router connection. I Know that this is a perennial problem but as an Ubuntu Newbie I have researched and read much on the issueson various forums and threads, I understand some but not all of the advice.

My problem is that although my wireless card is recognised and appears to be operating ok, and it recognises my router (D-Link G604t) it will not connect.  I use WPA security but Network Manager in Ubuntu does not offer WPA in the drop down box, only various WEP and LEAP security systems.

I have tried to implement Wicd but Terminal says it is not there so I downloaded wicd and have the .deb file but do not know what to do with it.

I can and do connect via my other laptop using wireless under XP 32. 

Please be gentle with me, remember I am a complete novice with Linux and am easily confused.

---

### Post by tomBorgia on 2009-09-09
Hi TerryD,

I'd use synaptic to install wicd... (system > administration > synaptic package manager) - You can customize the WPA settings better in wicd so it's worth a try.

Tom.

---

### Post by roger_1960 on 2009-09-09
Hi

wicd is not pre installed, but is best installed using the synaptic package manager.  Use system>administration>synapticpackagemanager and find the package using the search facility.  Check the box for installation and off you go. (This of course requires an internet connection.) This method is better than installing the .deb and it manages the software, allows easy removal and updates.

---

### Post by hockeytux on 2009-09-09
Terry, I had exactly the same problem when configuring a new router and connection for the first time. My router (also a D-Link) was according to the specs only supported by Windows and Mac but thats what my provider gave me.

I ran into the same problem that you have now and solved it by configuring the network on an old laptop running XP, then it worked for my Ubuntu desktop as well :)

---

### Post by terryd on 2009-09-09
Thanks for your suggestions they are greatly appreciated but I've tried using a wired network connection and asked Synaptic to search for wicd but it just seems to search locally and does nothing else.  What am I doing wrongly?  I need to understand so that I can solve problems better in future.  I am obviously missing something very basic.

---

### Post by terryd on 2009-09-09
I should perhaps have pointed out that this is a long standing home network and has worked well with both wired and wireless links.  I use normally XP machines and my wife uses her beloved Mac, all without problem.

---

### Post by gradinaruvasile on 2009-09-09
> **TerryD15 said:**
> I have just installed Ubuntu 9.04 on my HDD but now problems with my Wireless router connection. I Know that this is a perennial problem but as an Ubuntu Newbie I have researched and read much on the issueson various forums and threads, I understand some but not all of the advice.

My problem is that although my wireless card is recognised and appears to be operating ok, and it recognises my router (D-Link G604t) it will not connect.  I use WPA security but Network Manager in Ubuntu does not offer WPA in the drop down box, only various WEP and LEAP security systems.

I have tried to implement Wicd but Terminal says it is not there so I downloaded wicd and have the .deb file but do not know what to do with it.

I can and do connect via my other laptop using wireless under XP 32. 

Please be gentle with me, remember I am a complete novice with Linux and am easily confused.

What laptop u have?

---

### Post by tomBorgia on 2009-09-09
> **terryd said:**
> Thanks for your suggestions they are greatly appreciated but I've tried using a wired network connection and asked Synaptic to search for wicd but it just seems to search locally and does nothing else.  What am I doing wrongly?  I need to understand so that I can solve problems better in future.  I am obviously missing something very basic.

I'm assuming you have a working wired connection - i.e. you can get google etc. and by "search locally" you mean from the installation CD?

If so then (in synaptic) just go to settings > repositories and uncheck the install CD... ok it then "reload" then search.

If not (You've no wired connection) then I'd work out why that wasn't working "out of the box" before worrying about the wireless!!!

---

### Post by terryd on 2009-09-09
> **tomBorgia said:**
> I'm assuming you have a working wired connection - i.e. you can get google etc. and by "search locally" you mean from the installation CD?

If so then (in synaptic) just go to settings > repositories and uncheck the install CD... ok it then "reload" then search.

If not (You've no wired connection) then I'd work out why that wasn't working "out of the box" before worrying about the wireless!!!
Toshiba Satellite SPA10

---

### Post by gradinaruvasile on 2009-09-09
It is an older model?

What is the output of lspci?

---

### Post by LewRockwell on 2009-09-09
> **TerryD15 said:**
> I have just installed Ubuntu 9.04 on my HDD but now problems with my Wireless router connection. I Know that this is a perennial problem but as an Ubuntu Newbie I have researched and read much on the issueson various forums and threads, I understand some but not all of the advice.

My problem is that although my wireless card is recognised and appears to be operating ok, and it recognises my router (D-Link G604t) it will not connect.  I use WPA security but Network Manager in Ubuntu does not offer WPA in the drop down box, only various WEP and LEAP security systems.

I have tried to implement Wicd but Terminal says it is not there so I downloaded wicd and have the .deb file but do not know what to do with it.

I can and do connect via my other laptop using wireless under XP 32. 

Please be gentle with me, remember I am a complete novice with Linux and am easily confused.

reboot your LAN devices(cable/dsl modem, routers, switches, etc)

if that doesn't work then you might open the wireless network(disable WPA) and see if you can connect then

and, given that WPA now has a 60 second hack...

[http://www.pcmag.com/article2/0,2817,2352231,00.asp](http://www.pcmag.com/article2/0,2817,2352231,00.asp)

you'll want to change your security protocals anyway...

.

---

### Post by terryd on 2009-09-09
> **gradinaruvasile said:**
> It is an older model?

What is the output of lspci?

I have no idea what a 1spci is never mid what it'e output is,  Sorry to appear so ignorant  but as I said I am a complete Linux newbie.

Regardd

Terry

---

