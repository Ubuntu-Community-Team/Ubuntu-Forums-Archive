---
title: "bigpond next g wireless broadband"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by plbee on 2007-04-09
Very new to Ubuntu, and Linux, but quite adept with Windows. Am trying to get internet connection going using bigpond wireless next g broadband. Have maxon BP3-EXT modem all working fine in XP. Have looked at the quozl info page, but it all seems a bit confusing. Tried a couple of the options, but could not get modem recognised at all, probably because cannot fathom the methodology. Was using the terminal interface to type in all the lines, and got msg that not able to do this, and also got "no such file" msg. Was going with the "ask the usb/serial module to adopt the device" and typed in all the required text without success. Anybody have a step-by-step solution to make this work? (bearing in mind I am total newbie) Thanks to anybody that can help.

---

### Post by Frans81 on 2007-09-22
I got one of these units working today. it was a blue BP3-USB with a bigpond sticker.
there are a few ways to get this working. this is the way that i got it working first.

**Step 1.**
have your user name and password ready. [COLOR="Red"]THEY ARE CASE SENSITIVE[/COLOR].
go to [https://www.bigpond.com/mybigpond/default.asp]("https://www.bigpond.com/mybigpond/default.asp")    and enter your [email]username@bigpond.com[/email] and password in the login box on the left.

if the username and password is correct you will be able to see info on your plan.
doing this saves a lot of piss farting around if you have the password wrong (remember it is case sensitive). Trust me, I found out the hard way.

Write you user name and password down in exact case.

**Step 2.**
Plug the modem into to a USB port.
when the Blue LED has stopped flashing and is on solid Blue, then you have enough signal to make a connection. if the blue LED is blinking, then you don't have enough signal strength. the purveyor of the BP3USB [Maxon Australia]("http://maxon.com.au") sells [external antennas for the device in there online store]("http://maxon.com.au/shop/index.php?cPath=22")
The LED will turn green when when a point to point link has been established (ie you are connected to the internet)

**Step 3.**
open a terminal
```
ls /dev/ttyUSB*
```
if you can see 3 ttyUSB devices then you are in luck. otherwise you may have to open a terminal and type
```

sudo insmod /lib/modules/`uname -r`/kernel/\drivers/usb/serial/usbserial.ko \vendor=0x16d8 product=0x6280

```
this binds you modem to a tty device.

**Step 4.**
First download these files to your desktop.
[ppp.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=37181&d=1183447467")
[sierra.v.1.0.6.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=37181&d=1183447467")

Then Extract the archives downloaded by [Right click] [Extract Here]

**Step 5.**
The files in the ppp.tar.gz archive that you should now have extracted should be moved to 
/etc/ppp/peers/

the easiest way to do this is open a terminal and then 
```
sudo nautilus
``` then enter your password. this will give the file manager root access.

1) navigate to /home/[COLOR="Red"]Your Username[/COLOR]/Desktop/ppp/
2) select all of the files and copy.
3) navigate to /etc/ppp/peers/
4) paste the files that you copied.

**Step 6.**
open the file gsm with a text editor. (/etc/ppp/peers/gsm) you will need root access if you don't already have it.
on line 3, make sure that it says /dev/ttyUSB1
on line 21, change [email]username@bigpond.com[/email] to your [email]username@bigpond.com[/email]
on line 22, change [COLOR="Red"]your password[/COLOR] to your password (remember it is case sensitive)
Save the file and close it.

**Step 7.**
open a terminal
TIP - you can press TAB to complete a path after typing a few characters

```

sudo su [enter password]
cd /home/[COLOR="Red"]Your Username[/COLOR]/Desktop/sierra.v.1.0.6/ 
make
make install

```

**Step 8.**
you should be ready for testing now.

to dial type
```
pon gsm
```

to hang up open a terminal and type
```
poff gsm
```

if you connect successfully, in the terminal window it should tell you what IP address you have been assigned. sorry i don't have a terminal output of a successful connection as i was setting this up for someone else and i don't have the modem any more. 
if after about 30 seconds, if it has not said hanging up then chances are that it has connected.

to test it
```
ping www.google.com
```
if you get a response then it is all working.

---

### Post by cobelloy on 2007-09-28
hi I also have this modem and I am using it right now with kubuntu - it was very simple and just uses the usb serial module (you dont need to patch the sierra module), so far I have had great speed with it too.

mine has three leds and they are all red, bottom one is power, top one is connection (and is always flashing - or weak) middle one is send/recieve

even on a weak signal it works just fine.

also dont get the extra antennas that are designed for the modem, they are useless, get a car kit antenna for a 3g/nextg phone and have a 'patch cable' made the antenna goes on your roof or external wall and will boost a weak signal much better that the ones you can buy from maxon

but as I said with a weak signal I can still download a 700meg iso in around an hour

open a terminal and type:

sudo insmod /lib/modules/***********/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280

where *********** is what is produced by the uname -r command

then I used kppp to set up a dial up connection using *99***1#

user name is your whole email address (user@bigpond.com)

I find KDE easier to configure, maybe consider getting the kubuntu image - I downloaded it from the bigpond file library - which doesnt count to your monthly download limit, and it only took about an hour to get from there too.

---

### Post by sharke on 2007-10-14
> **cobelloy said:**
> hi I also have this modem and I am using it right now with kubuntu - it was very simple and just uses the usb serial module (you dont need to patch the sierra module), so far I have had great speed with it too.

mine has three leds and they are all red, bottom one is power, top one is connection (and is always flashing - or weak) middle one is send/recieve

even on a weak signal it works just fine.

also dont get the extra antennas that are designed for the modem, they are useless, get a car kit antenna for a 3g/nextg phone and have a 'patch cable' made the antenna goes on your roof or external wall and will boost a weak signal much better that the ones you can buy from maxon

but as I said with a weak signal I can still download a 700meg iso in around an hour

open a terminal and type:

sudo insmod /lib/modules/***********/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280

where *********** is what is produced by the uname -r command

then I used kppp to set up a dial up connection using *99***1#

user name is your whole email address (user@bigpond.com)

I find KDE easier to configure, maybe consider getting the kubuntu image - I downloaded it from the bigpond file library - which doesnt count to your monthly download limit, and it only took about an hour to get from there too.

Yes  the usb-serial module will work just fine  but will be limited to download speeds of around 62 KBPS  due to limeted cach size.
With the sierra patch i have download speeds upto 220 KBPS with the standard modem arials supplied. In windows shows average connection.

Wirh a yaggi 12 db gain rooftop aerial i have download speeds up to 395 KBPS. In windows shows very good connection .

I just downloaded the gutsy realease cd 695 MB in 43 Minutes.

If you have not already done so go to bigpond.com.au in windows and update your firmware for moden this is the next speed level for nexrg wireless.

Also if you have updated to the latest connection software in windows you are using the sierra or airprime driver in windows.

Regards
Sharke

---

### Post by plbee on 2007-10-17
Heya Sharke ... how're ya keeping? Read your last post abt the yagi you have. Have been thinking about getting one ... where did you get it and how many $$$$?
Am guessing it would be 5 elements or more. Did you find that if you aimed it at the nearest tower it works all the time. Just thinking that if the tower gets a bit busy, phones will switch to a different one. If you have a directional antenna that cannot happen I think. Have you had any drop-offs or other problems with it?
Cheers Plbee

---

### Post by sharke on 2007-10-17
> **plbee said:**
> Heya Sharke ... how're ya keeping? Read your last post abt the yagi you have. Have been thinking about getting one ... where did you get it and how many $$$$?
Am guessing it would be 5 elements or more. Did you find that if you aimed it at the nearest tower it works all the time. Just thinking that if the tower gets a bit busy, phones will switch to a different one. If you have a directional antenna that cannot happen I think. Have you had any drop-offs or other problems with it?
Cheers Plbee

Well thankyou
i bought from the rf shop in brisbane
[http://www.rfshop.com.au/Default.aspx?tabid=426&CategoryID=295&Category2ID=906&Category3=Yagi&List=1&Level=3&ProductID=2909](http://www.rfshop.com.au/Default.aspx?tabid=426&CategoryID=295&Category2ID=906&Category3=Yagi&List=1&Level=3&ProductID=2909)

I had some trouble getting the correct adaptor for the usb desktop modem but after sending a pic of the modem they got it sorted.

Yes i do get fluctuation in download speed but have never been les than say a 15% gain above the std modem attached arial usual speed is around 170kbps-240kbps maxing to arround 395kbps
Please beaware that this is subject to  my  connection an can vary due to distance from transmitter location of airial in elationship to outside interference. I set it up in windows adiusting height and direction untill i got the best possible signal strength and have not ghanged it since.  
Regards
Sharke

---

### Post by plbee on 2007-10-18
Thanx for the info Sharke ... how many bars do you get with the rabbit ears. I am guessing you would now get a full 5 bar?
I usually get 3 or 4 here, depending on conditions, and without connecting, then it sometimes has 5, but as soon as you connect, it drops by 1 bar. 
The price seems reasonable, and it works well. I am getting 1.8Mb and sometimes over 2Mb off the bigpond test site with ping times average 250ms.
Have been using voip lately and it is ok, but a small lag is sometimes apparent. I think that's due to slower uplink. I think it would be better with the 7 element yagi cos that should have a really high gain .... possibly 15db at a guess.
P

---

