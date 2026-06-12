---
title: "Can't connect to the internet"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by helliewm on 2007-02-02
I can't connect to the internet using wireless. My Network card is supported, Bigken from this forum sent me a compatible one, that isn't the problem. All its lights are on.

Connection properties applet says ath0 is idle. There is no green signal at the side of applet just a yellow/amber one,  I have configured it under System, Preferences, Networking.
 
Here are 2 screenshots from iwconfig and ifconfig that I have attached.

I have rebooted numerous times. Wireless Assistant is picking up my BT HomeHub-D130 signal.

Anyone any ideas?

Helen

---

### Post by encompass on 2007-02-02
Turn off your encription and don't hide the network... then go from there... your not associating... in other words it can't even see it yet.  Let alone have a digital conversation.

---

### Post by teaker1s on 2007-02-02
[COLOR="Red"]network-manager-gnome[/COLOR]

---

### Post by helliewm on 2007-02-02
How do I turn off the encryption? Its WEP. BT Home Hub comes with it?

Helen

---

### Post by helliewm on 2007-02-03
Eventually managed to turn off the encryption. 192.168.1.1 does not work with the BT Home Hub. To get into the modem/router configurations its [http://BtHomeHub.home](http://BtHomeHub.home) trust BT to be different!

Still could not connect to the internet so fed up with it  I am in process of reinstalling Ubuntu in the hope that that will sort itself out.

Helen

---

### Post by encompass on 2007-02-03
Did the device work before?
And yeah... each router is different.

---

### Post by helliewm on 2007-02-03
This is the first time I have tired to get Wireless working on my laptop. The BT Home Hub works fine with the wired connection to my desktop. A wired connection also works on the lap top. The BT Home Hub is BT's latest all singing and dancing modem/router.

Off to walk my dogs, have reinstalled ubuntu and shall give it another try and will report back.

Helen

---

### Post by bigken on 2007-02-03
Hi try this right click on you task bar and select add to panel the select 
network monitor doulble click it select configure from here you can add your 
essid and wep also make sure its enabled :)

---

### Post by bigken on 2007-02-03
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=24450&stc=1&d=1170505046[/IMG]


password is the wep key :)

---

### Post by helliewm on 2007-02-03
I am doing some serious swearing here. I still cannot connect using a Wireless connection. I reinstalled Ubuntu followed Ken's instructions, see screenshot.

I have also tried to set it up in System, Administration, Networking. I have tried to save the location as ath0 but as soon as close networking it seems to lose the ath0 location.

There are also screenshots of iwconfig and ifconfig.

What is the easiest way to set up wifi? Is it easier to this by the command line? If so, how do I set up wifi by the command line.

See screenshots.

Helen

---

### Post by bigken on 2007-02-03
you are connected look at the green power bar

---

### Post by bigken on 2007-02-03
also do have dhcp enabled in the router ?

---

### Post by helliewm on 2007-02-03
Solved::) :) :) :) 

Thank you so very much Ken for the Network Card  and phoning me this afternoon to talk me through this. I reset the modem and router again. I then went to my Desktop Computer and into System, Administration, Networking, Wired and DNS Servers.  Found the DNS then back to the laptop and into System, Network, Administration, Wireless, DNS. Went to add DNS Servers, added in the DNS that I had got from my Desktop. Restarted, just for good measure and I am connected 

Thank you for phoning without you talking me through the about:config and enabling IPv6 I still  would not have been connected. I would also never thought have it was a DNS problem.

My  12 year old greyhound Bamboo will be so pleased as I can now work downstairs. He cannot manage the steep second staircase to my room/ office! Barnaby the German Shepherd  could not care less he goes charging my cottage at top speed and up the second stair case! 

Thank you so much, speak to you soon. :) :) :) 

Helen

Ps For anyone following this thread I met Ken ( Bigken) through the forum and he literally lives down the road from me.

---

### Post by helliewm on 2007-02-05
A further update on this. I had re burn my Edgy disc as it was corrupt hence I had a corrupt install of Edgy on my laptop. So I reinstalled Edgy again and all the same problems occurred. I think one of neighbours has a BT Home Hub  their SSID is BT Home Hub, my SSID was BT Home Hub-D130. Hence it looks like I it was getting confused/conflicting with my neighbours SSID.

I am now using my Linksys Router/Modem and I am connected wirelessly and there is still a SSID/Channel called BT Home Hub according to KDE  Wireless Assistant. This why I think its a neighbours wirelessSSID/ channel. My BT Home Hub is in an box under the bed, so it can't it!

I did try changing my SSID on the BT Home Hub but that did not work. 

I did read somewhere if there is a conflict one can disable the channel or something like but can't remember where I read it. Does anyone have any ideas its just bugging me? 

For now I am happily connected using the Linksys Network Card BigKen sent me and my Linksys   modem/router.

Would just like to get to the bottom of this as its bugging me and I can't remember where I read about conflicting Wireless channels?

Helen

---

### Post by bigken on 2007-02-05
Hi Helen when you changed the ssid did you save it also the best channels to use are 3/7/11 

anyhow you are up and running now 


could never get that card to work in windows :lolflag:

---

### Post by helliewm on 2007-02-07
Your card is fine Ken, thanks so much:) Its the bloody router that is the problem. Everything works with my tempermental Linksysmodem/router ( it disconnects itself, did it with Windows too). Its the BT Home Hub that is the right pain. I done everything I can think of restored it to factory settings, changed the SSID etc etc.

Off to buy a Netagar Router at the weekend. Whats the best one to get? I am in loft and Belkin high speed modem/ router I had was useless it did not work downstairs; it died as one of the cats knocked a cup of tea in it!  I was thinking of a Netagar MIMIO M or N I think they are called, as there is 3 floors to the cottage? Looks like that would be about £100.

Thanks so much for the card, that is fine, its definitely not that:) 

Any ideas on the best modem/router to buy?

Helen

---

### Post by genbie on 2007-02-12
Hello Helen and Ken and any other BT subscribers out there!

If you don't mind me asking, how is your connection speed with BT? I have been with them for almost six years and now I am on the 8MB plan but I can just get an average of 3.5MB/sec, maybe because the modem they gave me was the USB Alcatel SpeedTouch one which is quite old and although it allegedly handles speeds of up to 8 MB/sec, I think the slow USB connection between it and my desktop is responsible for the slow speed. I do not live far from my exchange, I think 600 meters.  

How is the Home Hub's speed? I noticed it has v. 1.1 USB as opposed to v. 2.0, is this a problem? Does it have an extra free ethernet port? I am thinking of joining FON and I think an unused ethernet port is required. 

Appreciate your feedback a lot!

---

### Post by bigken on 2007-02-13
genbie you may be 600 metres as the crow files but as the wireing goes you could 10,000 metres personally I dont use bt as I have being with freeserve/wanadoo/orange from day one your lucky to have 3.5 I only get 1.1 and the girl next door only gets 512kb and she is with bt changing providers wont make your broadband faster you might change your modem 
for an all in one solution ie a netgear adsl modem wireless router :)

---

### Post by genbie on 2007-02-13
Thanks for the reply BigKen. BTW, when I say an average of 3.5 MB/sec, I mean the speed that I get when testing on the various broadband speed tests on the internet. During peak hours it gets to sub 3 MB/sec. I am NOT referring to the actual transfer rate of big files. For example with debian CD images [http://www.debian.org/CD/http-ftp](http://www.debian.org/CD/http-ftp), I tend to get around 380 Kbps only even though they are supposed to be very fast :mad: 
 
Is it the same with you?

---

### Post by helliewm on 2007-02-13
I think my BT is fine. I have always been with so historically get discounts on my second line. Hence staying with them works out cheaper for me.

The Home Hub is terrible I cannot get it work wirelessly at all. I think I am going to ring up BT for a replacemnt just so I have one that works.

The NetgeaR,  Modem Router I cannot get an internet light on it, Ken!?? When I am connecting it with wires to my Desktop. 

However I have used its power cable and now I connected Wirelessly with my old Linksys modem/router. Its was its power cable that was dodgy so Linksys works fine now.

Ken I bought of ebay the high speed Netgear Modem/Router all its lights are on apart from the internet LCD light. I am trying to connect with a wired connection to my Desktop before I start on the wireless side of things.

Do I need to set up PPOA as I have to do with Linksys, is that why the internet LCD is not coming on?   

I am not having much luck here!!!!!

Helen

Ps Someone was selling the Netgear Modem/router on ebay as they had just received a BT Home Hub!  I don't have any instructions with the Netgear Modem/Router as its second hand.
Brought that off ebay and saved money so I  treated myself to a lovely HP Phototsmart  Printer, Scanner and Photographer today. It works beautifully with Ubuntu, at least one thing has worked out OK!

---

### Post by bigken on 2007-02-13
yep just type 192.168.0.1 in the address bar then

admin

Password 

Just run the wizard :)

---

### Post by tyres on 2007-02-26
Hi,

Just for info (although probably not much consolation to Helen), i'm using a BTHomeHub wirelessly with no problems.
It's taken some work to get the BT 1055 USB adapter to work with Edgy, but I seem to have got it nailed down now. I'm using wireless on 2 desktop machines and a laptop, all connecting to the HomeHub. So it can be done!

Colin

---

