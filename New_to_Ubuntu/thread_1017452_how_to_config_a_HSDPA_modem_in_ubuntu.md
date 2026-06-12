---
title: "how to config a HSDPA modem in ubuntu"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Nisal on 2008-12-21
how to config a HSDPA modem in ubuntu???

i cant install my hsdpa modem to ubuntu can any one help me regarding this plz?

---

### Post by Zeedok on 2008-12-21
I can't help you . . . I don't think.  You'll need to give us some more information. Eg are you using a USB dongle, a mobile phone that you're trying to set up as a modem?

---

### Post by Nisal on 2008-12-22
> **Zeedok said:**
> I can't help you . . . I don't think.  You'll need to give us some more information. Eg are you using a USB dongle, a mobile phone that you're trying to set up as a modem?

ya im using a usb dongal

---

### Post by Zeedok on 2008-12-22
As I said before, I tried and ultimately failed to get a wireless USB dongle to work - I had to try and use ndiswrapper (which allows you to use windows drivers on linux).

Things may have changed now with NetworkManager 0.7 (which shipped with Ubuntu 8.10).

You need to list (and search the forums) for any posts which are about your exact make and model of your USB dongle to see if someone has got it working.  The first place to check is [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters"), the wiki hardware compatibility page.

If I was you, I'd seriously consider picking up a wireless card that is listed as "Works out of the box" on the wiki - it saved me hours of frustration.

Good luck

---

### Post by scorp123 on 2008-12-22
> **Zeedok said:**
>  If I was you, I'd seriously consider picking up a wireless card ....  HSDPA (a mobile phone technology) and Wireless (802.11 a/b/g/n) are _NOT_ the same!  ](*,)

---

### Post by scorp123 on 2008-12-22
> **Nisal said:**
> how to config a HSDPA modem in ubuntu??? How about giving more details?? :confused:

- What Ubuntu version are you running?
- What's the make and model of your HSDPA modem??

Without such information it's pretty much impossible to tell you anything.

Here a few threads ... depending on the modem which you have or don't have it maybe helps, or maybe it's totally useless. You didn't say which modem you have so it's not really possible to make useful suggestions.

Beware that some of those postings are a bit outdated ... most 3G modems that are currently in circulation (e.g. Huawei E220) should "just work" with the new Ubuntu 8.10 (I know that my Novatel MC950D does ... I plug it in, and it "just works").

Samsung SGH-G800 + Linux
[http://ubuntuforums.org/showthread.php?t=639362](http://ubuntuforums.org/showthread.php?t=639362)

Cell phones as modems:
[http://ubuntuforums.org/showthread.php?t=639330](http://ubuntuforums.org/showthread.php?t=639330)

Cell phones as bluetooth modems:
[http://ubuntuforums.org/showthread.php?t=656431](http://ubuntuforums.org/showthread.php?t=656431)

mostly for Novatel Ovation MC950D (Three, Vodafone, Sunrise, many other providers), but might work for more modems:
[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)

3G modems in general:
[http://ubuntuforums.org/showthread.php?t=569767](http://ubuntuforums.org/showthread.php?t=569767)

Huawei E220:
[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)
[http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html](http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html)
[http://oozie.fm.interia.pl/pro/huawei-e220/index.html](http://oozie.fm.interia.pl/pro/huawei-e220/index.html)

---

### Post by g0rd99 on 2008-12-26
Hi Nisal
Here's something that works for me. I haven't tried it extensively, and sometimes these things work occasionally, but give it a try.

Old  April 28th, 2008   	   #1
brentwas
First Cup of Ubuntu
 
Join Date: Apr 2008
Posts: 5
Thanks: 0
Thanked 1 Time in 1 Post
	
Smile HOWTO conect to internet with Huawei E226 usb modem
hi friends,

recently i connected my usb modem type Huawei E226 on to Ubuntu 8.04
great news is that i was able to access the web after a little google research only.

here are the steps to follow:
1. download from the Add/Remove... tab the 'GNOME PPP' program.
2. it installs in the Applications/Internet pull down menue
3. plug in the E226 modem
4. modem LED should blink now
5. start the program 'GNOME PPP'
6. enter your username, password and phonenumber. note that most providers have standard phrases or words. if you don't know then check this: [www.taniwha.org.uk/gprs.html](www.taniwha.org.uk/gprs.html)
7. click on 'setup'
8. click on 'detect'
9. change to tab 'networking'
10. depending on your provider adjust IP, DNS settings if needed. also the info is found on [www.taniwha.org.uk/gprs.html](www.taniwha.org.uk/gprs.html)
11. change to 'options' tab
12. activate 'dock in notification area'
13. thats it!
14. click close and now 'connect'
15. it takes abt. 10 secs and you are online.


any question please feel free to ask.

I'm using 8.10, and it worked for me.
Gord

---

### Post by Illuminated on 2009-02-09
Or if it is a t-mobile u can create the "wvdial" : 

[Dialer tmobileusb]
Phone = *99***1#
Username = web
Password = web
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","general.t-mobile.uk";
New PPPD = yes

Ps. I am new to ubuntu and don't realy know what i am doing but this worked for me on a "web'n'walk usb stick III"

---

### Post by arunarw on 2010-12-22
what is version ubuntu you use...?....network connection configure manually it's work better.check your dongle work at your ubuntu version...ok..

---

