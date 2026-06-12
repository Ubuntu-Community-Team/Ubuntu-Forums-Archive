---
title: "belkin &quot;my essential&quot; usb wireless adapter issue"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by mobilebuddha on 2007-03-29
Hello there,

Just installed ubuntu 6.10 on my old dell inspiron 7500 with a belkin "my essential" wireless usb adapter. the model # is ME1001-USB.

I can't seem to find any documentations anywhere regarding this specific model (the usb wireless adapter).

when i open up network settings dialog box, under connections tab, i'm only seeing a "Modem connection".

unlike windows, if i plug in the wireless adapter, ubuntu doesn't do anything. (since i don't know much, if anything about ubuntu, i'm not even sure if it's supposed to do something).

so i guess my questions are the following:
1) is this device supported in ubuntu?
2) where do i start to get this thing configured so i can access the network?

---

### Post by mobilebuddha on 2007-03-29
bump.. anyone?

---

### Post by alicemoon on 2007-03-29
I have just started looking at ubuntu and know very little however wireless was very tricky to get going with a belkin pcmcia wirelss card on my sony vaio under 6.10 - I had to get someone to help me set it up and it took him over an hour! and he knew what he was doing? However  I have just installed feisty fawn beta on a pc and it has much better support for those of us who don't know how to use the command lines. I have still failed to get wireless working with my belkin usb wireless adapter under feisty - it recognises it but when I put in my security code it does not connect (I know it is not a problem with the adapter or security code as I can reconnect it to my windows pc with success.

I would suggest uprating to feisty - hopefuly you will have better luck than me

---

### Post by mobilebuddha on 2007-03-29
alicemoon,

i'm making progress. after doing a lsusb on my system, i see this line in the result:

Bus 001 Device 005: ID 050d:705c Belkin Components

since i had looked at quite a few of the sites/pages that talked about Belkin usb adapters, that ID looked somewhat familiar. so I googled it (google 050d:705c)

turns out, on the 2nd page of google results, is the page that got me to where i am right now - i'm able to see wireless connection under Administration->Networking, but I am still not able to get it to connect to my router.

here's the URL to the site that helped me install what I needed and make the wireless connection show up in the Networking dialog box:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))

I followed it step by step. 

Here's my problem now:

if I do a lsmod, i'm able to see the zd1211 and zd1211b modules, i'm also able to see the wireless connection in the network dialog box. but when I try to connect to a router, it doesn't seem like it's working. This is the output that I'm seeing from running iwconfig wlan0

wlan0     802.11b/g NIC  ESSID:"home1248"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=35/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4511
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and now I'm out of ideas.. not sure why it's not "associating" itself with the access point.. can anyone share some insight here?

Edit: if i do a iwlist wlan0 scanning, it shows me a list of the current available access points in range correctly. the one that i'm connecting to is also in that list. but i just can't seem to connect to it. 

if anyone has any ideas/thoughts on how to resolve this.. i'd be grateful. thanks!!

---

### Post by mobilebuddha on 2007-03-29
so has anyone gotten their Belkin wireless card ( chipset is 050d:705c ) to work with 6.10?

---

### Post by alicemoon on 2007-03-30
well you've got a replication of my problem on feisty - I can see my wireless network - the dongle searches (and I have been trying to connect with an edimax dongle as well - same thing) but cannot associate - I think it may be a driver problem - I have resorted to getting expert help but may not hear from him till monday, will let you know if I solve the problem - good luck

---

### Post by mobilebuddha on 2007-03-30
i have to vent. been searching through various forums/sites for the last day or so with no results, i'm putting this computer together for a family member hoping that she can start using linux.. i ALWAYS hear people who love linux preach about how easy it is to use the system nowdays, if this is the definition of "easy", i don't really think I want to know what they think as a "hard" problem..

anyways, if your help figure it out, please keep me posted! thanks!!

---

### Post by thetruth on 2007-03-30
I have the same problem as above. tried everything  i came across but no luck. damn it it is so annoying cos I need it to work for my Main PC  having extra wire running  in the house is not pretty and i hate using Windows funny enough with  My laptop Sony Vaio i did nothing extra everything worked out the box

---

### Post by alicemoon on 2007-03-30
it is annoying and I am keen to use linux - I already use alot of opensource programs on windows and certainly support the linux/ubuntu ethos but I am having problems convincing my partner switching is sensible as we have really struggled with wireless internet connections. We are often away from our home base so do not have a wired option so this is a real stumbling block for me as I need access for my work. 
I suspect it is a driver conflict which is what it was with the belkin card in the vaio - I will keep you posted if I make any progress.

---

### Post by mobilebuddha on 2007-03-30
are there ANYONE out there that has gotten this 050d:705c chipset wireless cards to work with Edgy (6.10) ?

I cannot believe it's this difficult. And they say linux is ready for desktop, or prime time.. How is it that I can put in a CD and get the adapter to work in Windows 2000? Yes.. Windows 2000, the OS that came out in 1999/2000!

-_-

---

### Post by mobilebuddha on 2007-03-31
i'm keeping this bumped.

---

### Post by mobilebuddha on 2007-04-01
bump! someone? anyone? am i just screwed?

is ubuntu wireless networking really THIS crappy?

---

### Post by thetruth on 2007-04-01
Wow

I restarted my PC over and over after going really slow. and Guess what? I got my PCi Am772 working and working fine under Wpa encryption .. I can't believe my luck. This was a dead PCI and now it has been revived .
Well done Feisty Fawn beta I love you

---

### Post by mobilebuddha on 2007-04-01
ugh..

thanks for the "totally unrelated to the original post" bump.. i guess.. :confused: 

so where are the folks that bitch about windows and preach about linux's power, stability, and how easy it is to use the OS, i can't really use it if i can't get on the network.. right? so where are you people?

> **thetruth said:**
> Wow

I restarted my PC over and over after going really slow. and Guess what? I got my PCi Am772 working and working fine under Wpa encryption .. I can't believe my luck. This was a dead PCI and now it has been revived .
Well done Feisty Fawn beta I love you

---

### Post by Chrisj303 on 2007-04-02
Why don't you check out the supported hardware page, which is part of ubuntu's site. It lists all USB wireless adapters known to be working/non-working.
Also the ME1001 - only seems to be refering to the adapter when it has been sold as part of a package. I'd put money on it that it is in fact a 'Wireless-g FD7050' or very similiar.

---

### Post by mobilebuddha on 2007-04-02
Chrisj303:

I'm not sure if you read the -whole- thread. But just in case you haven't..

I've determined the usb id of the device to be 050d:705c

whether it's Wireless-g FD7050, or some other model #, it doesn't matter. I believe that's the chipset which drives the adapter. (right?)

if so, whatever drivers that support 050d:705c, should work.. or so one would assume.

the problem that i have is.. it IS working, sort of. I am able to do scans of the available networks, so it seems that at least it's able to access the adapter, do some of the functionalities that the usb adapter is supposed to be able to do, but it's not able to connect to my router.

do you see my problem now? it's not that ubuntu isn't recognizing the adapter at all, it's the fact that it is half working. i've tried -all- of the troubleshooting steps that i could find on wifidocs, ubuntuforums and other sites that i've been able to find but NONE is helpful with my particular problem.

my PRIMARY beef with this is that, people have been preaching ubuntu to be the ultimate easy to use linux distro. and it's been what, 3-4 days later, i still do not have a working wireless network connection!

as sad as it sounds, I had windows 2000 on the laptop before i wiped it to install ubuntu, the driver installation took a total of 5 minutes. i really want to believe that linux is better, but how can it when i have so much trouble? 

on a side note, as a test, i put the edgy 6.10 desktop cd into my new laptop, a dell e1405 that i bought about 2 months ago. guess what happens? it can't start x server. as a result, it won't start the installation procedure at all. 

i have 2 laptops: i can't get wireless to work on my old one, and the new one won't even install. i am SURE if i looked around enough, there will be some sort of switch, or config thing that i can put into the cmd line somewhere to make the install work on the new laptop. but guess what.. end users should NOT have to do this. 

this is why ubuntu is NO WHERE close to be ready for anyone who isn't a complete total nerd. I am sorry for bashing ubuntu on this, but this has been extremely frustrating to me.

PS. I looked at the ubuntu site a while ago, cards/adapters with 050d:705c has been said to be supported w/o much trouble. yeah.. right. -_-

> **Chrisj303 said:**
> Why don't you check out the supported hardware page, which is part of ubuntu's site. It lists all USB wireless adapters known to be working/non-working.
Also the ME1001 - only seems to be refering to the adapter when it has been sold as part of a package. I'd put money on it that it is in fact a 'Wireless-g FD7050' or very similiar.

---

### Post by alicemoon on 2007-04-02
mobile bhudda,
my 'expert' says feisty has network problems so I have returned to edgy - I know for me it is a driver problem and I know I can solve it if I can update the kernel 'whatever that means! - but to update I need to connect to the internet which |I can't do as my lan connection is broken. So the worksround is to remove the hard disc and put it in my work computer where the lan works!! and update from there then change the driver. If I connect I'll let you know
However - if this helps via another thread it was suggested I try the following which worked for someone who had a similar problem to us he said

"open terminal and

sudo iwconfig

This will tell you the name of your card in Ubuntu. (It will ask for your password before executing the command) Mine is rausb0, but that's weird. Yours might be wlan0. Note that sudo lets you run the command as root (think Administrator in WinXP).

Then type

sudo dhclient the-name-of-your-card

In my case, the command is:

sudo dhclient rausb0

Note that Ubuntu calls my card rausb0 (it's a wusb54g Linksys) but it might be something else in yours, like:

sudo dhclient wlan0

In any case, it will take a few seconds for the command to complete. Once it does, try running Firefox and navigating to any web page. If it works, you're golden...though you will probably have to enter the command each and every time you boot up. "

it may not work for you but worth a try - I have decided Ubuntu is not ready for my work computers - I shall stick with XP for work but keep running edgy on my personal laptop the one I'm writing on and keep learning. Ubuntu is not easy if you have limited knowledge but it's heading in the right direction.

---

### Post by Chrisj303 on 2007-04-03
read this: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

And please stop moaning like a little school girl regarding ubuntu. Do you think you could have switched to vista without any problems?

If you can't get it to work, read that link and just buy one that does - there only like £15-20!!!

Chipset and usbid are 2 different things.

---

### Post by mobilebuddha on 2007-04-03
Chris,

point #1: ya know, funny you asked that. I just installed vista ultimate on the DELL e1405 without any problems. this is the laptop that ubuntu refused to even start the X server to install programs.

so.. yeah, i switched to vista w/o any problems on that laptop, where ubuntu had a LOT of problems!

point #2: i'm quoting from the page that YOU gave out:

"lspci -v | less

Then, scroll to find your wireless device and note down its details. For USB devices, type lsusb instead. "

you see where it says, "for USB devices, type lsusb instead"?

and you know what sort of output lsusb gives? here's an example:

Bus 001 Device 003: ID 050d:705c Belkin Components 
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  

i hope now you see why the usbid is so critical to me, because w/o the usbid, there's not really another way for me to uniquely identify the particular hardware.

and you are right, the page that you gave me  makes no mention of that particular usbid, but it does have a loooong list of belkin devices that it says is supported. except i have no way of identifying whether the usb adapter that i have is one of them or not.. which makes it difficult for me to tell. in fact, how do i know that my next adapter is going to be supported? i don't, unless i can see the exact usbid that it uses.

my conclusion here is unfortunately going to upset you a bit: ubuntu is not ready for prime time, at least not for me. i've played with linux on and off since slackware 3.3, i love linux and the stability that it brings, just hate the nightmare that comes w/ the installation/configuration of all of the peripherals that i need to do.

before i end my post, i'll write about something else, hopefully you can read this w/o any prejudice and give it some serious thought:

most people do not like to tinker with their computers. if you do, you are in the extreme minority. most of the normal people like their computers to work when they need to work and disappear into the background while they are using the computer.

imagine if the car that you drive needs CONSTANT maintenance, or the fact that when you buy a new car, you need to spend a month or 2 configuring/installing various things just so you can drive it around - and sometimes after a month or 2, you realize that it's not gonna work unless you buy additional hardware. wouldn't you agree that this would be a pain in the butt, even if you got the car for free? i would.. my time is better spent doing something else.

i guess what i'm saying is that when computers (and the OS on top of the hardware) start to fade into the background like our highways, we'll know then that the OS has truly made a significant advancement.

I think linux is half-way there, the stability of the OS is phenomenal, but the amount of work that goes into setting one up is also phenomenal. in contrast, during my windows vista install of my new laptop, i remember having to click about 3 times and type in the computer host name and my user name/password. that was it. the rest of the time it churned happily in the background while i was typing frenzily into this laptop trying to figure out how to connect the usb adapter onto my router. what a difference, eh?

I will try out ubuntu 7.x once it's out of beta, i hope my experience is better next time.

cheers!
> **Chrisj303 said:**
> read this: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

And please stop moaning like a little school girl regarding ubuntu. Do you think you could have switched to vista without any problems?

If you can't get it to work, read that link and just buy one that does - there only like £15-20!!!

Chipset and usbid are 2 different things.

---

### Post by Chrisj303 on 2007-04-03
I never said ubuntu is for everybody - i KNOW it is most certainly not. I enjoy using computers and don't mind playing around with them.

If you don't like playing with computers and don't want to use windows get a mac.

Please don't take your frustrations regarding ubuntu out on me - i had nothing to do with your desicion to switch and your resulting frustations.

I don't care if (in your view) ubuntu is not ready for prime time - i enjoy it, thats all! I'm not a fanboy who gets upset at other peoples choice of operating systems. 

I run a triple boot Macbook - OSX/UBUNTU/XP - so belive me, i've has my fair share of problems! 

It seems a bit drastic to throw the towel in because you can't get your wireless to work. Personally, i'd just get a new USB adapter for a few quid rather than use windows as a primary OS.That was why i linked you to that page - find one that you now will work. And your going to have more luck searching for help if you know the chipset, rather than just the usbid. different companies often use identical chipsets as each other - thats why it is common to use one companies driver with another companies hardware.


chrisj303

---

### Post by alicemoon on 2007-04-03
mobile bhudda
- I have wireless!! I fixed the lan that was broken by replacing hardware with a network card that luckily proved to be plug and play then I updated everything - then reinstalled the recommended driver for my dongle - then restarted everything - then connected via admin - networking.  Nothing worked till I wrote in my essid and it all sprang into life.

---

### Post by Ripfox on 2007-09-22
I just plugged this into my desktop running Feisty and it worked out of the box. Maybe it was an Edgy issue?

---

### Post by blackaardvark on 2007-09-25
okay, i have a F5D7050 but my lsusb gives me a slightly diffferent usb id.

Bus 005 Device 007: ID 050d:705a Belkin Components 

Am I using the wrong driver or something?

---

