---
title: "Help Needed SERIOSULY."
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by NfF on 2007-06-18
hey there ubuntu users,

im a very very new ubuntu user.just converted from windows u see..so i dont know ANYTHING bout ubuntu
here is my story-->

Soon after i installed ubuntu, i took my 1 year old WUSB54Gver4 Linksys USB network adapter and plugged in my linux-installed PC. Woah..Linux recognised the adapter and my adapter started to search for networks like-"Osamanetwork", or "connectandgetfreevirus". So i connected to my own"linksys", and it showed strength signal 89%, which is rather strong. So i opened firefox, and typed"yahoo.com". But all i got was "firefox couldnt connect or find the webpage". i tried other websites too.. without success and now im sitting here with my laptop asking for help.

Pls guyz help me out. My Linux pc also couldnt use the modem connection and has NO INTERNET CONNECTION AT ALL...

---

### Post by scannerdarkly on 2007-06-18
Go into Terminal and put this command in.

ifconfig

That command will show you the information of your interfaces such as IP, Default Gateway, Mac Address, etc.  If you have an IP address that starts with 169 or something like that, you don't have a true IP address.  Regardless of the output I would try to restart your router.  I had the same problem when I first started with Ubuntu 6.06.  For some reason my Belken router didn't want to give me an IP address and if it did it didn't want to let me surf the web until i restarted it.

---

### Post by sharke on 2007-06-18
I think your card uses rt73 driver go here [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

Regards
Sharke

---

### Post by dliberal on 2007-06-18
Greetings

I checked this page: [http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)

Your wireless card is listed as compatible:
 802.11g 	 WUSB54GP v.4 	 	 USB 	 Ralink 	 rt2x00 	 green  	 Driver available from manufacturer: [http://www.ralinktech.com.tw/supp-1.htm](http://www.ralinktech.com.tw/supp-1.htm) or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

It uses a ralintek chipset. If you are using Ubuntu Feisty the driver for that card is included, but it has a bug and doesn't work. Even more, by using rt61 driver can make your PC to go totally unstable. You can see more here:

[http://ubuntuforums.org/showthread.php?t=416532](http://ubuntuforums.org/showthread.php?t=416532)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91192](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91192)

I had the same problem and the solution was to black list that driver, of course, now I have no wireless but a stable computer :-S ... fu**in' feisty bugs
Good luck!

DISCLAIMER: I'm not 100% if the USB card uses the same driver as the PCI card

---

### Post by NfF on 2007-06-18
first i wanna ask- how do i blacklist my LINKSYS,NOT RALINK! adapter? 
second-my adapter i checked on the ubuwiki is either rt2500,or rt2570.
third-pls show clearly how to install my WUSB54G VERSION 4. i prefer detailed.

---

### Post by wieman01 on 2007-06-18
Oh Ralink... bad news. Does your network use a key? I mean WEP or something?

_**EDIT:**_
It's a Ralink RT2570... I've got the same one and hated the Ralink driver that comes with Ubuntu. Had to replace it by installing "ndiswrapper" etc.

---

### Post by wieman01 on 2007-06-18
Start here if you want to replace the existing driver:

[http://ubuntuforums.org/showthread.php?t=192588&highlight=rt2570+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=192588&highlight=rt2570+ndiswrapper")

---

### Post by NfF on 2007-06-18
no..i dont use all that.my security is disabled.My PC that is using ubuntu has no internet connection at all..so dont type commands that start with "apt". I sorely depend on my network adapter for internet connection.

---

### Post by wieman01 on 2007-06-18
> **NfF said:**
> no..i dont use all that.my security is disabled.My PC that is using ubuntu has no internet connection at all..so dont type commands that start with "apt". I sorely depend on my network adapter for internet connection.
Again, the driver that is currently installed is flawed. If it does not connect immediately it's a no-go. I recommend to follow the above HOWTO, it applies to both Dapper and Edgy. The current driver for WUSB54G V4 is going to be trouble, sooner or later.

If you cannot connect right now that is. Don't replace it unless you have trouble connecting via GUI.

---

### Post by NfF on 2007-06-18
Alright then..ill giv it a try. 
Will show u the screenshots

---

### Post by NfF on 2007-06-18
ok ive blacklisted the rt2570. juz to make sure it's blacklisted. ive plugged it in both of my front 
USB ports, and the power LED lit up and died.

Ok now ive downloaded ndiswrapper 1.8 and copied it to my thumb drive. how do i extract? and where should i copy the file? to desktop?

Remember im using a different comp(laptop now)

---

### Post by wieman01 on 2007-06-18
> **NfF said:**
> ok ive blacklisted the rt2570. juz to make sure it's blacklisted. ive plugged it in both of my front 
USB ports, and the power LED lit up and died.

Ok now ive downloaded ndiswrapper 1.8 and copied it to my thumb drive. how do i extract? and where should i copy the file? to desktop?

Remember im using a different comp(laptop now)
Please skip the compiling bit... "ndiswrapper" is in the repositories. Let me know if you cannot find it. Simply install all packages that contain "ndis"... that'll do. Post a message if you are ready.

---

### Post by NfF on 2007-06-18
Xp..what i mean is do i install it in terminal or extract it using archive manager?

and erm..how do i find the reposoteries. show me..

---

### Post by NfF on 2007-06-18
> **wieman01 said:**
> Please skip the compiling bit... "ndiswrapper" is in the repositories. Let me know if you cannot find it. Simply install all packages that contain "ndis"... that'll do. Post a message if you are ready.

I don't know how to find"ndiswrapper" in the repositories. Pls type out the command. and the ndiswrapper 1.8.tar.gz is currently on my desktop.

---

### Post by wieman01 on 2007-06-18
> **NfF said:**
> I don't know how to find"ndiswrapper" in the repositories. Pls type out the command. and the ndiswrapper 1.8.tar.gz is currently on my desktop.
Do you how to use Synatic? "ndiswrapper" is on the Live CD and should be installed via Synaptic. That's the easiest way. This way you don't have to use the terminal at all.

---

### Post by NfF on 2007-06-18
yep i do. brb.

---

### Post by NfF on 2007-06-18
oh man..i think i deleted some really important files.
nvr mind..

ok ive installed it.now what?

---

### Post by scannerdarkly on 2007-06-19
> **NfF said:**
> oh man..i think i deleted some really important files.
nvr mind..

ok ive installed it.now what?

Now you need to find the drivers for your card and import them into ndiswrapper.  They have documentation on this here [http://ndiswrapper.sourceforge.net/joomla/index.php](http://ndiswrapper.sourceforge.net/joomla/index.php)

---

