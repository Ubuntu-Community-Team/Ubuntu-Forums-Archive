---
title: "[SOLVED] Bluetooth dongle not working"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by LinuxGEEK7288 on 2007-09-17
Ok first off i would like to apologize if this is answered somewhere else, but i've read all i could and at this point i've just become overwhelmed. So if there is another forum with the answer i need please point me in the right direction.

Ok so heres my problem i have a Motorola Razar and an Hp Ipaq running windows mobile( gross i know but it works for what i need) and they both have Bluetooth so i figured i could use my workstation to do stuff like backup files or transfer photos and music. So i bought one of those USB bluetooth dongle things. Then i used synaptic and got all the necessary files i think. what i've got is:

bluetooth
bluez-gnome
bluez-pin
bluez-utils
gnome-bluetooth
nautilus-sendto
obexftp
obexpushd
bluetooth file sharing

and then a bunch of libs.......i'm not sure which ones i needed so there are quit a few

libbluetooth2
libbtctl4
libgnomebt0

and then a completely random package that I'm not sure why i have but at this point and afraid to remove

multisync

Okay so i downloaded all of these and if i use hcitool scan i can see all my devices and in nautilus if i right click on a file and click send to i get the option to send files to all my devices but when i hit send about a minute or so later it says devices dose not support file transfer. And if i attempt to use my Ipaq to connect my computer shows up in the list of devices but when i look to see what services are available it says there aren't any, and if i try to send files from my Razar i get the option to send it to my computer but when it trys to send it, the phoes says its sending but 10 min later still notthing has changed and eventual the phone either times out or says its lost connection with object. 

So at this point i've tried all i know, and i'm at my wits end. So i'll will be very thankful for any help.

thank you in advance

Oh and if anyone knows of a program that would allow me to use my devices as a network drive or some sort that would be really cool

---

