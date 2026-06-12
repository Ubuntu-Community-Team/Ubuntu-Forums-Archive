---
title: "wifi-radar causes kernel panic"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by joshuaxls on 2005-11-02
I am wondering, has anyone else ever experienced a kernel panic due to wifi-radar? Actually, when the kernel panics, dhclient is the process which is currently running. But I found that when I removed wifi-radar from my system, I no longer got the kernel panic. The panic would happen about twenty seconds after booting up. At the panic, I would get a message saying that there was a bad EIP value (which I assume is the instruction pointer). Unfortunately, I didn't see any way to capture the panic, so I do not have a log to post of it.

To give you a little information about my setup:
   Laptop: Compaq Presario V2410US.
   Wireless: Broadcom chip onboard, using ndiswrapper.
   Processor: AMD Turion64 1.6 Ghz.
   
Strangely enough, the kernel panic never happened while I was at home. At home I have a personal wireless setup using a WEP key and so forth -- wifi-radar handled that just fine. The panic happens at my university, where wireless routers will give you an IP, but you will not be able to access anything outside of the school network until you open a web browser and login to the "bluesocket" gateway page which is automatically redirected to.

Without wifi-radar, I can use my wireless card normally via appropriate use of iwconfig and ifconfig in a terminal. I just like the way that wifi-radar automatically takes care of things.

I would appreciate any tips. If you need any more information, let me know.

---

### Post by killasphynx on 2005-12-15
Hey, I know that this is off your topic, but on top of giving it a bump, maybe you can help me. I'm having a hard time getting ndiswrapper to work with my laptop. I have the exact same model as you, hardware and all. The v2410US.  

So i have 3 questions for you, if you don't mind. 

1) did you use the 32 or 64 bit ubuntu version.   

2) what driver did you use ( 32 or 64 ) and was it the bcmwl5.inf that is on my windows partition? 

3) what version of ndiswrapper did you use? 

I have tried ndiswrapper versions 1.1, 1.6 and 1.7, with the bcmwl5.inf that i found on windows and no luck. I also tried all three ndiswrapper versions with the bcmwl5a.inf and the 64 bit driver from ndiswrapper site. I used the 32 bit ubuntu version. 

many thanks!

---

### Post by ztirffritz on 2006-02-19
I sure wish someone would respond to this question.  I have not had any luck with this computer and any Linux Distro.  I've gotten Suse to install, but no wireless.  I got Ubuntu AMD64 to install, but the graphics were screwed up and the wireless didn't work.  I wish that they'd get this straightened out.

---

### Post by joshuaxls on 2006-02-20
Oh, sorry guys, I can definitely help out... I have installed about three different Linux distros on this laptop and I've gotten them all to work. Currently I am running 64-bit Gentoo. If you want to use 64-bit, you'll need to get [this driver]("http://www.acerpanam.com/synapse/forms/portal.cfm?recordid=2473&formid=3394&website=AcerPanAm.com/us&originwebsite=acerpanam.com&central=1&words=All&keywords=broadcom&pupv=pu"). I found this on someone else's blog about getting Linux to work on a similar laptop ([link]("http://www.iit.edu/~kbloom1/Main/Compaq_Presario_v2310us"))

For graphics, you'll probably want to use ATI's binary drivers (I have never been able to get the open source driver to work). There are many issues with ATI's drivers, but they are usable. Basically, for now you should not put the computer in standby when using ATI's drivers. Also, use the most generic framebuffer possible inside the kernel. Anything else tends to screw up the graphics when you go back and forth (i.e. ctrl+alt+1, ctrl+alt+7) between terminals.

Let me know if you have any other questions.

---

### Post by joshuaxls on 2006-02-20
This website may interest you: [http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html]("http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html")

---

