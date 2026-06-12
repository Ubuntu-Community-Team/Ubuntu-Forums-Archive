---
title: "Cricket Broadband (or other EVDO connection)"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by woktrr on 2008-09-24
Hello. I was wondering if anyone has successfully been able to setup a Cricket Wireless broadband usb modem on their Ubuntu machine & what the process may be. I’ve seen posts about installing other services’ EVDO modems like Verizon & Sprint, but I have this stupid Cricket service & can’t seem to get anything going. I know it’s a long shot, as very few have probably even heard of cricket, but any help would be appreciated.

---

### Post by Skylara on 2008-10-14
I would love to find out about this too.  I am going to be getting their broadband when it comes out in our area this month and don't want to switch my laptop from Vista to Ubuntu until I know it will work - since I work from my laptop.

Maybe I can poke around the WINE forums to see what I can find there, since it's a software issue and the software says it's only compatible with Windows and Mac.

Edit: I found a thread with a possible solution: [How to set up EVDO card or usb enable phone (CDMA)]("http://egypt.ubuntuforums.com/showthread.php?t=343989&page=26"). Part way down the page you'll find someone talking about getting their Cricket broadband to work... it continues on to page 27 until the problem seems resolved. It's a huge thread, but you might want to review it all for steps on how to do this specifically for Cricket and then maybe post it here in detail for other Cricket/Ubuntu users to use as a How-to, perhaps.

I would, but Cricket's broadband hasn't come out in our area yet, so I still have a month or so to wait.

---

### Post by maxovride on 2008-10-21
I got the utstarcom um100c usb modem from cricket wireless to work for me in ubuntu 8.10 (this is the new release that is coming out on oct. 30th)
  
it is actully very easy to do with 8.10. it is listed in the network manager icon where you connect to wireless connections. you do need to edit the setting for it (it is recognized as a "CDMA Connection" and you need to put in a username and password.  for this you use [email]yourphonenumber@mycricket.com[/email] (you can get you phone number either from the cricket store or in windows in the aplication for the cricket service) and the password is cricket.  make sure that the number section says #777. then just tell it to connect like you would to connect to a regular wireless connection.  

I am in the Salt Lake City area and im getting according to dslreports speed test between 350k-800k download (same as i get from windows)and about 120-150k upload (again same as windows).

i will try this with my other laptop that is running 8.04 and let you know how that works, but from what i understand its pretty easy to get to work there too.

---

### Post by RedneckNerd on 2008-10-30
I had just installed my very first linux Ubunto 8.04 and the only thing I need to work out was cricket broadband and wireless.  I downloaded 8.10 rc tried it from the disk, love it, now installing it.

---

### Post by frankhdz on 2008-11-02
Followed instructions to make my cricket USB modem to work on both 8.10 and 8.04 and neither works. How exactly did you accomplish this?

---

### Post by frankhdz on 2008-11-02
Ok I got the phone number the modem connects but the authentication fails any ideas?

---

### Post by frankhdz on 2008-11-02
this is what I get in the log:

--> PPP negotiation detected.
--> Starting pppd at Sun Nov  2 14:40:08 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8763
--> Using interface ppp0
--> Disconnecting at Sun Nov  2 14:40:11 2008
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

---

### Post by frankhdz on 2008-11-02
Ok I got it to work. for those who may experience the same problem I was having this is how I did it. If you don't already have it 

sudo apt-get install ppp wvdial

after install:

sudo wvdialconf /etc/wvdial.conf

the previous step detects your Cricket modem

then:

sudo gedit /etc/wvdial.conf

you will see the something like the following:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
Modem = /dev/ttyACMO
ISDN = 0
; Phone = #777
; Username = **********@mycricket.com
; Password = cricket

```

Uncomment the phone, username and password and enter you information the way you see mine. For user enter your phone number and add @mycricket.com

now you can use GNOME PPP and click setup autodetect your modem. select USB modem. now enter the same information to dial in and you should be good to go.

---

### Post by spydergt on 2008-12-07
i have a ppc 6800 and i just use the WMwifi router program by chainfire then connect to the shared evdo with a wifi card ,

but you see i have a cell phone that has wap , and i am behind the wap.mycricket.com proxy , 

what are you behind , i want to compare my settings vs yours to see if i can hack my phone somemore to gain the unrestrickted internet access that i hear the usb modem and pcmcia card modem have ,  

can you use bittorrent over it ?  are you behind a proxy ?  i get the same speeds with my setup but i want to unlokk it so i can use torrents , i cant currently redirect behind this proxy to gain that feature and am therefore limited to web pages and a few other things , but i can use it to say , packet manager and upgrade my buntu

---

### Post by gaintsura on 2008-12-08
> **frankhdz said:**
> Ok I got it to work. for those who may experience the same problem I was having this is how I did it. If you don't already have it 

sudo apt-get install ppp wvdial

after install:

sudo wvdialconf /etc/wvdial.conf

sudo gedit /etc/wvdial.conf

I should also point out that you have to run wvdial after all of this, and secondly. I should have checked here before I went on IRC. Fully functioning on the Cricket UM100c Broadband modem, speeds reporting at 600Kbps Up/100Kbps Down. 

One thing I noticed, this may just be my system... after plugging in the modem, nothing happpens, if you run wvdialconf you get an error saying the device is not ready or in use. I fixed this by performing:

```

lsusb;
sudo wvdialconf /etc/wvdial.conf;
sudo gedit /etc/wvdial.conf; (modify phone,user and password settings)
sudo chmod 660 /etc/ppp/*-secrets; (Make it so wvdialer can access the secret keys)
wvdial;

```

---

### Post by RedneckNerd on 2008-12-10
I just had to plug mine in and it did the rest.

I did have it activated under xp though.  When I had to get my cricket reactivated I had to activate it under xp again.

---

### Post by longuriel on 2009-04-15
Two things I can add to this topic being I am a cricket customer service and sales rep who is moderatly computer savvy (not much on Lenux yet, that will change this weekend when I start learning MythUbuntu)

1)You probable have to activate your broadband card first, if you do not have a XP machine you can/want to install it on to activate it, you can take it into a cricket store and there staff there should allow you to hook it up to there laptop display which you can then go into the Cricket mobile Gui, Choose ->Tools->activation

2)You do not want to torrent on Cricket broadband or download large patches/updates for things such as wow, Xp, exc Due to there is a 5gb monthly cap that if you exceed your Speed will be slowed down below Dial up effectivly halting you from using more bandwidth than they have allocated. (currently broadband is growing faster than we can meet demand, although we are being pushed to sell even more than what we are already selling... tell me that makes sense?)

I should mention only cricket Corporate stores will have this display and be able to provide this service. To find out where a local Corporate store is, check [www.mycricket.com](www.mycricket.com) and click on the store locater. If you have any problems with the store staff, email me at the listed email below, with the store location you are having problems with, your name and number, and I will see if I can mediate.

Also Side note:This activation is only known to work for the PCIM card and Cricket UM100c modem, we currently have a new one with a built in Micro SD slot and a swivel mount that is the a100. That device has built in softwear that conflicts with our Cricket Store displays (and newer stores such as Chicago and Philly may be running these newer USB modems and so might not be able to activate in store)
If anyone has any other questions, I would be happy to field whatever questions I can at angel14@.com

---

### Post by clownsas on 2009-04-17
> **woktrr said:**
> Hello. I was wondering if anyone has successfully been able to setup a Cricket Wireless broadband usb modem on their Ubuntu machine & what the process may be. I’ve seen posts about installing other services’ EVDO modems like Verizon & Sprint, but I have this stupid Cricket service & can’t seem to get anything going. I know it’s a long shot, as very few have probably even heard of cricket, but any help would be appreciated.
Hello install ubuntu then plug in your cricket modem look at the top right hand corner of the screen there will be a small monitor left click on it go down to auto broadband left click on it then you will be connected then click on firefox web browser

---

### Post by Huntly on 2009-04-21
Switched to Ubuntu 8.10 a few weeks ago, after setting up the Cricket on an XP machine.  Modem worked fine for a while.  I set up a new machine with 8.10 again and now my signal keeps stopping after a few minutes; comp also freezes up if I try to reconnect.  Called Cricket and was told to re-activate the modem, obviously can't do this on linux.  Anyone been able to get WINE to run the setup wizard for the modem?  I can get to the point where it tries to find the modem but can't get past that.  Also, even when it was running fine I could rarely get over 100k down.

---

### Post by miklo1337 on 2009-05-22
This is what Cricket Broadband has to say about the issue. I found it kinda funny.
 
**Cricket Broadband**

**Cricket Broadband Compatibility**

** Is Cricket Broadband compatible with Linux?**

No. Linux is not supported at this time.
 
However, you can go to the network connection and edit it and it will connect to the internet. Add USA then add Cricket Broadband it's listed and I checked off any  user and connect automatically and it works, but I also noticed that it stops working after a while and you have to boot back into windows and start it up again. Then boot back into linux and repeat. I think it's that Cricket's Servers are rejecting the connection after a while of running linux. IONO hope this helps.

---

### Post by Cerin on 2009-07-02
> **miklo1337 said:**
> This is what Cricket Broadband has to say about the issue. I found it kinda funny.
 
**Cricket Broadband**

**Cricket Broadband Compatibility**

** Is Cricket Broadband compatible with Linux?**

No. Linux is not supported at this time.


Yeah, that's the first thing I saw when I started researching their service.

As a result, their service isn't supported by my wallet at this time. I wish these Corporations would get a clue.

---

### Post by Krepta3000 on 2009-07-07
> **frankhdz said:**
> Ok I got it to work. for those who may experience the same problem I was having this is how I did it. If you don't already have it 

sudo apt-get install ppp wvdial

after install:

sudo wvdialconf /etc/wvdial.conf

the previous step detects your Cricket modem

then:

sudo gedit /etc/wvdial.conf

you will see the something like the following:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
Modem = /dev/ttyACMO
ISDN = 0
; Phone = #777
; Username = **********@mycricket.com
; Password = cricket

```

Uncomment the phone, username and password and enter you information the way you see mine. For user enter your phone number and add @mycricket.com

now you can use GNOME PPP and click setup autodetect your modem. select USB modem. now enter the same information to dial in and you should be good to go.

Wow, thanks to this message I was finally able to get my ubuntu laptop to use my LG VX8360 cell phone from Verizon as a dialup modem to connect to my dad's Juno internet account.  [snip] Never mind all that stuff I said before, whatever was wrong has disappeared and all I have to do now is run Gnome PPP.  Forget about all that wvdial stuff, just tell Gnome PPP to auto detect the phone.  Also I told it the phone is a USB modem rather than an analog modem, but I don't know if that makes a difference.  Awesome!  I love Ubuntu!

---

### Post by perezomail on 2009-09-25
> **woktrr said:**
> Hello. I was wondering if anyone has successfully been able to setup a Cricket Wireless broadband usb modem on their Ubuntu machine & what the process may be. I’ve seen posts about installing other services’ EVDO modems like Verizon & Sprint, but I have this stupid Cricket service & can’t seem to get anything going. I know it’s a long shot, as very few have probably even heard of cricket, but any help would be appreciated.

i just solved this problem on fedora 10 

the first you need to make sure it is checked on your start up files
the second will make sure the third works note there is a set of files on the third which
is the syntax needed..........check your repositories for the first two
**********im on fedora 10......after i did all of this i shut the computer down and started it up
the modem seems to only pick up from off to on not already on
1) [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) 
 
2) [http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/) 
 
3) [http://www.tummy.com/journals/entries/jafo_20090829_150952](http://www.tummy.com/journals/entries/jafo_20090829_150952)

i did not need to put in phone info or anything however the modem must first be activated account wise on xp or mac before working on linux.......goodluck--------pass it on

---

### Post by doctorronnie on 2009-10-13
Just wanted to share that I got quite a laugh out of that. I called Cricket and the people I talked to didn't even know what Linux was.

---

### Post by kencorbin on 2009-11-13
After lots of reasearch and following up on dead end leads, the process of getting a Cricket modem working turned out to be almost trivial.  Just install the usb_modeswitch package available in the Ubuntu repositories.   It isn't quite perfect.  It didn't take effect until I rebooted my machine.  And still won't recognize the modem if it is installed when you boot up.  But you just unplug the modem and plug it back in and it installs the Cricket broadband network which you can activeate normally.

---

### Post by thedandalion on 2010-03-30
Ok ... 
 
I have 9.10 and I can connect and it will freeze up on me under less than a minute.  I have followed some suggestions in another thread and have tried this one but it doesnt help.  Can anyone help me?
 
I have the starcom185 stick and it works wonderfully on my laptop.  I put in the info and never had an issue.  Now on my desk top it will connect then freeze under a minute.  I am at a loss at what to do next.

---

### Post by CaptBry on 2010-04-15
Cricket UM185C USB in Ubuntu Linux

I was using a Verizon USB modem under Gppp and vfdial.conf as mentioned in the above posts. (I followed the Verizon install guides Search-able in this forum)

When I got my Cricket UM185C, I activated it in WinXP under the Cricket software supplied.

Then I (dual) booted to Ubuntu 9.10 and Gppp found the modem no prob and USED THE VERIZON NAME AND PASSWORD TO RUN THE UM185C THROUGH CRICKET'S ISP!!

This surprised me and I'm sure a more savvy Linux/Broadband Tech will have an idea WHY this worked so easily.

Moral of the story is, If you want Cricket, Ubuntu (probably any Linux) will work.

DO NOTE; Cricket [COLOR="Red"]***"Unlimited" Plan is NOT unlimited***[/COLOR]. They sell it that way but after just 5GB your "service" gets decimated to about 15Kb/second ;useless for anything above email usage!!!
And I joined Cricket because I was tired of Verizon's Byte-Counting games..... Geeezzzz:lolflag:

---

### Post by BKaren on 2010-04-17
> **Cerin said:**
> 
As a result, their service isn't supported by my wallet at this time. 
 
LOL, nor is in supported by mine any more.    The service was so poor and spotty we dumped it after fighting with it for 6 weeks!  
 
We were using a router and the speeds with just a single computer were abismal, connecting two was a joke.   
 
The price seemed too good to be true, as the old saying goes . . . . . .  . . . . . . .

---

### Post by BKaren on 2010-04-17
> **CaptBry said:**
> 
 
DO NOTE; Cricket [COLOR=red]***"Unlimited" Plan is NOT unlimited***[/COLOR]. They sell it that way but after just 5GB your "service" gets decimated to about 15Kb/second ;useless for anything above email usage!!!
And I joined Cricket because I was tired of Verizon's Byte-Counting games..... Geeezzzz:lolflag:
We tried Cricket and the 5GB cap was NEVER a problem. As slow and unreliable as the service was, we could not have reached 5GB if we had taken shifts and stayed online 24/7! On it's best day, our service was decimated from the start, once in awhile attaining 100K, but rarely. 
 
Like you we left Verizon because of their 5GB cap, and had high hopes for the Cricket unlimited. We are now using a truly unlimited plan, not $40 mind you, but it works 20 times faster and in a whole lot more areas than the Cricket ever did! Just Google No Limit 3G. We have a router and can connect 4-6 computers plus iTouch's, game consoles etc. 
 
The router eliminates a lot of headaches, we have a mix of Linux, Mac, and PC boxes, and the router does not discriminate and allows them all to coexist and share the USB modem. 
 
Incidentally we tried the T-Mobile product along the way, and it was equally lousy. 
 
HTH

---

### Post by silvergriffin on 2010-08-26
Hi I'm kinda new to linux and have 10.04 Lucid lynx thing is I can't get my Cricket internet to work in 10.04 and Cricket is the only internet I can afford any advice ideas on how to set it up?

---

### Post by desnaike on 2010-08-28
I've been using cricket a600 modem since May 2010 this is how.
[http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html)

---

