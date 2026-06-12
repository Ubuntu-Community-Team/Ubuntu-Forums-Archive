---
title: "Ubuntu 11.04 Freezes at login"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by TonyT0819 on 2011-07-16
I have a Toshiba Satellite C655D-S5126:
   
  Processor: AMD E-240 1.5 GHz, 512KB L2 Cache
  Video Card: AMD Radeon HD 6310 with 384MB-1459MB
  Memory: 3GB DDR3
   
  I have recently installed Ubuntu 11.04 as a dual boot with Windows 7 on my hard drive. [COLOR=black]Everything installed successfully and when I rebooted my system into Ubuntu 11.04 everything worked perfectly. I was able to connect to the internet via my wifi connection, set up my e-mail account, signed into all of my instant messaging accounts, and used Firefox to go onto YouTube. I also updated the software and rebooted the system and everything was still working fine. When I shut down the system for the night and turned it on the next morning Ubuntu froze at the login screen and everything is unresponsive. I have not been able to login since then and since I am new to Linux I am not sure what to do to get the system running again. If anyone can help me it would be extremely appreciated. [/COLOR]

---

### Post by bennyroger on 2011-07-16
At the Grub menu at startup, try to choose an older kernel if available or choose safe boot if available in your grub. Could be an update that went wrong.

---

### Post by Jamsers on 2011-07-16
Hey TonyT0819, I had the same problem as you recently. My solution was to  enable network boot in the BIOS, then put the network on top of the  hard drive in the boot sequence (meaning, make the BIOS try to boot from  the network first before making it try to boot from the hard drive).  I'm sorry if I can't be any clearer, I'm not that good with computers,  and I'm not sure if my BIOS and your BIOS are the same. But I do hope  this helps.

---

### Post by amjjawad on 2011-07-16
> **TonyT0819 said:**
> I have a Toshiba Satellite C655D-S5126:
   
  Processor: AMD E-240 1.5 GHz, 512KB L2 Cache
  Video Card: AMD Radeon HD 6310 with 384MB-1459MB
  Memory: 3GB DDR3
   
  I have recently installed Ubuntu 11.04 as a dual boot with Windows 7 on my hard drive. [COLOR=black]Everything installed successfully and when I rebooted my system into Ubuntu 11.04 everything worked perfectly. I was able to connect to the internet via my wifi connection, set up my e-mail account, signed into all of my instant messaging accounts, and used Firefox to go onto YouTube. I also updated the software and rebooted the system and everything was still working fine. When I shut down the system for the night and turned it on the next morning Ubuntu froze at the login screen and everything is unresponsive. I have not been able to login since then and since I am new to Linux I am not sure what to do to get the system running again. If anyone can help me it would be extremely appreciated. [/COLOR]

Hello and Welcome :)

Please try some Google Search ([http://www.googlubuntu.com/](http://www.googlubuntu.com/)) and I'm sure you'll find the answer. I could have done that for you but it's better of you do it :)

Good Luck!

---

### Post by TonyT0819 on 2011-07-16
Thanks to all of you for your reply's, I didn't expect for anyone to reply so quickly. I'm going to try everyone of these solutions and let you all know which one worked. Like I said I'm new to Linux, I didn't know that there was a Google Ubuntu, lol. But I'm going to check that out too. And thanks again for the help, I'll reply later on tonight to give you all an update.

---

### Post by amjjawad on 2011-07-16
> **TonyT0819 said:**
> Thanks to all of you for your reply's, I didn't expect for anyone to reply so quickly. I'm going to try everyone of these solutions and let you all know which one worked. Like I said I'm new to Linux, I didn't know that there was a Google Ubuntu, lol. But I'm going to check that out too. And thanks again for the help, I'll reply later on tonight to give you all an update.

Waiting for your feedback ;)

We are all here learning so don't worry about anything :)

---

### Post by TonyT0819 on 2011-07-17
Sorry it took me so long to respond but I have been looking into this issue online and what i have found out is that Ubuntu 11.04 works perfectly when I start my laptop with the Ethernet cable plugged in. If I keep the Ethernet cable plugged in for a couple of minutes after logging in, it still continues to work and I can continue to use the internet with my wifi connection but if I unplug it too soon it freezes. I'm not sure what to do beyond this point to get it to work without the Ethernet cable plugged in. I want to try Jamsers solution but I'm not sure what to select in BIOS to make the network boot first. My BIOS screen doesn't make it clear which selection is for the network. I recognize the hard drive, CD Rom, USB, but there are a few other selections that I do not. But if there is any other solutions they are welcomed too. I really like Ubuntu 11.04 and want to continue using it.

---

### Post by amjjawad on 2011-07-17
> **TonyT0819 said:**
> Sorry it took me so long to respond but I have been looking into this issue online and what i have found out is that Ubuntu 11.04 works perfectly when I start my laptop with the Ethernet cable plugged in. If I keep the Ethernet cable plugged in for a couple of minutes after logging in, it still continues to work and I can continue to use the internet with my wifi connection but if I unplug it too soon it freezes. I'm not sure what to do beyond this point to get it to work without the Ethernet cable plugged in. I want to try Jamsers solution but I'm not sure what to select in BIOS to make the network boot first. My BIOS screen doesn't make it clear which selection is for the network. I recognize the hard drive, CD Rom, USB, but there are a few other selections that I do not. But if there is any other solutions they are welcomed too. I really like Ubuntu 11.04 and want to continue using it.

Perhaps it's downloading some updates when you unplug it?

If you're not using any browser or any application that require a connection to the internet then I see no problem if you unplug the cable. Perhaps the freeze has to do with something else? I'm not sure.

Booting from Network has nothing to do with this IMHO.

[B]Edit:
[/B]Try to unplug your Cable and Login to Ubuntu. See what will happen?!

---

### Post by TonyT0819 on 2011-07-17
When I first was able to log into Ubuntu 11.04 with the Ethernet plugged in, I let it update without taking the cable out. Then after that I rebooted the computer with the it still plugged in and after a while I took the Ethernet cable out and it continued to work. After that I rebooted without the Ethernet cable plugged in and it froze at login again. Then I rebooted the computer with the Ethernet cable plugged in and it booted fine but after I logged in and the desktop was loaded I took it out and it froze again. The last time I rebooted it, I rebooted it with the Ethernet cable plugged in and left it in for a while until I unplugged it and it is still working fine, but if i were to restart it without the Ethernet cable plugged in, it will freeze.

---

### Post by amjjawad on 2011-07-17
> **TonyT0819 said:**
> When I first was able to log into Ubuntu 11.04 with the Ethernet plugged in, I let it update without taking the cable out. Then after that I rebooted the computer with the it still plugged in and after a while I took the Ethernet cable out and it continued to work. After that I rebooted without the Ethernet cable plugged in and it froze at login again. Then I rebooted the computer with the Ethernet cable plugged in and it booted fine but after I logged in and the desktop was loaded I took it out and it froze again. The last time I rebooted it, I rebooted it with the Ethernet cable plugged in and left it in for a while until I unplugged it and it is still working fine, but if i were to restart it without the Ethernet cable plugged in, it will freeze.

Your post is really confusing ;)

What I meant is: Turn your machine ON without plugging in your LAN Cable. Keep using it without the cable until you shut it down. Will the same issue occur?

Honestly, I have never tried Ubuntu without Internet Access. My PC was always connected.

---

### Post by TonyT0819 on 2011-07-17
Sorry about the confusing post. I've rebooted the computer without the Ethernet cable being plugged in and it freezes.

---

### Post by amjjawad on 2011-07-17
> **TonyT0819 said:**
> Sorry about the confusing post. I've rebooted the computer without the Ethernet cable being plugged in and it freezes.

I'm trying to search here [http://www.googlubuntu.com/](http://www.googlubuntu.com/) to see if I can find something related to your case.

Try to use that link and search too ;)

---

### Post by TonyT0819 on 2011-07-17
Thank you for your help, I'm looking too.

---

### Post by TonyT0819 on 2011-07-17
I have been looking around on the Internet and can see that a lot of other people are having the same issue with Ubuntu as me, but from what I can see no one has been able to fix it. If anyone can help it would be greatly appreciated.

---

### Post by Jamsers on 2011-07-20
Hey man, try this:

> **dino99 said:**
> googling a little around and found lot of users having troubles with wifi:

[https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Baspire%2B522&ie=utf-8&oe=utf-8]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Baspire%2B522&ie=utf-8&oe=utf-8")

and a possible solution:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034)

look post "3 to blacklist the module :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034/comments/3](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034/comments/3)

sudo gedit /etc/modprobe.d/blacklist.conf


but first you need to be able to boot:
- at bios end process, hold "shift" key down to get the grub menu
- choose "recovery" mode (second line choice)
- choose "network" to get a command line prompt
then run the command line above to blacklist the module, save and reboot  to see if it makes a difference, otherwise you should continue in  recovery mode and you should install the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")
in that order:
- install linux-headers...all.deb
- install linux-headers...i386.deb (as your install might be a 32 bits one, otherwise choose the amd64 one)
- then install the related linux-image package

---

### Post by amjjawad on 2011-07-20
> **TonyT0819 said:**
> I have been looking around on the Internet and can see that a lot of other people are having the same issue with Ubuntu as me, but from what I can see no one has been able to fix it. If anyone can help it would be greatly appreciated.

Although I did not hear back from you, I'm just trying to do my best to solve a similar issue of yours.

[http://ubuntuforums.org/showthread.php?t=1805746](http://ubuntuforums.org/showthread.php?t=1805746)

Have a look and follow the same steps here. Even if you think you case is different, there is no harm to have a look.

Should you have any question? please post back in your thread (this one) and I'll get back to you. I prefer NOT to post on this ([http://ubuntuforums.org/showthread.php?t=1805746](http://ubuntuforums.org/showthread.php?t=1805746)) because that will confuse the other OP and everyone else.

Waiting to hear back from you!

---

### Post by TonyT0819 on 2011-07-23
Sorry I've been pretty busy recently with school, I just wanted to let you all know that I am going to check out those links right now. Thanks for all of your help and I will be posting an update to let you know if any of them helped.

---

### Post by TonyT0819 on 2011-07-23
[amjjawad]("http://ubuntuforums.org/member.php?u=941822"):

I was reading through your post and saw that you had someone else with the same problem disable their wireless connection. I tried the same thing and that worked for me. 

Before I turn off my computer I disable the wireless connection and when I reboot the computer starts without freezing. After Ubuntu is running I enable my wireless connection and it works without any problems. 

Thank again for all of your help, hopefully later there is another update that will completely fix this issue, but for now this is better and more manageable than having to connect the Ethernet cable.

---

### Post by amjjawad on 2011-07-23
Glad to know it worked for you and I'll be waiting for your update :)


> **TonyT0819 said:**
> Before I turn off my computer I disable the wireless connection and when  I reboot the computer starts without freezing. 
It started without Freezing BUT was your LAN Cable plugged in???

> After Ubuntu is running I  enable my wireless connection and it works without any problems. 

Again, was your LAN Cable plugged in?
IF YES, is there any good reason why you're connected to both LAN and Wireless connection at the same time?

Honestly, it shouldn't be a problem as long as each connection has its own IP.
I have a Toshiba Labtop here and it has Linux Mint 11 and Windows 7. It is connected to both Wireless and Wired connection and it works without any issue.


> hopefully later there is another  update that will completely fix this issue, but for now this is better  and more manageable than having to connect the Ethernet cable.
But I thought your issue is fixed? anyway, I'll wait your answer about the above questions :)

By the way, have you logged in to Unity Session? or Classic? or Classic with no effect?

You can see the other guy got it worked only if he logs in to Classic with no effect session. I posted that thread on my previous post. What about you?

---

### Post by TonyT0819 on 2011-07-23
I'm assuming that I am in the Unity Session right now but I don't know how to log into the classic session. 

There was no Ethernet plugged in when I turned on my computer yesterday and it didn't freeze. I had just disabled the wifi settings before I turned the computer off. And when I booted it up last night it worked without freezing. Once everything was loaded up I turned my wifi connection on and everything still worked. 

But I just turned it on this morning with the wifi turned off and it froze at the Ubuntu screen. Then after that I turned off the computer and turned it on again and it booted up to the desktop and I waited a couple of minutes before enabling the wifi connection, but it froze as soon as I enabled it. 

In conclusion, Ubuntu still freezes.

---

### Post by amjjawad on 2011-07-23
> **TonyT0819 said:**
> I'm assuming that I am in the Unity Session right now but I don't know how to log into the classic session. 

There was no Ethernet plugged in when I turned on my computer yesterday and it didn't freeze. I had just disabled the wifi settings before I turned the computer off. And when I booted it up last night it worked without freezing. Once everything was loaded up I turned my wifi connection on and everything still worked. 

But I just turned it on this morning with the wifi turned off and it froze at the Ubuntu screen. Then after that I turned off the computer and turned it on again and it booted up to the desktop and I waited a couple of minutes before enabling the wifi connection, but it froze as soon as I enabled it. 

In conclusion, Ubuntu still freezes.

My friend, don't get me wrong please but you're confusing me big time :D
I'll do my best to read your post again and again but what I want you to do is simply:

Explain in steps OR answer each Q on its own.

When you turn your machine on, you see the login screen where it asks you for your username and password? on the bottom of that screen, there is a bar and there is a list of the session you can login. 
From there, you can choose which session to login.

The other user in that thread I posted for you, he has no problem when he logs in to another session rather than Unity.

Me and my other friends can't really figure it out yet. Is it a Unity issue that is causing all this? is it a Network issue that is causing this? We don't really know.

I'd appreciate if you go through that thread and try all the suggestions over there one by one and post back the result in your thread (this one).

Remember, it's too early to give up just in case you're thinking about that :)

---

### Post by TonyT0819 on 2011-07-24
I'm going to try to log into the Classic Session after I send this message. Last night I tried to reply to your private message that you sent me but it says that you do not accept private messages. If you like we can use Google Talk instant messenger and that would work out fine. Just send me your screen name in a private message and I will add you. Thanks again for your help.

---

### Post by amjjawad on 2011-07-24
> **TonyT0819 said:**
> I'm going to try to log into the Classic Session after I send this message. Last night I tried to reply to your private message that you sent me but it says that you do not accept private messages. If you like we can use Google Talk instant messenger and that would work out fine. Just send me your screen name in a private message and I will add you. Thanks again for your help.

Same happened with me when I tried to send you one but there is an option (scroll down) which will enable you to send even if we don't accept.

Looks like I need to reduce my privacy settings ;)

I sent you a friend request, please accept it :)

---

### Post by anewguy on 2011-07-25
If you see the latest posts in the old thread, you'll find they (supposedly) deleted newer kernels and it works fine straight into Unity.

---

### Post by Sleepy-zz-John on 2011-08-24
I'm also struggling with what looks like this same freezup at log-in problem on my newly purchased netbook, an Acer Aspire One 522,  and I'm also on Natty.

I get the same trouble regardless of whether I'm on Unity or Classic,   but what I've found is that mine seems to be temperature related.   If I try to boot up from cold,  my system invariably crashes at the log-in stage,  and the only way I can boot my Natty is to dual boot into Windows and work there for several minutes first while my system warms up.  I then press restart in Windows,  choose Natty at the reboot grub stage,  and because my system is warmed up,  I'm able to log-in reliably without the freeze occurring.   Also, from within Natty,  if I press restart and then boot back via grub into Natty again,  once again because my system is already warmed up,  I'm able to log-in reliably without freezup.   It's just like trying to start a car in the middle of winter;   starts easily when warm!!  :lolflag:

Before I installed Windows on my netbook as a dual boot, I had it set up dual booting Linpus Linux with Natty,  and I was equally able to overcome my Natty log-in freezups by going into Linpus Linux and playing around there for a few minutes before trying to log-in again on Natty.    

I don't want to hijack this thread with a different case and different symptoms,   but if the OP or anyone else is still struggling with log-in freezes,  it might be worth trying my warm-up method and see if that works.

---

### Post by uglylaughingman on 2011-08-25
> **amjjawad said:**
> 
Booting from Network has nothing to do with this IMHO.


Oddly enough, I have both the same model of Toshiba (Satellite c655d-s5126, identical configuration to the OP), and was having exactly the same issue, if somewhat worse- Ubuntu 11.04 x64 failed to boot at all (even to install)unless a wired Ethernet connection was present. I connected it to my router and booted up just to see what would happen, and was then able to install and run normally- at least up until I disconnected the cable, at which point it froze. 

Rebooting, it worked sporadically, but would frequently freeze, particularly if I tried to do anything affecting the network (e.g., connect to a wireless network, bring up network properties, etc.). 

Since I was frustrated enough as is and nothing else seemed to work, I decided to try the oddball fix mentioned previously i.e., move the LAN boot up to the top in priority (I am running version 1.60 at the moment, and this is done by going to the boot tab, Highlighting LAN and moving it to the top of the list using F6). Once this was saved and the machine rebooted, it worked fine. I tested it for quite some time and had no issues whatsoever, including connecting to wireless networks, etc.

Weird, yes, but true- whatever is going on with this (I suspect a bios issue, or a delayed initialization of either the LAN or wireless adapter), it is easily fixable with this (admittedly odd)workaround, and it very definitely is connected to the priority given to the LAN boot in Bios.
 
The only drawback seems to be a slightly slowed boot as the laptop searches for a PXE server, which seems a small price to pay to have Ubuntu on this.

---

### Post by amjjawad on 2011-08-27
> **Sleepy-zz-John said:**
> I don't want to hijack this thread with a different case and different symptoms,   but if the OP or anyone else is still struggling with log-in freezes, ** it might be worth trying my warm-up method and see if that works**.

ONLY if the user is living in The North/South Pole :D

IMHO, I think it's irrelevent but thanks for sharing your experience with us ;)

---

### Post by amjjawad on 2011-08-27
> **uglylaughingman said:**
> Oddly enough, I have both the same model of Toshiba (Satellite c655d-s5126, identical configuration to the OP), and was having exactly the same issue, if somewhat worse- Ubuntu 11.04 x64 failed to boot at all (even to install)unless a wired Ethernet connection was present. I connected it to my router and booted up just to see what would happen, and was then able to install and run normally- at least up until I disconnected the cable, at which point it froze. 

Rebooting, it worked sporadically, but would frequently freeze, particularly if I tried to do anything affecting the network (e.g., connect to a wireless network, bring up network properties, etc.). 

Since I was frustrated enough as is and nothing else seemed to work, I decided to try the oddball fix mentioned previously i.e., move the LAN boot up to the top in priority (I am running version 1.60 at the moment, and this is done by going to the boot tab, Highlighting LAN and moving it to the top of the list using F6). Once this was saved and the machine rebooted, it worked fine. I tested it for quite some time and had no issues whatsoever, including connecting to wireless networks, etc.

Weird, yes, but true- whatever is going on with this (I suspect a bios issue, or a delayed initialization of either the LAN or wireless adapter), it is easily fixable with this (admittedly odd)workaround, and it very definitely is connected to the priority given to the LAN boot in Bios.
 
The only drawback seems to be a slightly slowed boot as the laptop searches for a PXE server, which seems a small price to pay to have Ubuntu on this.

Had to go through the whole thread again because it's a one month thread or so. I'm not sure if the OP has already tried it or not?

I clearly posted that "Booting the machine with Network set to be the first device" has nothing to do with the issue because every time I install Ubuntu 11.04, I don't face that issue UNLESS of course it has something to do with a particular machine and my machine is an exception. 
I installed Ubuntu 11.04 on two different PCs, each P4 but with different MB (Mother Board) and LAN Cards, etc. Didn't have that issue at all.

@OP:
Please, could you confirm whether you can boot normally if your LAN is set to be the first? just for everyone's information.

Thank you!

---

### Post by Sleepy-zz-John on 2011-08-27
> **amjjawad said:**
> *ONLY if the user is living in The North/South Pole :D*
LOL. No, this particular user is hardly in the polar regions.   Tropics,  actually!
> [i]
IMHO, I think it's irrelevent but thanks for sharing your experience with us ;)[/i]
My pleasure,  but it wasn't irrelevant in my case because it definitely worked and until I moved LAN to the top of my boot order, it was actually the only way I could open Natty on my Acer Aspire One netbook at all.   Of course changing boot order is a much better workaround,  but I think owners of this netbook should keep it in the back of their minds that under some circumstances,  a residual benefit can accrue from booting immediately after a previous session, compared to cold.  Can't guess whether it's truly a temperature effect or perhaps caused by some residual electrical charge in the hardware,  but still worth remembering as a possible means of getting out of trouble.

---

### Post by ffmurray on 2011-09-05
I have the same problem with my acer 5250, in unity classic and safe mode with or without networking.  I need the ethernet plugged in even if its not connected to a network.  i tried the stuff i found in the links but nothing has worked for me so far, and no matter how long my systems been running i still cant unplug the cable without freezing.

---

### Post by TonyT0819 on 2011-10-31
Since the new release of Ubuntu 11.10 I had been looking online to see if other people were having the same issue as I had with Ubuntu 11.04 and other distros in regards to freezing at the login screen. And I had read three post of people having the same issue, but one of them had the same laptop series as mine (Toshiba Satellite C655D) and solved the issue by disabling his LAN in BIOS. So I decided to give it a try with Ubuntu 11.10 and it worked!!! I have rebooted and shut down my laptop about 6 or 7 times and it has not had a freeze at all. I'm thinking that the Ethernet adapter and the WiFi adapter may have been conflicting with one another at startup. Its weird because the only way that I could get it to startup before without it freezing was by connecting the Ethernet cable into my laptop. But I hope that this helps anyone who was having the same problem as me.

---

### Post by amjjawad on 2011-10-31
Finally? WOW, great to know that :D
Well, in computer world, lots of things may surprise you and I know it happens all the time so I won't be surprised.

Thanks for updating us and good luck with your installation :)

---

### Post by shemdroid on 2012-02-28
> **TonyT0819 said:**
> Since the new release of Ubuntu 11.10 I had been looking online to see if other people were having the same issue as I had with Ubuntu 11.04 and other distros in regards to freezing at the login screen. And I had read three post of people having the same issue, but one of them had the same laptop series as mine (Toshiba Satellite C655D) and solved the issue by disabling his LAN in BIOS. So I decided to give it a try with Ubuntu 11.10 and it worked!!! I have rebooted and shut down my laptop about 6 or 7 times and it has not had a freeze at all. I'm thinking that the Ethernet adapter and the WiFi adapter may have been conflicting with one another at startup. Its weird because the only way that I could get it to startup before without it freezing was by connecting the Ethernet cable into my laptop. But I hope that this helps anyone who was having the same problem as me.

see, i have the c655d-s5130 duelboot win7 ubuntu 11.10 and my bios for some reason doesnt have lan as an option for boot order. rathe i have to f12 and pick lan as my first boot device everytime i boot linux.
i had all the same problems as previously mentioned in this thread. no issues now.  Gettin linux to run properly on this particular computer was a nightmare. lol

---

