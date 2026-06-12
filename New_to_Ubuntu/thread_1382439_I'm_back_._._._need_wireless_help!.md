---
title: "I'm back . . . need wireless help!"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by hiloguy on 2010-01-15
OK, so I gave up on Ubuntu a few months ago.  Just too many glitches, not enough time to sort them all out.  I've regretted it ever since, so I just installed 9.10 as a dual-boot (for now) on my Dell D-620, alongside W-WP-Pro.  After reading the rave reviews, I at least expected 9.10 would find the wireless and have it ready to go.  NOT!

Everything I've tried goes through like it's going to work and then I get a little window that cheerfully tells me I'm disconnected.  "Help" is of no help.  Any tricks out there?  The wireless card is whatever came in the D-620, which is about 2 yrs old.

Thank you, thank you!  I REALLY want to make go of it this time.

---

### Post by warfacegod on 2010-01-16
First thing I would do is get updated and then go to: System> Admin.> Hardware Drivers> and activate the recommended wireless driver maybe do the video driver while your there.

---

### Post by -kg- on 2010-01-16
You may find your answer at this thread:

[http://ubuntuforums.org/showthread.php?t=1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

### Post by hiloguy on 2010-01-16
I went through enough of the listed procedures to get the "wireless connected" notice on boot, and indeed it shows connected and 100% signal strength.  The first time it got me online, but after another reboot, it still shows "connected" but when I try to get online I get "no server found."  It works with a cable, but not wireless.  

What am I missing?

---

### Post by warfacegod on 2010-01-16
Do you have your wireless encryption set up correctly?

---

### Post by hiloguy on 2010-01-17
> **warfacegod said:**
> Do you have your wireless encryption set up correctly?

I have no idea how to do that.  I've read miles of "how-to" on various sites, including this one, and when it gets to the part about "hex," I'm gone.

WHY is is to difficult to get Ubuntu 9.10 to work with the very generic wifi card in my Dell D620?

OK, sometimes I power up and it works, most of the time it does not.  When it works, I can get online.  When it does not, it shows as "connected," the signal strength is excellent, but when I try to get online, I get "cannot find server."  Plug in a wire and it works fine.  The other three laptops here all work fine.

Any suggestions?  I'm going nuts here and this is exactly why I gave up on Ubuntu a few months ago with an older version. All the reviews talk about 9.10 having fixed these kinds of issues.  I REALLY want to convert all of our computers (5 of them) to Linux, but it's hard when something so basic seems to require such a lot of Linux-specific techno-savvy.

HELP!!  Please?

---

### Post by warfacegod on 2010-01-17
> **hiloguy said:**
> I have no idea how to do that.  I've read miles of "how-to" on various sites, including this one, and when it gets to the part about "hex," I'm gone.

WHY is is to difficult to get Ubuntu 9.10 to work with the very generic wifi card in my Dell D620?

OK, sometimes I power up and it works, most of the time it does not.  When it works, I can get online.  When it does not, it shows as "connected," the signal strength is excellent, but when I try to get online, I get "cannot find server."  Plug in a wire and it works fine.  The other three laptops here all work fine.

Any suggestions?  I'm going nuts here and this is exactly why I gave up on Ubuntu a few months ago with an older version. All the reviews talk about 9.10 having fixed these kinds of issues.  I REALLY want to convert all of our computers (5 of them) to Linux, but it's hard when something so basic seems to require such a lot of Linux-specific techno-savvy.

HELP!!  Please?

No issue is ever entirely fixed regardless of your OS (Windows, Linux, etc.) no matter what the reviews say. As a first step I suggest disabling your wireless security on the router and in network manager for that connection. Browse for a bit, reboot a few times, browse each time, doing that will trouble shoot your wireless card itself. It will make sure your wireless driver is working okay.

FYI Windows (especially Vista) generally has more wireless issues than Linux. You don't hear about it because there are so many more Windows users than Linux it sort of just gets drowned in the voices as it were. Another reason you don't hear about it is because Microsoft spends tens of millions on PR and "glossing" its flaws.

---

### Post by Methuselah on 2010-01-17
Setting encryption password is not really a linux specific thing.
Is your network set to WPA or WEP and have you given network manager the correct password to connect.
Nontheless, since it is working sometimes it is unlikely that this is the issue.

The fact is that some wireless cards are not well supported in linux because the drivers are not in a great state.
In some cases, the people who make the hardware do not provide drivers and the reverse-engineered drivers (if they exist) might not be fully mature.

I understand that this laptop uses a broadcom wireless chip which is among the less well supported.
[http://hea-www.harvard.edu/~dsteeghs/dell_d600.html](http://hea-www.harvard.edu/~dsteeghs/dell_d600.html)
The best you can do is forget about it or try to get it working by using the windows drivers and ndiswrapper.
The same link above seems to be saying that the chip works well with ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by hiloguy on 2010-01-17
> **Methuselah said:**
> Setting encryption password is not really a linux specific thing.
Is your network set to WPA or WEP and have you given network manager the correct password to connect.
Nontheless, since it is working sometimes it is unlikely that this is the issue.

The fact is that some wireless cards are not well supported in linux because the drivers are not in a great state.
In some cases, the people who make the hardware do not provide drivers and the reverse-engineered drivers (if they exist) might not be fully mature.

I understand that this laptop uses a broadcom wireless chip which is among the less well supported.
[http://hea-www.harvard.edu/~dsteeghs/dell_d600.html](http://hea-www.harvard.edu/~dsteeghs/dell_d600.html)
The best you can do is forget about it or try to get it working by using the windows drivers and ndiswrapper.
The same link above seems to be saying that the chip works well with ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

OK, well, I'm not real happy to hear that the chip in my 2 yr old Dell isn't among the well supported, but I will try the ndiswrapper approach next.  I haven't done that yet, so it will be a new adventure!

Thank you very much for your reply!

---

### Post by hiloguy on 2010-01-17
> **hiloguy said:**
> OK, well, I'm not real happy to hear that the chip in my 2 yr old Dell isn't among the well supported, but I will try the ndiswrapper approach next.  I haven't done that yet, so it will be a new adventure!

Thank you very much for your reply!

More on this:

After spending a long while trying to come up with driver data that matches anything I can download from ndiswrapper, I'm wondering, since this is a W-XP dual boot, can I use the driver info I can easily get from Windoze?  It is: Dell Wireless 1490 Dual Band WLAN Minicard Driver Version 4.10.40.0, along with the location of the file.  Is there a way ndiswrapper can use this information?

---

### Post by bkratz on 2010-01-17
did someone somewhere in this thread determine what your wireless device even is?

If you go to the terminal and type in

lspci | grep Wireless

(the terminal is at Applications>>Accessories>>terminal
(that was LSPCI in lowercase)

---

### Post by knxville on 2010-01-18
It sounds like the same problem I've had, though it first came when I upgraded to 9.10.
I reckon it's because of Ubuntu One, somehow shutting out anyother internet connection made from my PC. Everytime I run Ubuntu One, it shuts down my connection, though it still show that my signal strenght is full, and does not disconnect me from IRC, but I just can't get any new packages through, nor surf the web. 

I solved it simply by making Ubuntu One, not start on startup!

Cheers.

---

### Post by warfacegod on 2010-01-18
> **knxville said:**
> It sounds like the same problem I've had, though it first came when I upgraded to 9.10.
I reckon it's because of Ubuntu One, somehow shutting out anyother internet connection made from my PC. Everytime I run Ubuntu One, it shuts down my connection, though it still show that my signal strenght is full, and does not disconnect me from IRC, but I just can't get any new packages through, nor surf the web. 

I solved it simply by making Ubuntu One, not start on startup!

Cheers.

I don't think Ubuntu One ships with start on boot as it's default. Although, it *may* do that if you install it yourself, not sure though.

---

### Post by hiloguy on 2010-01-19
Wow!  I was so excited that after only three long days of trying to get my wireless working I found this set of instructions in my book, "Beginning Ubuntu Linux." I did the blacklisting of existing drivers.  It worked.  I extracted the correct .inf file (in XP on on the same computer) and via thumbdrive installed them on the Linux  side of this Dell D620.  I installed it with ndiswrapper and it all worked as planned, right up until I opened the "Windows Drivers" box and there was my driver with a big red X through it and the words, "invalid driver."

This is getting very frustrating.  Why would this driver, which obviously works on this same computer with XP, be an invalid driver in Ubuntu 9.10?

Followup on the above:  The driver, according to XP, is bcmwlr.**sys**.  Ubuntu will only accept .**inf** files as drivers.  Is this the issue here?










> **Methuselah said:**
> Setting encryption password is not really a linux specific thing.
Is your network set to WPA or WEP and have you given network manager the correct password to connect.
Nontheless, since it is working sometimes it is unlikely that this is the issue.

The fact is that some wireless cards are not well supported in linux because the drivers are not in a great state.
In some cases, the people who make the hardware do not provide drivers and the reverse-engineered drivers (if they exist) might not be fully mature.

I understand that this laptop uses a broadcom wireless chip which is among the less well supported.
[http://hea-www.harvard.edu/~dsteeghs/dell_d600.html](http://hea-www.harvard.edu/~dsteeghs/dell_d600.html)
The best you can do is forget about it or try to get it working by using the windows drivers and ndiswrapper.
The same link above seems to be saying that the chip works well with ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by cariboo on 2010-01-20
Can you connect to your router with an ethernet cable, if you can it would probably take less than 10 minutes to solve your problem.

---

### Post by hiloguy on 2010-01-20
> **cariboo907 said:**
> Can you connect to your router with an ethernet cable, if you can it would probably take less than 10 minutes to solve your problem.

Yes!  Everything works just fine when connected to the router.  It actually worked intermittently with the Ubuntu-supplied bcm43xx driver.  It would connect fine for a while, then it would show connected but I couldn't get past the router.

Anyway, I would LOVE to hear the 10-minute fix!

---

### Post by hiloguy on 2010-01-20
> **cariboo907 said:**
> Can you connect to your router with an ethernet cable, if you can it would probably take less than 10 minutes to solve your problem.

I'm still eagerly waiting for the ten-minute fix to this uber-frustrating problem!

Please?

---

### Post by hiloguy on 2010-01-20
> **hiloguy said:**
> Wow!  I was so excited that after only three long days of trying to get my wireless working I found this set of instructions in my book, "Beginning Ubuntu Linux." I did the blacklisting of existing drivers.  It worked.  I extracted the correct .inf file (in XP on on the same computer) and via thumbdrive installed them on the Linux  side of this Dell D620.  I installed it with ndiswrapper and it all worked as planned, right up until I opened the "Windows Drivers" box and there was my driver with a big red X through it and the words, "invalid driver."

This is getting very frustrating.  Why would this driver, which obviously works on this same computer with XP, be an invalid driver in Ubuntu 9.10?

Followup on the above:  The driver, according to XP, is bcmwlr.**sys**.  Ubuntu will only accept .**inf** files as drivers.  Is this the issue here?


I followed the entire procedure to blacklist the original drivers and install the correct new one with ndiswrapper.  It installed just fine, but when I pull it up in "Windows Drivers" it comes up as "invalid driver."  According to the XP side of this laptop, the driver is bcmwl5.sys, but Linux needs the bcmwl5.inf file.  Could this be the issue?

---

### Post by bkratz on 2010-01-20
although I never did find out what wireless card you have (post 11 above), you must have used ndiswrapper on one of the BCM43xx cards. Yes it does have to be the .inf file for ndiswrapper to be valid. Actually you are supposed to have both available, but it only seems to require the .inf file.  If you don't have it here is a link of the source.

[http://www.infdump.com/inffiles/B/bcmwl5.inf](http://www.infdump.com/inffiles/B/bcmwl5.inf)

The 10 minute fix would have been to use the native b43 driver (depending on the card)
Here is the link to this should this be necessary. You would have to remove ndiswrapper to use it though

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by hiloguy on 2010-01-20
> **bkratz said:**
> although I never did find out what wireless card you have (post 11 above), you must have used ndiswrapper on one of the BCM43xx cards. Yes it does have to be the .inf file for ndiswrapper to be valid. Actually you are supposed to have both available, but it only seems to require the .inf file.  If you don't have it here is a link of the source.

[http://www.infdump.com/inffiles/B/bcmwl5.inf](http://www.infdump.com/inffiles/B/bcmwl5.inf)

The 10 minute fix would have been to use the native b43 driver (depending on the card)
Here is the link to this should this be necessary. You would have to remove ndiswrapper to use it though

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

The native b43 driver is the one that I had all the problems with in the first place.  It worked fine as soon as I activated it but after the next time I powered up, it still showed "connected" but would not connect to the internet.  Directly connecting (cable) to the router worked fine.  The only way I could get it to work again was to disable it, reboot, and then re-enable it.  I kept getting other people's feedback about how the native driver had issues and that for this application the Windows driver was the way to go.

What I really want to know is why does the properly-installed Windows driver come up as "invalid?"

---

### Post by bkratz on 2010-01-20
It comes up invalid if it doesn't think it is the correct driver. The sys file would say that, so would some other .inf file, sometimes the Vista version doesn't work while the XP version does, you just have to try.

Here is another one worth looking into

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

---

### Post by PTSWhite on 2010-01-20
> **hiloguy said:**
> More on this:
 
Dell Wireless 1490 Dual Band WLAN Minicard Driver Version 4.10.40.0, along with the location of the file. 
 
I'm an Ubuntu newbie too, anad I had EXACTLY the same problem with a one year old Belkin USB dual band adapter.  I changed to a Netgear PCI card and have had no problems ever since.  In the interim I also found that a D-Link PCI card wasn't even seen by Network Manager, aparently because it uses the dreaded Broadcom 4.3 chipset.
 
Long story short, it might be worth $30 or so try a different wireless card.  I KNOW that before I decided to just try playing Musical Wi-fi Cards, I spent much more than that much worth of my time (at my current rate of pay) dinking around with drivers and ndiswrap, etc.

---

### Post by hiloguy on 2010-01-20
> **PTSWhite said:**
> I'm an Ubuntu newbie too, anad I had EXACTLY the same problem with a one year old Belkin USB dual band adapter.  I changed to a Netgear PCI card and have had no problems ever since.  In the interim I also found that a D-Link PCI card wasn't even seen by Network Manager, aparently because it uses the dreaded Broadcom 4.3 chipset.
 
Long story short, it might be worth $30 or so try a different wireless card.  I KNOW that before I decided to just try playing Musical Wi-fi Cards, I spent much more than that much worth of my time (at my current rate of pay) dinking around with drivers and ndiswrap, etc.

Thanks for the reply!  I'd like to hear some other opinions about changing the wifi card in a Dell D600 laptop.  Seems like there has to be a way to make this work . . .  If changing it is a good way to go, any recommendations?  A Dell D620 is probably the most common notebook out there as just about every IT guy uses them, so there have to be some positive experiences on these.  Don't there?

---

### Post by hiloguy on 2010-01-25
Well, here it is. I want to extend my sincere appreciation to all of you who have helped me through yet another adventure in trying to get Ubuntu to a place on my test laptop where I finally felt confident enough in it to switch over our four computers. Alas, since after two long weeks of entering cryptic terminal entries and trying at least half a dozen entirely different tedious approaches to the seemingly simple end of getting the wifi working, I admit defeat.

I love Linux and especially Ubuntu and was so hoping to be able to pull it off this time. Every app I need to run our two businesses is up and running, but as long as there is no one doable answer to something as basic as getting the wifi working, I just can’t take the chance on it at this time. I will try again, maybe when M/S officially stops supporting XP-Pro, but for the meanwhile, I need an OS that works without my Lovely Bride having to drag me away from yet another eight-hour day of trying, in vain, to get it working.

I tried again because of the several reviews I read that announced 9.10 being pretty much plug-and-play. For most things it is. Maybe after a while somebody will come up with a list of proven drivers that actually work with the most common wifi cards. I’m working with the ubiquitous Dell D-620, and I’m sure Dell has those drivers hidden away somewhere, since they ship new laptops with Ubuntu. Compiling a list of WHAT WORKS shouldn’t be such a big deal for the good folks who are designing the OS. It just seems unfathomable to me that with all the expertise there is on these forums, nobody has taken on that challenge and become the Ubuntu Hero of All Time! A huge percentage of the mystified users who post here are asking the same questions and still there are no finite answers.

Ubuntu is SO CLOSE to being the perfect OS . . .

With much appreciation for all the ongoing effort of the terrific Linux/Ubuntu community, I can only say that I can’t stay away for long, so I’ll be back. I hope when that happens I can get my wifi to work!

Aloha from Hawaii,

Hiloguy
__________________

---

### Post by walt.smith1960 on 2010-01-26
> **hiloguy said:**
> Well, here it is. I want to extend my sincere appreciation to all of you who have helped me through yet another adventure in trying to get Ubuntu to a place on my test laptop where I finally felt confident enough in it to switch over our four computers. Alas, since after two long weeks of entering cryptic terminal entries and trying at least half a dozen entirely different tedious approaches to the seemingly simple end of getting the wifi working, I admit defeat.

I love Linux and especially Ubuntu and was so hoping to be able to pull it off this time. Every app I need to run our two businesses is up and running, but as long as there is no one doable answer to something as basic as getting the wifi working, I just can’t take the chance on it at this time. I will try again, maybe when M/S officially stops supporting XP-Pro, but for the meanwhile, I need an OS that works without my Lovely Bride having to drag me away from yet another eight-hour day of trying, in vain, to get it working.

I tried again because of the several reviews I read that announced 9.10 being pretty much plug-and-play. For most things it is. Maybe after a while somebody will come up with a list of proven drivers that actually work with the most common wifi cards. I’m working with the ubiquitous Dell D-620, and I’m sure Dell has those drivers hidden away somewhere, since they ship new laptops with Ubuntu. Compiling a list of WHAT WORKS shouldn’t be such a big deal for the good folks who are designing the OS. It just seems unfathomable to me that with all the expertise there is on these forums, nobody has taken on that challenge and become the Ubuntu Hero of All Time! A huge percentage of the mystified users who post here are asking the same questions and still there are no finite answers.

Ubuntu is SO CLOSE to being the perfect OS . . .

With much appreciation for all the ongoing effort of the terrific Linux/Ubuntu community, I can only say that I can’t stay away for long, so I’ll be back. I hope when that happens I can get my wifi to work!

Aloha from Hawaii,

Hiloguy
__________________

Hi Hiloguy

I'm sorry to hear about your problems. Here is a WiFi adapter that I have had very good luck with:[http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=42](http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=42)  I've used this on a few different machines and it has always been plug & play. Monoprice.com has WiFi adapters that they claim work with Linux. At least some of the Monoprice adapters use Ralink chips which seem well supported by the Linux Kernel. Broadcom for whatever reason seems to not be well supported.  If a WiFi card is supported natively, it'll work with a LiveCD. You could burn a LiveCD and try any new adapters you buy without having Linux installed in your hard drive.  Another possibility might be to try Linux Mint.  It's based on Debian as is Ubuntu but is said to have better hardware support, and will run as a LiveCD.

---

