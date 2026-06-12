---
title: "Need help getting my wireless network going"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Rickncel on 2009-05-19
Ok first off i am VERY new to Linux so please be nice ):P. 2nd Ive looked through many forums and tutorials and found many great pieces of information and i don't know if im just not following them right or my problem is unique. so here goes.

I installed Ubuntu 8.04 (think i read somewhere that it was also called Hardy)and my biggest battle is getting my WAP set up. I am using a Netgear wap that is running on my wife's XP machine as a server/ internet port. and sadly i am sharing a dial up connection through the network. (sad but true i know)i already have another laptop running XP that is on the network and it works fine. but i cannot seem to get the Linux box to connect. when i looked online its said that i have to install a package called WPA supplicant which confused me at first since my network is un-secure meaning no WPA. So i tried downloading and installing the WPA supplicant anyway, but i haven't figured out how to install anything but debian files (which will probably be another post). Any help would be Much appreciated this is driving me nuts. And if you need any more info ask and i will tell you anything i can thank you in advance.)

---

### Post by HDave on 2009-05-19
Can you please clarify something -- Are you saying that you have  Windows XP boxes that are connecting to a WAP or are you saying that you are using internet connection sharing from a Windows XP box?

I would expect that the WAP is connected to your router (or is your router) and that all three computers connect to the WAP to share the internet connection.

On a side note -- wireless connectivity improves with every Ubuntu release so you may want to try 8.10 or 9.04.

---

### Post by Rickncel on 2009-05-20
okay i hope this is what you mean. I have a desktop running xp that the router is attached too and that is the only computer that is actually hooked up to a phone line. the other computers (1 running xp that works fine and the other is running hardy) are using wireless network adapters. does that help? p.s. thankyou for your response.

---

### Post by nhasian on 2009-05-20
i also encourage you to install ubuntu 9.04.  most likely you'll find that it fixes your wifi automatically.  in 8.04 there was a lack of support for some of the newer atheros and broadcom adaptors.  to see which adaptor you have in your computer in a terminal type:

```
lshw -C network
```

---

### Post by 3rdalbum on 2009-05-20
I agree, install Ubuntu 9.04 (or upgrade to 8.10 and then to 9.04). Always use the latest version of Ubuntu because it contains the latest drivers for the latest hardware.

But until then, did you look in the network manager applet on your panel to see if your network was listed? The network manager is towards the right on your top panel; it probably has a picture of two computer screens or a picture of an Ethernet cable with a circled cross. Click that and see if your network comes up.

---

### Post by xavierp94 on 2009-05-20
> **nhasian said:**
> i also encourage you to install ubuntu 9.04.  most likely you'll find that it fixes your wifi automatically.  in 8.04 there was a lack of support for some of the newer atheros and broadcom adaptors.  to see which adaptor you have in your computer in a terminal type:

```
lshw -C network
```
I also agree, version 8.04 of Ubuntu was not compatible with my wireless card. Seems that they added new drivers for Atheros wireless cards in the 9.04 release.

---

### Post by Rickncel on 2009-05-21
well since i am on dialup until my 9.04 cd gets here i want to see if i can get this working. when i go into network manager it sees the network and i was able to install the drivers for my airlink wireless card using ndis wrapper. thanks again for the help i need all i can get.

---

