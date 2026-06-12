---
title: "WUSB54G v4"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by justin1278 on 2007-10-18
Hello,

Just tried installing Gutsy on my desktop, didn't go over too well as my wireless adapter doesn't work.

I have a Linksys WUSB54G v4 USB adapter, and when I connect to my network (sometimes it will let me connect sometimes it won't) I don't get internet access. And with the location of the desktop, wireless is its only access :(

Any ideas on how to fix this, any help is greatly appreciated :)

---

### Post by rustybronco on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=580241](http://ubuntuforums.org/showthread.php?t=580241)
that adaptor worked in fiesty I will have to try it on a live cd and see if it works.

---

### Post by rustybronco on 2007-10-18
didn't work with gutsy in roaming mode or manual config.
try ndiswrapper and let me know.

***edit*** strange changed it to manual config tried it and it was a no go, went back to roaming mode and i could see my network at 87% but could not connect.
rebooting as we type.
it can see the router and the mac address of it, it's at -31dbm down but it just won't associate with the network (yes the mac address is in the router for the wusb54g) i'll look again tommorow and see what I can find out if there is time.

---

### Post by justin1278 on 2007-10-18
How am I supposed to get Ndiswrapper on a PC that has no internet connection?

---

### Post by spezticle on 2007-10-18
> **rustybronco said:**
> didn't work with gutsy in roaming mode or manual config.
try ndiswrapper and let me know.

i'm having trouble with this same device... no IP gets assigned. i'm a bit new to linux but not computers thouogh... so whats this ndiswrapper? Or well... do you have any idea why it doesn't want to assign an IP?

---

### Post by justin1278 on 2007-10-18
> **spezticle said:**
> i'm having trouble with this same device... no IP gets assigned. i'm a bit new to linux but not computers thouogh... so whats this ndiswrapper? Or well... do you have any idea why it doesn't want to assign an IP?

Ndiswrapper is a linux program which will allow your wireless device to operate using Windows drivers.

---

### Post by justin1278 on 2007-10-18
Ok just re-install Ubuntu 7.10 on the PC, will install Ndiswrapper from the install CD and see how it works.

---

### Post by rustybronco on 2007-10-18
> **justin1278 said:**
> Ok just re-install Ubuntu 7.10 on the PC, will install Ndiswrapper from the install CD and see how it works. 
plus you will need the .inf driver for the wusb54g v4 from the linksys cd. still let me find out what I can.
I have seen a lot of the posts on this piece of junk (my opinion). and I would like to try to help.

---

### Post by justin1278 on 2007-10-18
Ok ndiswrapper-common is installed, now what do I do? I can get the drivers of the CD, that isn't a problem, just don't know what to do because I do not have experience with Ndiswrapper.

*EDIT*
Ok I have the rt2500usb.inf file from the CD now.

---

### Post by spezticle on 2007-10-18
> **justin1278 said:**
> Ndiswrapper is a linux program which will allow your wireless device to operate using Windows drivers.

alright, well i'm not having a driver issue. just connectivity. it's reporting that my signal strength is 0%
There is another wireless network in range that is not my own, and encrypted, and it seems to want to connect to that one if i try, but i don't know the key for the WEP so of course i can't try it out.

So back to original thought.... why might it report a signal at 0% ? i shouldn't have to set something up with the router, DHCP should just take care of it.... think i'm going to go out to the garage and get my 60 feet of cat5 and ditch this lame *** wireless ****. so unreliable and such a pain haha

---

### Post by justin1278 on 2007-10-18
> **spezticle said:**
> alright, well i'm not having a driver issue. just connectivity. it's reporting that my signal strength is 0%
There is another wireless network in range that is not my own, and encrypted, and it seems to want to connect to that one if i try, but i don't know the key for the WEP so of course i can't try it out.

So back to original thought.... why might it report a signal at 0% ? i shouldn't have to set something up with the router, DHCP should just take care of it.... think i'm going to go out to the garage and get my 60 feet of cat5 and ditch this lame *** wireless ****. so unreliable and such a pain haha

I was having an issue similar to this earlier today, sometimes it would connect, sometimes it would not, and when it did my connection was at 0%. So I think your issues could be the drivers just like mine. 

If you need the rt2500usb.inf file I have it and can give it to you so you can try ndiswrapper, although the Cat5 idea sounds easier lol

---

### Post by spezticle on 2007-10-18
> **justin1278 said:**
> I was having an issue similar to this earlier today, sometimes it would connect, sometimes it would not, and when it did my connection was at 0%. So I think your issues could be the drivers just like mine. 

If you need the rt2500usb.inf file I have it and can give it to you so you can try ndiswrapper, although the Cat5 idea sounds easier lol

i have the driver file... but thanks for the offer :) yeah, i can't ever get it to connect to mine. it just stops trying and says no network connection after a bit. and always reports signals at 0% i'll try some driver stuff but i dont' feel like screwing with it that much

 i never really did like wireless at all. cat5 is so much faster. well, not that i'll ever really be able to transfer at 1000 mps lol

---

### Post by justin1278 on 2007-10-18
> **spezticle said:**
> i have the driver file... but thanks for the offer :) yeah, i can't ever get it to connect to mine. it just stops trying and says no network connection after a bit. and always reports signals at 0% i'll try some driver stuff but i dont' feel like screwing with it that much

 i never really did like wireless at all. cat5 is so much faster. well, not that i'll ever really be able to transfer at 1000 mps lol

imo, wireless isn't worth all the hassle, although when it is setup it is nice to have, but then when a new OS comes out it is more trouble... 

I don't have the Cat5 option so you're lucky lol

---

### Post by rustybronco on 2007-10-19
ok a couple of posts.

[http://ubuntuforums.org/showthread.php?t=478558&highlight=wusb54g+v4](http://ubuntuforums.org/showthread.php?t=478558&highlight=wusb54g+v4)
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

but I would try the ndiswrapper approach first. I will try it on my laptop and let you know.

---

### Post by justin1278 on 2007-10-19
I have installed the Ndiswrapper drivers, still not working :(

I will check those links.

Thanks for your help so far, I appreciate it :)

*Edit*

Just tried Ndiswrapper method listed in one of the links, still no go... I will wait and see if you can do Ndiswrapper on your notebook before I try anything else.

---

### Post by delmore on 2007-10-19
ive tried just about every solution I could find here since Gutsy Tribe 5 to get my WUSB54G to work and still have not gotten anywhere

someone please squash this!;) the WUSB54G has worked out of the box since Edgy--I wonder what happened?

the worst part is, ive been using windows since the gutsy beta, after running Ubuntu full time since Dapper (tho im not a 'power user' per se, i hardly ever use the terminal and only then based on explicit instructions from the web)

i noticed that in Edgy and Feisty the interface? was 'rausb1' and now it is 'wlan0'

I'm not sure if that has anything to do with the problem, but it makes me hate 'wlan0'

---

### Post by wieman01 on 2007-10-19
Got to work my WUSB54G V4 using this approach:

[http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419")

Post over there if you need support.

---

### Post by delmore on 2007-10-19
yous is the first solution i tried. i've tried it a zillion different ways splicing it with other similar guides etc etc... have you actually tried this in gutsy with a WUSB54G v4? it doesnt seem anyone else has confirmed this method as working, minus anyone who got it to work and didnt post about it

---

### Post by wieman01 on 2007-10-19
> **delmore said:**
> yous is the first solution i tried. i've tried it a zillion different ways splicing it with other similar guides etc etc... have you actually tried this in gutsy with a WUSB54G v4? it doesnt seem anyone else has confirmed this method as working, minus anyone who got it to work and didnt post about it
Mmm... odd. Only the poll seems to suggest that it has worked for somebody. In fact I have tried that myself and it does work in Gutsy, no doubt. What sort of issues did you have?

---

### Post by New Penguin on 2007-10-19
I've been tearing my hair out about this issue all morning having upgraded from Feisty where it previously worked. However I can confirm that if you follow the method outlined by wieman01 then it definitely does work (I'm writing this now from Firefox in Gutsy). Hope it works for the rest of you too!

Edit: Tried it later on and it now no longer works *sigh*

---

### Post by rustybronco on 2007-10-19
I don't doubt it will work fine, but I want to know why ralink doesn't play nice with network manager (it bugs me to no end) 
wieman01 do you know why?

---

### Post by wieman01 on 2007-10-19
> **rustybronco said:**
> I don't doubt it will work fine, but I want to know why ralink doesn't play nice with network manager (it bugs me to no end) 
wieman01 do you know why?
Yes, you can read this thread... short discussion on the topic:

[http://ubuntuforums.org/showthread.php?t=560229&highlight=ralink+drivers+work&page=2]("http://ubuntuforums.org/showthread.php?t=560229&highlight=ralink+drivers+work&page=2")

---

### Post by justin1278 on 2007-10-19
Ah maybe the issues I was having last night was after I installed the drivers I was trying to connect through the network manager.

With the drivers installed, how do I go through on connecting to the wireless network?

---

### Post by wieman01 on 2007-10-19
> **justin1278 said:**
> Ah maybe the issues I was having last night was after I installed the drivers I was trying to connect through the network manager.

With the drivers installed, how do I go through on connecting to the wireless network?
Network Manager or WICD that is.

---

### Post by justin1278 on 2007-10-19
Ok I will try again later, I am currently going to try Suse 10.3 after that, I will re-install Ubuntu 7.10 and try that....

Can you give me some instructions please? I am still new to linux and I really appreciate your help.

---

### Post by wieman01 on 2007-10-19
> **justin1278 said:**
> Ok I will try again later, I am currently going to try Suse 10.3 after that, I will re-install Ubuntu 7.10 and try that....

Can you give me some instructions please? I am still new to linux and I really appreciate your help.
You can follow the tutorial in my signature... if you run into problem, just post there and I will try to help. :-)

---

### Post by justin1278 on 2007-10-19
> **wieman01 said:**
> You can follow the tutorial in my signature... if you run into problem, just post there and I will try to help. :-)

Ah ok thank you!!!! :KS

---

### Post by Kizlum on 2007-10-19
Does it work now or you just have the .inf file?
For the Ndiswrapper configuration, look [there]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28ndiswrapper%29") from the 6th step. It's for a Linksys WUSB11v4 802.11b USB Wireless Adapter, but I think you can adapt this.

EDIT:
Sorry : I haven't ,seen the other posts. :(

---

### Post by delmore on 2007-10-19
Wieman, here's the problem I have

after I install the driver with ndiswrapper and blacklist it, wlan0 stops showing up under iwlist

i only see lo and eth

also, shouldn't you run 'ndiswrapper -m' after installing the driver rather than before?

is this because im installing the rt2500usb driver with ndiswrapper and then blacklisting the rt2500usb driver?

on a clean install, if I go to "connection properties" for the wlan0 device, it tells me im using the rt2500usb driver, so im supposed to blacklist that so it doesnt use the broken driver eh? but then shoot myself in the foot cause the ndiswrapper driver is also called rt2500usb?

i read on some forgotten website that the WUSB54G uses the rt2570 driver? anyone know about that?

---

### Post by justin1278 on 2007-10-19
Ok guys, still nothing is working, I'm about ready to give up on this :(

I appreciate the help and time you have put in to help me with this issue, but hopefully Ubuntu 8.04 will fix this...

---

### Post by rustybronco on 2007-10-19
> **delmore said:**
> Wieman, here's the problem I have

after I install the driver with ndiswrapper and blacklist it, wlan0 stops showing up under iwlist

i only see lo and eth

also, shouldn't you run 'ndiswrapper -m' after installing the driver rather than before?

is this because im installing the rt2500usb driver with ndiswrapper and then blacklisting the rt2500usb driver?

on a clean install, if I go to "connection properties" for the wlan0 device, it tells me im using the rt2500usb driver, so im supposed to blacklist that so it doesnt use the broken driver eh? but then shoot myself in the foot cause the ndiswrapper driver is also called rt2500usb?

i read on some forgotten website that the WUSB54G uses the rt2570 driver? anyone know about that?wusb54g v4 is a rt2570 chipset.

---

### Post by rustybronco on 2007-10-19
> **justin1278 said:**
> Ok guys, still nothing is working, I'm about ready to give up on this :(

I appreciate the help and time you have put in to help me with this issue, but hopefully Ubuntu 8.04 will fix this...buy something with an atheros chipset,  I bought  a dynex dx-wgnbc pcmcia for 20.99 and a dx-wgdtc desktop for 22.49@ best-buy on clearance I figured the money I saved for an os I could splurge. Don't wait for 8.04 enjoy 7.10 now.

P.s. didn't get much time to try the ndis-wusb today and tommorow I have to work, as soon as I can I will.

---

### Post by justin1278 on 2007-10-19
> **rustybronco said:**
> by something with an atheros chipset,  I bought  a dynex dx-nbc pcmcia for 20.99 and a dx-dtc desktop for 22.49@ best-buy on clearance I figured the money I saved for an os I could splurge. Don't wait for 8.04 enjoy 7.10 now.

P.s. didn't get much time to try the ndis-wusb today and tommorow I have to work, as soon as I can I will.

I'm not missing Ubuntu 7.10, I can bring it with me anywhere on my notebook :)

Anyways yes you're right I should just go get a new wireless adapter, any particular brand you recommend which is supported?

I would prefer a USB adapter if you know of a good one which is Ubuntu compatible :)

---

### Post by delmore on 2007-10-20
i cant do windows anymore after almost 2 years of Ubuntu, its just horrible, im gonna buy a new receiver tomorrow...

whats a good B/G wireless receiver that DOES work in Gutsy and is most likely to work down the line?

:popcorn:

---

### Post by rustybronco on 2007-10-20
notebook card/pcmcia or a desktop card?  
wireless b, g, gs or n?

I have a linksys wpc54g v2 (acx-111 chipset)   a dynex dx-wgnbc (atheros chipset) both are "g" cards and work with 7.04 and 7.10
and I have a dynex-wgdtc (atheros chipset) "g" card it works in 7.04 and 7.10

[http://www.dynexproducts.com/pc-435-4-dynex-80211g-wireless-g-wireless-desktop-card.aspx](http://www.dynexproducts.com/pc-435-4-dynex-80211g-wireless-g-wireless-desktop-card.aspx)
[http://www.dynexproducts.com/pc-436-4-dynex-80211g-wireless-g-wireless-notebook-card.aspx](http://www.dynexproducts.com/pc-436-4-dynex-80211g-wireless-g-wireless-notebook-card.aspx) 

who knows about 8.04 and beyond.

---

### Post by rustybronco on 2007-10-20
> **justin1278 said:**
> I'm not missing Ubuntu 7.10, I can bring it with me anywhere on my notebook :)

Anyways yes you're right I should just go get a new wireless adapter, any particular brand you recommend which is supported?

I would prefer a USB adapter if you know of a good one which is Ubuntu compatible 
:) I don't have any good ideas for a wireless usb, maybe someone can recommend one.

---

### Post by justin1278 on 2007-10-21
> **rustybronco said:**
> I don't have any good ideas for a wireless usb, maybe someone can recommend one.

Well USB is not required, I would just prefer to have USB, do you know any PCI cards that are well supported?

---

### Post by wieman01 on 2007-10-21
"Netgear WG311T" for instance. See this thread:

[http://ubuntuforums.org/showthread.php?t=363633&page=3]("http://ubuntuforums.org/showthread.php?t=363633&page=3")

---

### Post by wesswei on 2007-11-07
This could be two weeks too late, but in case anyone ever has any problems with ubuntu gutsy gibbon 7.1 and using a linksys wusb54g VERSION 4 wireless usb adapter...


I had similar problems, but ran fine on feisty and on debian etch although i had to tweak it to work at all.


Firstly wusb54gv4 uses rt2500/rt2570. if you use [serial monkey's drivers]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads"), it's rt2570.  the latest release fails to compile properly with 7.10, but the latest cvs hourly tarball compiles fine. after compile, make sure you change the interfaces file from /etc/network/interfaces

replace wlan0 with rausb0

save

if it doesn't start, try starting and stopping the network /etc/init.d/networking restart or stop then start

be sure to modprobe rausb0

boom! restart and hopefully you should be up. you might have to manually configure you network using network manager, but hey, at least it works!

cheers!

---

### Post by spezticle on 2007-11-09
Thanks :) I have actually gotten my hardwire setup taken care of so no more wireless :) That works fine so i no longer need to use wireless, i s'pose i'll try it anyway just to see if that works, but thanks anyway.
~cheers

---

### Post by wesswei on 2007-11-14
no worries! if you do try let me know how it works, I'd be happy to hear if it did or not. 
cheers! :)

---

### Post by wieman01 on 2007-11-15
> **wesswei said:**
> no worries! if you do try let me know how it works, I'd be happy to hear if it did or not. 
cheers! :)
If you happen to own a Ralink based adapter, try the tutorial in my signature.

---

### Post by robjoski on 2007-12-19
There is another way to get your adapter working without using ndiswrapper...

1. Download the rt2570 driver from [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
2. Open up a terminal...
```
$ tar xvzf rt2570-cvs-daily.tar.gz
$ cd Module         ***
$ make
$ sudo make install
$ sudo modprobe rt2570
$ sudo modprobe -r rt2500usb
$ hal-set-property --udi /org/freedesktop/Hal/devices/usb_device_13b1_d_noserial_if0 --key info.linux.driver --string rt2570
```*** wherever the "Module" folder is - sometimes when the archive is updated, it gets moved...
Oh, and you might have to run the last command more than once (I had to).

I hope this works for you!

EDIT: I forgot two very important modprobe commands.

---

### Post by cutlerite on 2008-04-06
**This post could be related to an Ubuntu bug filed at**: 134660 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				When I upgraded to Ubuntu 8.04, it broke my wireless, and neither of these methods work.    I get:

rausb0: ERROR while getting interface flags: No such device.

What is odd, is that it is picking up the SSID but not listing any signal strengths...

has anyone else gotten it working in Hardy?

---

### Post by wieman01 on 2008-04-06
No, Ralink is still not working. Tried with a WUSB54G v4. I am tired...

---

### Post by jacoblyles on 2008-04-27
> **robjoski said:**
> There is another way to get your adapter working without using ndiswrapper...

1. Download the rt2570 driver from [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
2. Open up a terminal...
```
$ tar xvzf rt2570-cvs-daily.tar.gz
$ cd Module         ***
$ make
$ sudo make install
$ sudo modprobe rt2570
$ sudo modprobe -r rt2500usb
$ hal-set-property --udi /org/freedesktop/Hal/devices/usb_device_13b1_d_noserial_if0 --key info.linux.driver --string rt2570
```*** wherever the "Module" folder is - sometimes when the archive is updated, it gets moved...
Oh, and you might have to run the last command more than once (I had to).

I hope this works for you!

EDIT: I forgot two very important modprobe commands.

Will this work in 8.04?

---

### Post by jabba80 on 2008-05-23
> **cutlerite said:**
> 
What is odd, is that it is picking up the SSID but not listing any signal strengths...

same problem here, was trying with an wusb54g, but no effort yet :(

---

### Post by AlexMono94 on 2008-05-24
[http://youtube.com/watch?v=fskARysZRwM](http://youtube.com/watch?v=fskARysZRwM)

Hope it helps.

---

