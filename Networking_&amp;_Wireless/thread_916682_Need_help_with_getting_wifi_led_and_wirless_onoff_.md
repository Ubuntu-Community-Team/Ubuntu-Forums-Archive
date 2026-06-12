---
title: "Need help with getting wifi led and wirless on/off key in acer aspire 4720z"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by arunvir on 2008-09-11
Friends, I have got my wireless card working with ndiswrapper and it Works like a charm. 

All I need to know, something that I have not tried to know for the past 4 installs of ubuntu in my laptop is whether the wifi LED & the wireless key can be turned on/off , as I do want them. 

I did learn from searching the forum and on google that acer-acpi can be used to get the wifi led and wireless key working. 

As I have no prior experience on whether acer-acpi also overrides my ndiswrapper wireless drivers and installs its own drivers or I can use it to get my key and led working alone, I might need some advice and help in this issue. 

further I found that acer-acpi comes pre-installed in ubuntu, but I couldn't find anywhere like acer on my /etc/acpi folder(if that is where it installs by default).

If so I would also like to know how I go about getting my wifi LED / wireless keys working.

I'm also interested in any command line works that I could do to get them working without the acer-acpi........

I want to try everything by hand as I get it to work.

My laptop model is acer aspire 4720z. with running kubuntu.
wireless card:- atheros AR5007eg 
wireless drivers:- XP WHQL 5.3.0.67 sing ndiswrapper

Thanks in advance!!!!

---

### Post by arunvir on 2008-09-11
somebody bump in!!!!!!!!!!!! I need replies from guys who have done this or have knowledge about this..........

---

### Post by arunvir on 2008-09-11
Well I think It's always a good thing to google around till you find the thing you need............

I found what I needed and now not only my led glows............ but can glow in different blink rates........

I express my sincere thanks to the thread 

[http://ubuntuforums.org/showthread.php?t=715187](http://ubuntuforums.org/showthread.php?t=715187)

by felipefox=D>=D>

actually aspire 4720z and 4520 are nearly same it seems(I never knew it).

I added just following 2 lines to the file-"/etc/ndiswrapper/net5211/168C:001C.5.conf" and it started working
> 
gpioPinFunc1|3
gpioLedCustom|4

in the file-"/etc/ndiswrapper/net5211/168C:001C.5.conf" after the 
> 
sys_files|ar5211.sys 
NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
driver_version|,07/25/2007,5.0.3.67
BusType|5
SlotNumber|01
NetCfgInstanceId|{28022A01-1234-5678-ABCDE-123813291A00}

..................
..........
DriverDesc|NDIS Network Adapter
............


"driverdesc"  and everything works like a charm.........


mine was atheros 5211 drivers installed with ndiswrapper on kubuntu 8.04 hardy......... 

He has mentioned in his post for the 5416 drivers to be used in case of 7.10, the line gpioPinFunc1|3 will already be there, one has to just add
the remaining there.

Wireless key always used to work it seems. Only I didn't notice that till now.

Thanks to this forum and ubuntu, I'm slowly growing from a noob to be an expert.
:guitar::guitar::-({|=:-({|=:lolflag:

---

### Post by GibsonSGKing on 2008-09-12
:confused: ok, i installed ubuntu off of the official website, and have an acer 4620z. everything seems to work all right, except wifi. i know nothing at all about linux btw. everything installs fine until the sudo ndiswrapper -i net5416.inf part. then it just says ndiswrapper command unknown or something like that. plzzzzzzzzzzz help me, cuz im sick of vista. and if you could tell me how to get it to stop asking for my password every time i try to change something that would be awesome too. thanks!

---

### Post by arunvir on 2008-09-13
pal!!!!!!! first learn using synaptic or using the command line apt-get


for installing ndiswrapper

type the command from command line using a terminal application

sudo apt-get ndisgtk

(then enter your login password)
(if any error occurs with this step, reply back.

Google around on how to use synaptic and apt-get..... there'll be lot of help topics.....

Don't worry being a newbie, you ll get use to using ubuntu....
I was even sick of vista, so cheerup........


after installing ndisgtk(it automatically installs ndiswrapper... so don't worry)

goto the menu and try finding "windows wireless drivers" option somewhere...

use that to install 5416 atheros driver... after that try reporting back with screenshots on how it worked about..... I'll be happy to help you...

It'll add the driver and display a line below it whether the hardware is present or not...... If hardware is present, be happy and report back on how to use wifi........ or report back with your hardware configuration for me to help you.....
:):):):):):)

---

### Post by GibsonSGKing on 2008-12-01
> **arunvir said:**
> pal!!!!!!! first learn using synaptic or using the command line apt-get


for installing ndiswrapper

type the command from command line using a terminal application

sudo apt-get ndisgtk

(then enter your login password)
(if any error occurs with this step, reply back.

Google around on how to use synaptic and apt-get..... there'll be lot of help topics.....

Don't worry being a newbie, you ll get use to using ubuntu....
I was even sick of vista, so cheerup........


after installing ndisgtk(it automatically installs ndiswrapper... so don't worry)

goto the menu and try finding "windows wireless drivers" option somewhere...

use that to install 5416 atheros driver... after that try reporting back with screenshots on how it worked about..... I'll be happy to help you...

It'll add the driver and display a line below it whether the hardware is present or not...... If hardware is present, be happy and report back on how to use wifi........ or report back with your hardware configuration for me to help you.....
:):):):):):)

sorry for teh super long wait, i sorta gave up on it for a while. ndiswrapper works, but the driver wont do anything once i set it up. i have a broadcom 802.11g Network Adapter. i dont know if this helps at all, but i also am using an acer extensa 4620z. i got it last year a month before christmas. please help, nobody is responding to any of my threads. and because i have to reboot to get between linux and windows, and i can not use wired internet, i have no way to learn how t use synaptic and ap-get. thank you in advance

---

