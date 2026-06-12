---
title: "Wireless works but not continuesly (WUSB54Gv4)"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by saz on 2006-12-11
hey,

i have an usb card Linksys WUSB54Gv4, i've configured the wireless network through System>Admin>Network. it recognizes the card and i had no problem whatsoever configuring the network. i didn't install any drivers, and every thing runs smooth (just like on dapper was), using only native drivers, but now i'm using edgy for some weeks, and the problem is that although the wireless network works well, it only works for a period of time, after that my internet conection stops. What do i have to do make it work? i have desactivate the conection on System>admin>network, disconnect the card, connect it again and finally activate the connetion, again. I don't mind doing this, if it is the only way to escape MS Windows. but what annoys me is that when i go out and let the pc downloading, when i arrive the internet connection has disappeared and i have downloaded almost nothing... 

i've read this sticky:
[How to install WUSB54G for Dapper Drake]("http://www.ubuntuforums.org/showthread.php?t=192588")

but i didn't do it because it is for dapper, and as i said, when i had dapper it worked just fine with native drivers...

hope someone may help me, if i have been unclear in anything, please just ask me to explain it better..

---

### Post by marx2k on 2006-12-11
I have similar problems - The WiFi Networking will be working for some time but then drops connection for probably 1/2 second, then it goes right back.  Im not sure why this is happening.  Happening on an internal Linksys PCI 54Mbps G card as well as a Belkin PCMCIA Wireless B card for my laptop.

---

### Post by saz on 2006-12-11
this guy has similar problem too
[http://www.ubuntuforums.org/showthread.php?t=314614]("http://www.ubuntuforums.org/showthread.php?t=314614")

---

### Post by FrodoB on 2006-12-11
What is the chipset in this device?

---

### Post by wieman01 on 2006-12-11
I had a similar problem too, but I eventually discovered a workaround: Decreasing the "beacon interval" (router settings) from the default value of 100 to 10-20. That worked & my network connection has not dropped since (Linksys WUSB54G and WRT54G). I would try different wireless settings & do some testing.

Chipset is Ralink.

---

### Post by dbott67 on 2006-12-11
There definitely seems to be a problem with network manager in Edgy.  I've been seeing lots of 'dropped' wifi connection problems and haven't been able to help any of them.

wieman01 may be onto something here.  Log into your router and change the beacon.  I've got a D-Link 614+ & my settings are under ADVANCED > PERFORMANCE.

Just as a matter of record, I down-graded back to Dapper after about a month running Edgy on my desktop PC (I didn't upgrade my laptop --- still on Dapper).  I had frequent lockups in Firefox, my network drives & home partitions would take a minute or more to open, and other strange stuff.

-Dave

---

### Post by eggdeng on 2006-12-12
Tried wieman01's suggestion of decreasing the beacon interval but no joy. One thing I've noticed is that, even when the network is unreachable (you can't ping the router), the wireless card is still seeing the access point (iwconfig will tell you the mac address of the ap). So I think the problem is higher up the stack than the actual physical connection issue.

---

### Post by wieman01 on 2006-12-12
> **eggdeng said:**
> Tried wieman01's suggestion of decreasing the beacon interval but no joy. One thing I've noticed is that, even when the network is unreachable (you can't ping the router), the wireless card is still seeing the access point (iwconfig will tell you the mac address of the ap). So I think the problem is higher up the stack than the actual physical connection issue.
Are you using "ndiswrapper" or "rt2570"? Just for the protocol...

---

### Post by eggdeng on 2006-12-12
Using ndiswrapper with a Conceptronic USB wireless adapter on Edgy.

---

### Post by wieman01 on 2006-12-12
> **eggdeng said:**
> Using ndiswrapper with a Conceptronic USB wireless adapter on Edgy.
Alright... I was more referring to Linksys WUSB54G... the initial post.

---

### Post by saz on 2006-12-12
wieman01, i'm using native drivers (rt2570, i think at least on dapper were... but on dapper worked perfectly..)

---

### Post by wieman01 on 2006-12-12
Perhaps try using "ndiswrapper" instead. I know that the RTxxxx drivers have certain drawbacks and are in a fairly early development stage. I don't recommend them. Perhaps "ndiswrapper" does a better job for you.

---

### Post by saz on 2006-12-18
> **wieman01 said:**
> Perhaps try using "ndiswrapper" instead. I know that the RTxxxx drivers have certain drawbacks and are in a fairly early development stage. I don't recommend them. Perhaps "ndiswrapper" does a better job for you.
wieman01

tried this sticky/howto, and didn't work...

[http://www.ubuntuforums.org/showthread.php?t=318539]("http://www.ubuntuforums.org/showthread.php?t=318539")

please help me...

10ks

---

### Post by wieman01 on 2006-12-18
> **saz said:**
> wieman01

tried this sticky/howto, and didn't work...

[http://www.ubuntuforums.org/showthread.php?t=318539]("http://www.ubuntuforums.org/showthread.php?t=318539")

please help me...

10ks
Ok, can you post there and tell us what you have done? What kind of encryption/authentication are you trying to set up? What does your "interfaces" file look like? Please post all your stuff there so that we can help.

_**EDIT:**_
That sticky is for wireless security only. Guess that's what you are looking for, and NOT for a "ndiswrapper" howto.

---

### Post by saz on 2006-12-19
> **wieman01 said:**
> Ok, can you post there and tell us what you have done? What kind of encryption/authentication are you trying to set up? What does your "interfaces" file look like? Please post all your stuff there so that we can help.

_**EDIT:**_
That sticky is for wireless security only. Guess that's what you are looking for, and NOT for a "ndiswrapper" howto.
sorry, that wasn't the sticky i was talking abount, this is the ridht one (ndiswrapper howto)

[http://www.ubuntuforums.org/showthread.php?t=192588]("http://www.ubuntuforums.org/showthread.php?t=192588")

i folowed it no probs, but after installing .inf file, when a reboot the device still isn't there...

---

### Post by wieman01 on 2006-12-19
When you deploy the *.INF file, please make sure that all other driver files (e.g. *.CAT, *.SYS, or similar) are also in the same folder... Otherwise the installation will fail.

If that's not the problem, what steps have you performed? Also run these commands for me and post the results:

_**Scanning for networks:**_
> iwlist scan
_**Checking network configuration file:**_
> sudo gedit /etc/network/interfaces
We'll what's going on first of all...

---

### Post by saz on 2006-12-20
well, i explained what was going on on the firste post of this thread.. the wireless connection worked, but no continuesly. i was using ubuntu's native drivers and you recommended me to use ndiswrapper. so i did:

> extracted these files to my desktop:
rt2500usb.inf, rt2500usb.cat, rt2500usb.sys

then

> 
console:
ndiswrapper -i rt200usb.inf

then

> 
console:
ndiswrapper -m

then

> 
console:
ndiswrapper -l

output: "driver present hardware present"

so every thing all right, i restarted ubuntu, went Sistem>admin>network and no wireless device was there. (remeber, as i followed that howto i had blacklisted the rt2570 driver)

as to the commamds you asked me, i'm not in ubuntu right now, but when i boot it i'll edit this and paste the outputs...

---

### Post by wieman01 on 2006-12-20
And again, commands given in post #16 will help a lot. Trying to understand if you have installed "ndiswrapper" successfully. If the scanning works & "/etc/network/interfaces" look fine, then you are one step further. Please post the stuff & we'll see.

---

### Post by saz on 2006-12-21
here we go: 

first command:
> 
sa@Sazito:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rausb1    Scan completed :
          Cell 01 - Address: 00:13:10:0A:D3:75
                    Mode:Managed
                    ESSID:"linksys"
                    Encryption key:on
                    Channel:11
          Cell 02 - Address: 00:11:D8:8D:60:4B
                    Mode:Managed
                    ESSID:"default"
                    Encryption key:on
                    Channel:1
          Cell 03 - Address: 00:11:50:58:1A:3F
                    Mode:Managed
                    ESSID:"belkin54g"
                    Encryption key:on
                    Channel:11

sit0      Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.


this with the rt2570 out of the blacklist

with the rt2570 ON the blacklist, here is what i get:

> 
sa@Sazito:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.


not so successful...

second command:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback






iface rausb1 inet dhcp
wireless-essid linksys
wireless-key bae760db54edfca9d8497e2eff







auto rausb1


every thing is right again...

any ideas whta's the problem?

if i take the rt2570 off the blacklist, every thing will work well, but again the old problem, from time to time connection will drop, as i first explained in post #1...

thnks, pls help me

---

### Post by wieman01 on 2006-12-21
The reason why your scanning is not successful is that your "interfaces" file has not been updated. Please blacklist "rt2570" and make "/etc/network/interfaces" look exactly(!) like this:
> auto lo
iface lo inet loopback

auto [COLOR="Red"]wlan0[/COLOR]
iface [COLOR="Red"]wlan0[/COLOR] inet dhcp
wireless-essid linksys
wireless-key bae760db54edfca9d8497e2eff
Then restart the network or the computer:
> sudo /etc/init.d/networking restart
Please also ensure that the "ndiswrapper" module is loaded at startup. Add "ndiswrapper" at the end of this file (just the word "ndiswrapper" in a new line):
> sudo gedit /etc/modules
If it has been missing, restart the PC.

If this still does not work, please also post the contents of this file:
> sudo gedit /etc/modprobe.d/ndiswrapper
That should do... no worries, we'll find a way.

---

### Post by saz on 2006-12-22
did everything exactly as you said, but still doesn't appear...

did the command you asked if didn't work, here is what i get:

> alias wlan0 ndiswrapper

so i think it's correct, and should work...

i'll be away for thw weekend, but when i come back i hope we can resolve this problem, thanks for the help you're giving me, i really appreciate it!

be cool

---

### Post by MdaG on 2006-12-22
I've also got the same problem. Until there's a solution to it I'm forced to use XP :(

---

### Post by wieman01 on 2006-12-23
One important thing... You cannot use Ethernet & wireless at the same time. You have to pull the cable while you are trying to connect to a wireless network. Could that be the problem?

---

### Post by saz on 2006-12-24
nope, no ethernet cable connected...

---

### Post by saz on 2006-12-24
well, i managed to get  the device to appear on System > Admin > Network, even with rt2570 blacklisted!

1. get the latest ndiswrapper version (do not use the one in synaptic!!)
2. install ndiswrapper and the windows driver
3. modprobe it
4. gedit /etc/network/interfaces, and change rausb1 or wlan0 to **rausb0**

done!!

now let's see if it works continuesly, with no interruptions... hope it does...

i'll let you know...

Merry Christmas!!

---

### Post by saz on 2006-12-24
well, you can see that i my previous post was written minutes ago... i'm writing again cuz the connection have already droped... so back to 0, but now using ndiswrapper.. ](*,) 

help... anyone there??:confused: 

hope wieman01 can help out this one... :-k 

my guess is that ndiswapper may be using the alternative driver (rt2570).. but i'm propably wrong.. :) 

merry christmas anyway..

> sa@Sazito:~$ ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2570)


the device id is correct, checked with > lsusb

---

### Post by wieman01 on 2006-12-24
Can you post "/etc/network/interfaces" please? And by way... "rausb0" stands for the native driver, "wlan0" for "ndiswrapper". So I am a bit confused as far as you configuration is concerned...

---

### Post by saz on 2006-12-24
so lets get everything clear

this is the /etc/network/interfaces file i had before:

> auto lo
iface lo inet loopback

auto **wlan0**
iface **wlan0** inet dhcp
wireless-essid linksys
wireless-key bae760db54edfca9d8497e2eff

i changed to:

> auto lo
iface lo inet loopback

auto **rausb0**
iface **rausb0** inet dhcp
wireless-essid linksys
wireless-key bae760db54edfca9d8497e2eff


with the first one I could not see my device in sistem > Admin > network (if i had blacklisted rt2570), but with the second i can, even with rt2570 blacklisted!

**_Note:_** when i used the native drivers my device was **rausb1**

please, if i was unclear, let me know!

thanks!

---

### Post by wieman01 on 2006-12-25
If you are using "ndiswrapper", then "wlan0" is the correct interfaces name. Have you performed all [these steps]("http://www.ubuntuforums.org/showthread.php?t=280176&page=2") (post #20) when configuring your card?

---

### Post by saz on 2006-12-25
yes made it...

> sa@Sazito:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rausb0    Scan completed :
          Cell 01 - Address: 00:13:10:0A:D3:75
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:D8:8D:60:4B
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.


you can see that device is named rausb0...  :s and before i use ndiswrapper (when i used native drivers..) it was rausb1...

---

### Post by wieman01 on 2006-12-26
Another guy seems to have the same problem, so I believe that "rausb0" is the right one then. Now back to the original question, could you test your network & see if you still have the same issues with your card?

---

### Post by saz on 2006-12-26
just started seeding ubuntu dvd and went out, if when i came back it had stopped then i had the same issues as before, if not i hadn't... but turns out that i had... now i've made some changes and it seems to be working, but i'll just seed a bit more, to make sure that the connection does not drop...

---

### Post by wieman01 on 2006-12-26
Do you have access to the router? Do you see a setting called "beacon interval"? You could change the default value i.e. reduce it. This did the trick for me a while ago (100 -> 20).

---

### Post by Floppyjoe on 2006-12-26
I think the designation of rausb just means ralink usb device wether or not it is used natively or with ndiswrapper.

---

### Post by wieman01 on 2006-12-26
> **Floppyjoe said:**
> I think the designation of rausb just means ralink usb device wether or not it is used natively or with ndiswrapper.
Well, I don't think so ... or put it this way: I thought that's not the case. Usually "wlan0" stands for "ndiswrapper", "rausbx" for the Linux driver. But perhaps this differs with the version of "ndiswrapper" that you are using. My "ndiswrapper" interface is referred to as "wlan0" (WUSB54G V4 - Ralink).

---

### Post by Floppyjoe on 2006-12-26
I have the same device and it shows up as rausb1 on one of my computers when used with ndiswrapper after blacklisting the native driver which did not work.

---

### Post by wieman01 on 2006-12-26
> **Floppyjoe said:**
> I have the same device and it shows up as rausb1 on one of my computers when used with ndiswrapper.
Ok, good to know. Another user has confirmed the same thing so I believe this has something to do with the version of "ndiswrapper" you have installed. Thanks for pointing this out.

---

### Post by saz on 2006-12-26
hey, i think i got it working.. :o 

well, as wieman01 said, ndiswrapper is configures to wrok using wlan0, but it recognises the device as rausb0, which is pretty strange :confused:,  so what i though, probably the files are configured to work with wlano and not with rausb0, so...

i went to these files:
> /usr/sbin/ndiswrapper
>  /etc/modprobe.d/ndiswrapper
> /etc/network/interfaces

and just changed every single "wlan0" to "rausb0". i've been using this configuration for 2 days and not once has it droped. today i've been seeding Edgy DVD since 9.00am till now, 14,5 hours have passed and no "interruptions" happened. so i think it's working, but if it drops again, i'll come here begging for help :-D 

still wieman01, i do have access to the router and i am able to see the beacon thing, even though i've managed to make it work, do you think i should change it? (actually the value is 100) what exactly is this beacon thing and how will it affect my network?:-k 

thank you very much for your precious help! i'm really glad i got this working, and that i'll be able to go to school knowing that i'll have my downloads completed when i come back! thanks ;)

---

### Post by wieman01 on 2006-12-27
Excellent!

As for the "beacon interval", please don't change it for the time being. You could read [this]("http://www.wi-fiplanet.com/tutorials/print.php/1492071") if you are interested in learning more about wireless networking, etc.

---

### Post by jamesstansell on 2006-12-31
This is interesting to read about ndiswrapper.  So far everything I've read had suggested that it always used wlan0.

Just today though I read about ifrename and at least one other similar method. which would make it possible for the device names to vary.

I've also read that although the rt2570 driver uses rausb0 the upcoming rt2x00 driver (still alpha quality?) uses wlan0.

---

### Post by brucetan on 2008-02-24
> **saz said:**
> well, i explained what was going on on the firste post of this thread.. the wireless connection worked, but no continuesly. i was using ubuntu's native drivers and you recommended me to use ndiswrapper. so i did:



then



then



then



so every thing all right, i restarted ubuntu, went Sistem>admin>network and no wireless device was there. (remeber, as i followed that howto i had blacklisted the rt2570 driver)

as to the commamds you asked me, i'm not in ubuntu right now, but when i boot it i'll edit this and paste the outputs...


Hello,

You said you extracted the driver for WUSB54G v4 - rt2500usb.xxx.  I downloaded from Linksys.com for v4 are: 

rt2500usb.inf, rt2500usb.sys, WUSB54GV4.cat

and there is no such file called rt2500usb.cat

Was it a typo??  Please kindly confirm this.  


Also, you said "blacklist rt2570" in latter posts of this thread.  Why "rt2570"?  Shouldn't it be "blacklist rt2500usb"? 

I understood from various thread discussion "rt2570" is the linux driver and not use with Ndiswrapper.  Am I wrong on this?

Bruce

---

### Post by brucetan on 2008-02-24
> **saz said:**
> hey, i think i got it working.. :o 

well, as wieman01 said, ndiswrapper is configures to wrok using wlan0, but it recognises the device as rausb0, which is pretty strange :confused:,  so what i though, probably the files are configured to work with wlano and not with rausb0, so...

i went to these files:




and just changed every single "wlan0" to "rausb0". i've been using this configuration for 2 days and not once has it droped. today i've been seeding Edgy DVD since 9.00am till now, 14,5 hours have passed and no "interruptions" happened. so i think it's working, but if it drops again, i'll come here begging for help :-D 

still wieman01, i do have access to the router and i am able to see the beacon thing, even though i've managed to make it work, do you think i should change it? (actually the value is 100) what exactly is this beacon thing and how will it affect my network?:-k 

thank you very much for your precious help! i'm really glad i got this working, and that i'll be able to go to school knowing that i'll have my downloads completed when i come back! thanks ;)

Saz, is your WUSB54G connection still stable?  Are you on Ubuntu 7.10 (Gutsy)?

---

### Post by wieman01 on 2008-02-24
> **brucetan said:**
> Hello,

You said you extracted the driver for WUSB54G v4 - rt2500usb.xxx.  I downloaded from Linksys.com for v4 are: 

rt2500usb.inf, rt2500usb.sys, WUSB54GV4.cat

and there is no such file called rt2500usb.cat

Was it a typo??  Please kindly confirm this.  


Also, you said "blacklist rt2570" in latter posts of this thread.  Why "rt2570"?  Shouldn't it be "blacklist rt2500usb"? 

I understood from various thread discussion "rt2570" is the linux driver and not use with Ndiswrapper.  Am I wrong on this?

Bruce
No typo. There should also be a .CAT file. If there isn't, don't worry and continue with the other 2 files.

You need to blacklist "rt2570usb" if you are on Gutsy and own a WUSB54G V4. Please see my tutorial (signature) for more.

---

### Post by wieman01 on 2008-02-24
> **brucetan said:**
> Saz, is your WUSB54G connection still stable?  Are you on Ubuntu 7.10 (Gutsy)?
Yes, I am on Gutsy. As of late 'nsidwrapper' has not been very stable to tell the truth. Sometimes I have to restart the PC in order for the network card to work. No idea what's going on but I look forward to Hardy.

---

### Post by saz on 2008-03-27
hey guys, that rausb thing was only up to Edgy! from edgy on wusb54gv4 is recognized as wlan0! making our lives much easier =)

cheers!

---

