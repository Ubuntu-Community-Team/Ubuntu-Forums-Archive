---
title: "Belkin Wireless Network Card F5D7000"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by TonyVF on 2008-04-24
Hello all - first of all this is going to be rather a long post so anyone who takes the time to read I tahk you in advance

To I'm trying to get my Belkin wireless G 54mb f5d7000 card working on the latest release of Kubuntu

I've been a developer fo some 15 year (however on Windows) and really love Kubuntu and want to switch to using it at home.  With having a family PC , I need to convince them that this is going to be a good move and get buy in. (trying things out on another PC) I've got the Kids games to work , instant messaging, office and Virtual box.

Before I make the final switch I was running the latest Kubuntu live CD in the target machine and it did not recognise the wireless network card.  I read about the ndiswrapper and applied it to the belkin drivers supplied with the card like so:-

sudo ndiswrapper -i belkinwhatever.inf
sudo modprobe ndiswrapper
***************************
At this point I got a segmentation fault - Poo !
*******************


so I do an lspci on my system and get

02:04.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

I've seen someone else suggest that this is a realtech chipset

So after a reboot I do

Install realtek driver:
sudo ndiswrapper -i net8185.inf

Make it work with your card:
sudo ndiswrapper -a 1799:700f net8185

Reload ndiswrapper module:
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

See if you have a wireless interface:
iwconfig (should report wlan0 as wireless)

and now iwconfig gets me :-

iwconfig gets me 

wlan0 IEEE 802.11g EESIDff/any

Mode:Auto Frequency:2.1412 Ghz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:-2147483648 Sensitivity=0/3
RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I presume this looks good.

Now I go to my network control panel and see wlan0 listed and then go and set the SSID and encryption key.
After apply the settings it takes a very long time for the network to restart.

BUT I STILL HAVE NO WIRELESS CONNECTION !

So... id do

iwconfig wlan0 mode managed
iwconfig wlan0 channel 11
iwconfig wlan0 essid networkname
sudo iwconfig wlan0 key FEFEFEFEFE - not my real key.

It show the key when I iwconfig but STILL No connection.

1. Someone else seemed to suggest that event without me going into the network control panel it would attempt to find the network and then prompt for the key is this so ?
2. Just because is see a wlan0 does this mean the drivers have accepted my wireless card
3. What do I do now I AM DESPERATE TO LEAVE WINDOWS !!

Thank you for taking the time to read this any help greatfully received 
TA

---

### Post by TonyVF on 2008-04-25
I should have searched more thoroughly , this thread did it for me

[SOLVED] Belkin F5D7000 v7000 - Here's my solution

---

