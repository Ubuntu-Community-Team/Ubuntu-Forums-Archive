---
title: "Tethering 6800/Mogul/Titan (Sprint)"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by astanix on 2007-08-10
I've been trying all day to get my Ubuntu 7.04 to use my HTC 6800 as a modem.

```
[ 5409.840000] usb 1-1: new full speed USB device using uhci_hcd and address 15
[ 5410.016000] usb 1-1: configuration #1 chosen from 1 choice
[ 5410.020000] ipaq 1-1:1.0: PocketPC PDA converter detected
[ 5410.020000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
```

wvdial.conf is as follows
```

[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 921600
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = #777
Password = 
Username = 
Idle Seconds = 0
Carrier Check = no
```

I've followed all the guides I've found to get this setup.
When I type wvdial I get the following output from my laptop:

```
astanix@astanix-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
CLIENTCLIENT
--> Sending: ATQ0
CLIENT
--> Re-Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
CLIENT
--> Modem not responding.
astanix@astanix-laptop:~$ 
```

and this is on the phone screen for a while, even after the wvdial fails... it disappears eventually, but i have to soft reset to try wvdial again.

[IMG]http://img373.imageshack.us/img373/1586/dsc00049xo8.jpg[/IMG]

I can also get this screen to show up if I just try to connect with kppp or gnome-ppp or the default network manager modem thing.

Any help at all would be greatly appreciated.

---

### Post by astanix on 2007-08-11
bump

---

### Post by gnubunny on 2007-08-14
I have been trying to figure out how to do this myself. All i know concerning the Phone as modem for the mogul, that it appears not to operate like the 6700. 

The way it works on windows, is that it seems to connect via ICS, instead of a directly dialing over it. 

You launch the internet connection sharing, select connect and then plug the device in and that is it, at least that is how it work on a windows box. 

Also you must have a phone as modem plan in order for it to work our it will fail to login.

---

### Post by watson540 on 2007-08-19
you dont HAVE to have a PAM plan to tether. there are ways around that already. 

I myself have tethered in xp through virtualbox with my 6800, but not quite the same, so I would like to know as well.
I do know this, on the phone under settings>connections>usb to pc there is an option for something like "advanced network functionality". if I have that box checked, the these modules load... rndis_host and cdc_ether.

What that ends up doing is creating a device called eth1 on my system, so it sees it as somewhat of an ethernet card. I dont run ubuntu so you might have a different reaction to that.

Also, when  I tether, i start up the ICS app on the phone first (have PIE connect to the net for you first) and hit connect. I do all this BEFORE I plug the usb cable in. After PIE has connected you to the net, and you have started ICS and hit connect...THEN plug the usb cable in.. The point is, with the ICS app running, the system see's the phone as yet ANOTHER usb device which is not recognized.

A little note you might want..if tethering with the ICS app, be sure you hit DISCONNECT b\efore you eit the app. This is very important or you will keep getting an "error 67' while trying to connect to the net everytime after if you dont hit disconnect

---

### Post by gnubunny on 2007-08-29
I have pam plan on my account. I am still getting the same results. I am not a an expert on these things, but i think it requires rndis or something like that in order for it to work.

---

### Post by watson540 on 2007-08-29
> **gnubunny said:**
> I have pam plan on my account. I am still getting the same results. I am not a an expert on these things, but i think it requires rndis or something like that in order for it to work.


man. you obviously didn't read my post right above yours and its apparent you have no idea wtf your talking about. let me spell it out for you then. 

THE MOGUL WILL NOT ACT AS A MODEM OUT OF THE BOX. unless you have bluetooth and enable the DUN profile. as far as the old methods though. they are gone. ics has taken its place. even though the framework is still in wm6

so here's the deal once again noob. you cannot tether the mogul in linux atm UNLESS you have a bluetooth adaptor. if you are lucky enough to have one then go over to xda developers forum and search on how to tether via BT. otherwise...give it up

and yes it does act as an rndis device..duh..that's what it is..next time try to read the whole thread man..pitiful

---

### Post by gnubunny on 2007-09-18
> **watson540 said:**
> man. you obviously didn't read my post right above yours and its apparent you have no idea wtf your talking about. let me spell it out for you then. 

THE MOGUL WILL NOT ACT AS A MODEM OUT OF THE BOX. unless you have bluetooth and enable the DUN profile. as far as the old methods though. they are gone. ics has taken its place. even though the framework is still in wm6

so here's the deal once again noob. you cannot tether the mogul in linux atm UNLESS you have a bluetooth adaptor. if you are lucky enough to have one then go over to xda developers forum and search on how to tether via BT. otherwise...give it up

and yes it does act as an rndis device..duh..that's what it is..next time try to read the whole thread man..pitiful

How about this dipshit, how do you get rndis to work in ubuntu? 

Yes i can get it to working using virtual box, and running windows xp.  Any idiot can do this, case in point, you where able to figure it out. 

The point is trying to get it to work in "Ubuntu" tethered as the subject line states. Not how to get it working using  windows, via vmware or virtual box.


If you do not know, then shut the hell up.

---

### Post by watson540 on 2007-09-18
> **gnubunny said:**
> How about this dipshit, how do you get rndis to work in ubuntu? 

Yes i can get it to working using virtual box, and running windows xp.  Any idiot can do this, case in point, you where able to figure it out. 

The point is trying to get it to work in "Ubuntu" tethered as the subject line states. Not how to get it working using  windows, via vmware or virtual box.


If you do not know, then shut the hell up.



haha.."case in point" lol...see i'm laughing because i DID get it to work suckah..It's very possible and real over usb. Now i dunno about your lame distro, but on the one i use all it took is a kernel recompile and a few things from the synce svn.

You oughtta be able to figure it out with that little hint sice you're so smart, but maybe if you beg me enough i'll actually explain it

---

### Post by gnubunny on 2007-09-22
> **watson540 said:**
> haha.."case in point" lol...see i'm laughing because i DID get it to work suckah..It's very possible and real over usb. Now i dunno about your lame distro, but on the one i use all it took is a kernel recompile and a few things from the synce svn.

You oughtta be able to figure it out with that little hint sice you're so smart, but maybe if you beg me enough i'll actually explain it

You need to just stop posting. You just contradicted your previous post. Yes there is an entire thread explaining on how to do it. I am glad you are able to read. 

Anyways, you bore me, no more feeding the troll for me.

---

### Post by watson540 on 2007-09-22
> **gnubunny said:**
> You need to just stop posting. You just contradicted your previous post. Yes there is an entire thread explaining on how to do it. I am glad you are able to read. 

Anyways, you bore me, no more feeding the troll for me.

WOW. You really are dumb. I guess you didnt see the little part on my PREVIOUS post that states it was THREE WEEKS ago. geez. 

No I didnt read any thread. Unlike most people here I went and found the answer myself by reading the mailing list and actually talking to the guy who put the code into the driver for synce on irc. So much for assumptions. They only make a dumbass outta you buddy. Anyway, read any of my previous posts in here and you will see I am far from a troll and have helped dummies like you all the time. Compared to your 5 whole posts under your belt I think it's safe to say I have a much more established reputation here. Have a nice day dummy. no hard feelings huh?

---

### Post by biggyfred on 2007-09-22
Way to take what could have been a quality thread and crap all over it, gentlemen. This is the most pathetic thread I've seen on these forums. Congrats. You two have earned it.

---

### Post by watson540 on 2007-09-22
Nice of you to join to pitiful people then. I told everyone in this thread how to tether via usb. If i get attacked though i will defend myself. As for your judgement sir.. You only have 2 posts so i take it very lightly

Also as I have done before. I invite any of you slobs to look at any of my previous posts and tell me whos the gentleman ..I have taken much time out for the forums here to helopmany people with problems that I MYSELF have solved. I dont need to always ask in a forum. So you just go look at my posts then tell me what a terrible person I am..cause i cant understand how so many people can thank such a terrible person for helping them out with various problems such as their box always locking up due to bugsin ubuntu's framebuffer and etc.

---

### Post by biggyfred on 2007-09-23
> **watson540 said:**
> I invite any of you slobs to look at any of my previous posts and tell me whos the gentleman .
That's an ironically sad sentence. I pity you.

---

### Post by moogle on 2007-10-26
I just got a mogul (6800) under sprint. I can manage to tether partially while activating the USB Modem program on the phone itself. Has anyone managed to get this working without using the USB Modem program? It seems that I /dev/ttyACM0 only shows up on my system after I run it. I'm using wvdial to connect and create the ppp0 device.

---

### Post by moogle on 2007-11-03
gee watson you're a douche 
thanks for killing a useful thread
:guitar:

---

### Post by gnubunny on 2007-11-06
well, I have been able to get it pam to work with ubuntu. But i had to do it via bluetooth. 

Seems to work fairly well. The only problem I seem to have at this time, is it will completely drop bluetooth connection, and i have to soft reset the device. And reconnect. Data speeds appear to be decent, concerning it is over a bluetooth connection, but for my needs it is very acceptable. 

This method is much easier than patching the kernel with the rndis_host patch.

---

### Post by gnubunny on 2007-11-15
Here is a pdf file that gives step by step instructions on how to do it. I wrote it up for work, but i think it is fairly easy to follow. I took my name off of it for obvious reason :) hope it helps

---

### Post by moogle on 2007-12-03
ok I'll give it a shot gnubunny, thanks for the help.
I'm actually trying to get it to work using USB, have you managed to get that working
?

---

### Post by gnubunny on 2007-12-07
Well, I have a good idea on getting it working via tethering. Just need to find the time to do so. 

I did it over BT due to the ease of getting it working via that method. 

For me doing it via bluetooth was way much more easier and less time consuming. And seems to work fairly well. The only issue i had when writing that document, was that i would lose complete BT connection with the device. And in order to get it re-established i had to soft reset the phone and reconnect it again. 

I have not had that problem after doing the last update from htc, seems the bt is working much better now.

---

### Post by moogle on 2007-12-09
yeah unfortunately, I have no BT on this laptop so I've got to get USB tethering working, What I really want to understand is what the USB Modem program does to change the way the phone is recognized by the computer. It seems that all it does is allow the phone to show up as a usbserial modem.

---

### Post by Pirat3 on 2008-03-14
> **gnubunny said:**
> Here is a pdf file that gives step by step instructions on how to do it. I wrote it up for work, but i think it is fairly easy to follow. I took my name off of it for obvious reason :) hope it helps

Thank you for posting something HELPFUL.

---

### Post by gwbennett on 2008-05-23
Unfortunate that what could have been a useful thread that answered a question that a lot of people quite possibly have turned instead into a flame war.:confused:

(Edit)
also let's everyone try to remember the kinds of Google searches that can lead here. For instance I put "mogul forum" and got here on the first page of results when I wasn't even trying to find anything Linux related. Good thing I was already familiar with Linux and this page wasn't my first impression of Ubuntu!

---

### Post by bucksgt on 2008-06-19
I stumbled upon this thread and eventually figured it out on my own. Hope this helps other:

[http://quinnmadson.blogspot.com/2008/06/how-to-htc-6800mogultitan-as-usb-modem.html](http://quinnmadson.blogspot.com/2008/06/how-to-htc-6800mogultitan-as-usb-modem.html)

HOW-TO: HTC 6800/Mogul/Titan as USB Modem in Ubuntu

sudo -s
apt-get install subversion
svn co [http://synce.svn.sourceforge.net/svnroo](http://synce.svn.sourceforge.net/svnroo) … rndis-lite
cd usb-rndis-lite/
make
./clean.sh
make install
vim /etc/network/interfaces

add:

auto rndis0
iface rndis0 inet dhcp

reboot

Plug in the phone via USB. On the phone go to programs/applications and select "Internet Sharing"

PC Connection:USB
Network Connection: Phone as Modem

Click "Connect"

---

### Post by moogle on 2008-06-20
damn you beat me to it bucksgt!
I had asked this about a week ago over at ppc-geeks 
[http://forum.ppcgeeks.com/showthread.php?t=29134](http://forum.ppcgeeks.com/showthread.php?t=29134)
but it looks like it's not propogating across the web. As long as it ends up here I'm happy though. Anyone know if they're the possibility of getting hit with PAM (phone as modem) fee using this method? I like this better than wmwifirouter since it saves some battery life.

---

### Post by GTIwhat! on 2008-06-25
Ok 

I have taken the steps, and i am still not able to surf. now i am able to see the rndis0 interface. but i have not been able to find an ip to go with it. 

Please help.

---

### Post by nization on 2008-07-01
> **moogle said:**
> damn you beat me to it bucksgt!
I had asked this about a week ago over at ppc-geeks 
[http://forum.ppcgeeks.com/showthread.php?t=29134](http://forum.ppcgeeks.com/showthread.php?t=29134)
but it looks like it's not propogating across the web. As long as it ends up here I'm happy though. Anyone know if they're the possibility of getting hit with PAM (phone as modem) fee using this method? I like this better than wmwifirouter since it saves some battery life.

Does the Mogul not charge via USB cable?  Mine should arrive tomorrow and I'll find out then, I suppose, but I hope it does, as that's just the most convenient way to tether and charge the phone at the same time.  And I have half a dozen standard mini USB chargers and cables already!

---

