---
title: "Wireless bug/ General intro"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Laramie1997 on 2010-04-24
I know that there is a networking section already, but I feel that my very first post on this forum should go here. I've grown up around computers in general, but like many, I have been severely limited in the operating systems I've used. I started in Windows 95 and have worked my way up the mountain side from there, so saying that I know practically nothing about Linux would be an understatement at this point aside from some light reading here and there. If it were not for some of my classes that I'm taking while on the certification journey for networking, it has become clear to me that I need to submerse myself in the Linux OS as it is a most handy tool to have at my side. 

That being said, I started with Karmic and am now in beta 10.04. Everything went pretty good with the Karmic install, but I was having a problem with my wireless card driver for my system. After talking to some friends and a couple of professors, I decided that I would try the beta OS and see if my issue was common enough to have been included in the change. For the most part, it looks like it has been.... somewhat.. 

My system that I've chosen to boot with is an HP DV6z with the specs in my sig. The main concern here is that I have an Atheros wireless card. Under Karmic, the NIC would function correctly for awhile and then it would fail. Usually, it would just drop the network connection and would not allow me to reconnect with out restarting the system. After some online research, I found that most Atheros card and WPA2 encryption methods have issues under Karmic. Now that I'm booting the beta (Xubuntu) It hasn't kicked me off of the network one time. Just like Karmic though, the signal strength has been weak compared to what it is under Windows, and my quick launch button will flash from blue to orange during data activity on the card. The light doesn't bother me. In fact, it reminds me of the status lights on our copper cards and that's alright with me. My issue now is the weak signal. From where I'm sitting now, I should have be at full strength, but under beta, I'm sitting at 2 bars when it should be 4. 

My main question right now is that when 10.04 gets released, will the be a good chance that a proprietary driver will be released, or am I going to have to look at other options? 

I might add that I'm not new to forums at all, so while this may seem like a newbie post, I'm actually far from it. I was just a little confused as to where this particular post need to go. :D

Thoughts, ideas,  and comments would be great. 

Thanks,
Laramie

---

### Post by petert33 on 2010-04-24
Unlike Laramie I am a newbie for Linux and an ordinary user of Windows and OS X. 
I too have a wireless router access problem that doesn't exist on the two Windows machines I am trying Xubuntu 9.10 on. 
Forum members have been kindly offering advice and instruction but currently I am pinning my hopes on 10.4.

---

### Post by Laramie1997 on 2010-04-24
Wow. Tough crowd.

---

### Post by undecim on 2010-04-25
It's probably just that Ubuntu is reporting the signal strength differently. Do you have any slower connection speed, or any places that you can connect with Windows but not Ubuntu? If everything is the same except for what the network manager says the signal is, then the difference is likely just nominal.

---

### Post by Aearenda on 2010-04-25
I don't know your hardware at all, but most Atheros wireless cards use the open-source ath5k driver now. This is improving steadily, but there are times when it drops connections for me, although always in a way that does not require a reboot.

I don't think there will be a proprietary driver for Linux released just for your hardware. It is possible to compile the older madwifi driver still, and its seems to be more reliable but it reports lower signal levels than the ath5k driver for me on the same hardware.

Some cards use the ath9k driver - I have no experience with that.

The solution to your problem may be to use the Windows driver, and ndiswrapper. Ndiswrapper is a 'shim' that (usually) makes Windows network drivers work with Linux.

I'm hesitant to offer specific advice since I don't have the same hardware as you. I'd update the 10.04 installation to the latest state, and try again. We are so close to release that it is very unlikely there will be any change in this area between now and final.

---

### Post by Laramie1997 on 2010-04-25
Under Karmic the wireless would connect and work for a few minutes and then kick me all the way off of it. Under 10.04, it's just a weak signal so far. Until I made a change.

I went into the software center and searched atheros.... There is an app that does what the last poster said I think. All I had to do was tell it what driver off of my other partition to use and the signal issues have gone away. It might be a basic fix for others out there, but I dunno. Hardware can be kinda tricky sometimes.

---

