---
title: "wireless network problem"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by OLT on 2006-08-02
ok im new to ubuntu and mostly linux in general and i have been solving most of my problems for a month now with reading carfully and an ethernet cord but now this one has me completely stumped so i hope you people out there can help. Ive got a this computer connected to a home wireless network in windows using a linksys wireless b usb reciever and it work perfectly there. I can`t find it in the device manager but when I run wireless lan assistant in sudo using gksudo wlassistant i get networks that are mine and around my area that im used to see. So i see my network and I attempt to connect to it. I put in the neccesary information that it asks for insert my wep key 128 bit encryption hit ok and i wait and wait. After about a minute i get the message in the bottom of the window connection failed. Just to test out something i disabled my wep key and i still get the same problem no error to go off of just connection failed. Im at a complete loss every attempt to fix it has ended in failure. Interestinly this device worked with my friends powerbook and his network which is unencrpyted though he had installed ubuntu 5.10 and mine is offcourse version 6.06 If i left out any info that would help you solve this let me know. Some info that might help

My computers wireless reciever is a linksys wireless b usb adapter i dont know the exact model though its provided through comcast
My network is wep encrypted
The device seems to be receiving data though it doesn`t connect to my network
It worked with a microsoft wireless g tranmitter with services provided through version in the powerpc edition of ubuntu breezy badger
The light that says power is on the light that says link is constantly blinking
My isp is comcast and there are 3 other computer on the network all windows computers

you help would be greatly thanked and praised
OLT

ps i won`t be able to respond right away though i will get back asap

---

### Post by encompass on 2006-08-02
you sond like you have my card... is it the gold or the silver.
the blinking light means your not connected to a network.  it need to be on to show you have associated.
Try running this program from the command prompt:
wifi-radar
if you don't have it installed I would recommend doing that threw synaptic.
This program can show you errors very well if they happen and your running it from the command prompt.
Hope this helps.
The other option is to do it manually and see if you can connect that way.
I can help you with that... but lets see if your first try here works.8)

---

### Post by OLT on 2006-08-02
no the card is not the same but that program did work after a little tweaking i had to enter all my settings manually but it still works great. I am exsperiencing 1 thing that if you could help me clear up that would be great.i would like wifi radar to automatically connect me when ever i start ubuntu but i am not sure how to do this but still thanks for finding this program im happy my wifi works now

---

### Post by encompass on 2006-08-02
I think it is called deamon mode... type man wifi-radar aditionaly you would want to put the setting in interfaces section... surch the forums on how to load network setting at boot time.

---

### Post by encompass on 2006-08-02
Or you could try network manager... that connect to anything automaticaly... loook it up with synaptic... "network-manager"
Does it help?

---

### Post by OLT on 2006-08-04
the network manager worked to connect automattically now i dont have to worry about it thanks for the help on this problem

---

### Post by luckypirate on 2006-08-04
I seem to be having a similar issue though with a diffrent card. Im using a belkin F5D6020 and i can see the networks just like he could and i get the same error message. I can however see the card in the device manager but it shows up as Texas Instruments PCI1510 PC card Cardbus Controller, and the device type and capabilities both say unknown. I am a complete newb to linux, and I was unable to find the wifi-radar ap in the synaptec list. 

Id appreciate any detailed help in finding and using that program. 

Thanks

---

### Post by encompass on 2006-08-04
I recommend you start a new post on the subject.  More people will see it.
Thanks.

---

