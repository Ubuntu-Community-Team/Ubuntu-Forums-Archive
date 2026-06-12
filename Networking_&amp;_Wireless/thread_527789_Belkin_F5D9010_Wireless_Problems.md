---
title: "Belkin F5D9010 Wireless Problems"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by rustyjazz1938 on 2007-08-17
Howdy,

First, it must be know that I am new to linux, but have some computer knowledge (just enough to be dangerous as I like to say...)

My problem is, I have a laptop (my old college issued Compaq evo n800w) with a fresh installation of Kubuntu Feisty 7.04, and a Belkin F5D9010 Ver 3000 PCI Wireless card (The lspci output shows a Ralink RT2600 MIMO Chip, and the windows disk I have uses rt61.inf). I have read on some of the forums and have attempted to use Ndiswrapper to mount the inf file to my laptop. I physically removed the installed rt61 drivers from the modules file using the 'rm' command. I am able to get ndiswrapper to recognize the card with the windows driver I have, and am able to insert the driver into the kernel using modprobe. The computer than recognizes the 'wlan0' in 'ifconfig'. I am able to see the hotel wireless (I work in the field alot...) and run dhclient, but when I open  konqueror, I am unable to connect to the network. I get a white screen saying there was an error connecting to whatever website I try. I do not even get to the hotel contract screen for using the wireless network.

The wireless is the only method of connecting to the net with my linux laptop. I have been using my windows work machine to connect the web. I am completely baffled by the actions of my machine and have no clue where to turn. Any help or insight would be very greatly appreciated.

Thanks,

Rusty

---

### Post by NULL712 on 2007-08-17
I am having similar problems with my belkin F5D9010. I have two laptops that I am trying to use this card on, the card works for me as soon as I slide in the card but when I go out side network manager says that the connections are 0%? One of the connections is around 68-70% but when I try to serf the web firefox tells me it can not connect to the server. 

hard ware: Sony Vaio 1G of RAM P4 ubuntu 7.04 I haven't rememberd the model # because I just got it.

Toshiba Tecra 8000 128MB of RAM P2 xubuntu 7.04

both computers have the same issue with this card. I have even tried it with my Dell Inspiron 6000 that came with wireless but just wanted to see if it was the pcmcia slots on the other machines were defective, but to no avail the card did the same thing it did on the other two. If you go to this link [http://linux-wless.passys.nl/query_hostif.php?hostif=PCMCIA]("http://linux-wless.passys.nl/query_hostif.php?hostif=PCMCIA")
 it says only the belkin F5D6020 and F5D6020 v.2 work.

If there are any networking adept people reading this please respond asap

Thanx

---

