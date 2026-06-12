---
title: "Ubuntu 10.04.1 Desktop I386 Install: Now what?"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by crustyasp on 2010-09-19
I'm a total noob and just installed Ubuntu, on the laptop listed below. I have to install Scanmodem as I am on dial up, my problem is that I can not find  a way to install gunzip, and I am for some reason unable to do much with Ubuntu other than to login, click on the various buttons  on the desktop and don"t know how to access any of the pre installed programs or make them operational.
 Can someone please tell me what I am doing wrong?:confused:
The laptop has only Ubuntu installed as XP had totally crashed and the recovery disk when I got the computer was corrupt and couldn't do anything.

---

### Post by garvinrick4 on 2010-09-19
> **crustyasp said:**
> I'm a total noob and just installed Ubuntu, on the laptop listed below. I have to install Scanmodem as I am on dial up, my problem is that I can not find  a way to install gunzip, and I am for some reason unable to do much with Ubuntu other than to login, click on the various buttons  on the desktop and don"t know how to access any of the pre installed programs or make them operational.
 Can someone please tell me what I am doing wrong?:confused:
The laptop has only Ubuntu installed as XP had totally crashed and the recovery disk when I got the computer was corrupt and couldn't do anything. If you need to install a .zip file. Right click on .zip file and go to extract here. Will put a folder usually that says install open the folder (directory in linux) and should be a install icon. Click it and let it install.

---

### Post by crustyasp on 2010-09-19
I put scanmodem in cd drive, I get UDF volume on desktop, right click icon, takes me to UDF Volume file browser, shows folder scanModem.gz, right click folder takes me to Extract window, UDF volume highlighted, deselect re-create folders and overwrite existing files, select Extract all files, receive message that I do not have the right permissions to extract archives in the folder. I do not know how to achieve the permissions. Thanks.

---

### Post by garvinrick4 on 2010-09-19
[LEFT]**LINUX - **Agere  does not make a Linux driver available to the public. Agere has made a  Linux driver for some Linux distribution packages - the biggest problem  appears to be the [Free Software Foundation]("http://gnu.org/")  (FSF): a softmodem driver needs to contain proprietary code that would  be in hardware (firmware) for a hardware modem. The FSF's license (GPL)  requires anyone using any part of Linux code to make all derivative  works available for free - Agere is concerned that making a Linux driver  available without making the source freely available might result in  FSF suing Agere. ([FSF has sued a number of companies over such issues]("http://www.gnu.org/philosophy/enforcing-gpl.html").)
However, Olive Essert from Belgium sends feedback to Modemsite indicating that the Linux driver from [Smartlink's]("http://www.smlink.com/")  website (slmodem-2.9.9.tar.gz) works with the Lucent/Agere Scorpio  modem that came in a Toshiba notebook. This is possible because the *hardware*  in both Agere's AMR modem and Smartlink's - the silicon DAA - are the  same component. (As the softmodem name implies, all modem functions  except the physical interface to the computer and phone line are  performed outside the modem itself by software running on the PC). And,  Gennaro from Italy reports success using the Smartlink Linux driver on  Linux Slackware 10.0 (2.4.26) on an Acer Travelmate 740.[/LEFT]

---

### Post by garvinrick4 on 2010-09-19
Hopefully someone else will come up with better news for you. What exactly does your
Cd say? Here is a site:
[http://www.ncbi.nlm.nih.gov/Ftp/uncompress.html#gz](http://www.ncbi.nlm.nih.gov/Ftp/uncompress.html#gz)

---

### Post by crustyasp on 2010-09-20
[QUOTE=garvinrick4;9866266][LEFT]**LINUX - **Agere  does not make a Linux driver available to the public. Quote]

I realize that Agere does not make drivers and I know that US Robotics makes Linux compliant modems. 
Questions:
1. The only Linux modem I can find in my area is a USB drive one with what appears to be the modem  within the stick. Will this work  with Ubuntu?
2. How do I get past the pretty pink desktop? I have managed to set up a password, and play a game of solitaire and that is all.I am the only user but everything I try to access either tells me that I do  not have the right permissions or does nothing? What am I doing wrong?

---

### Post by mikewhatever on 2010-09-20
> **crustyasp said:**
> 
Questions:
1. The only Linux modem I can find in my area is a USB drive one with what appears to be the modem  within the stick. Will this work  with Ubuntu?

There is no way of knowing that, unless you provide some particulars.

> 2. How do I get past the pretty pink desktop? I have managed to set up a password, and play a game of solitaire and that is all.I am the only user but everything I try to access either tells me that I do  not have the right permissions or does nothing? What am I doing wrong?

What exactly are you trying to access? Preinstalled programs should be available in the 'Applications' menu.

---

### Post by crustyasp on 2010-09-20
I can access the applications of the distro, Open office, solitaire  and the limited applications available are not much fun, to do over and over again, playing solitaire until I can resove the dial up situation is not my idea of an experience of a Linux Distro.

My idea at the moment is to go pay the $100 bucks for a new XP and be done as in more searching of all Linux disros, the dialup is an issue with all distros, not because they do not try, but because modem makers do not cooperate. The help you get for dialup on all distro forums makes me intellectually inadequate and makes my brain go into freeze mode. Unfortunately I have dialup because that is what I can afford, and hi speed connection for me is about a 45 min. drive. As much as I hate the thought, it looks like windows will have to do. I really hope Linux makes strides to make their distros compatible to all users regardless of their means of connection.:(
Thanks to all who have replied.

---

### Post by Rasa1111 on 2010-09-20
> As much as I hate the thought, it looks like windows will have to do. I really hope Linux makes strides to make their distros compatible to all users regardless of their means of connection.
Thanks to all who have replied.

 I agree, dial-up users should be given an easier time in this regard. 

 I really hated the thought of having to continue using windows also..
and I had dial up, but I forced the few extra bucks out of myself each month so I could get DSL just so i could use Ubuntu. lol

setting up dial up was just not working, no matter what i did..
and i couldnt really afford an external modem and countless more hours trying to get it to work. 

so said screw it, ill just get DSL for 20 bucks a month rather than dial up for 10 bucks a month. 

if I can be totally windows free..
it is worth it to me. lol

sorry that youre having the problem i haad for so long,
and it really was what kept me from using linux/Ubuntu.
freekin dial up. 

 no matter what dial up tools i would install/use..
i could not connect. :(

really does suck, i feel your pain mate.

---

### Post by crustyasp on 2010-09-20
Where do you get dialup for 10 bucks a month , {I wish}, I have 3 options dialup, a USB stick with limited download and it only is a sometime connection, and very expensive if you go over the limit, or satellite which is just ridiculously priced.

So I guess for now it is back to windows.:(

---

### Post by Rasa1111 on 2010-09-20
> **crustyasp said:**
> Where do you get dialup for 10 bucks a month , {I wish}, I have 3 options dialup, a USB stick with limited download and it only is a sometime connection, and very expensive if you go over the limit, or satellite which is just ridiculously priced.

So I guess for now it is back to windows.:(

It was through netzero. 
I think the bill actually came closer to 12-13 bucks a month. 

I believe Verizon also does DSL for like 20$ a month .

---

### Post by Dustin2128 on 2010-09-20
> **Rasa1111 said:**
> 
I believe Verizon also does DSL for like 20$ a month .
That is your average price for DSL in the states. 
You really should go for broadband, dialup support's always been fairly bad on linux and nobody's likely to improve it soon because so few linux users now use it. The first transition week though, the shift in speeds... totally mind-blowing.

---

### Post by crustyasp on 2010-09-20
I have been surfing and found this page at [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)
I do not really understand the meaning OF the page but apparently it has something to do with making an Agere modem compatible with linux?? 
Anyone able to tell me if anything in there would be helpful to me?

---

### Post by jtarin on 2010-09-20
> **crustyasp said:**
> I can access the applications of the distro, Open office, solitaire  and the limited applications available are not much fun, to do over and over again, playing solitaire until I can resove the dial up situation is not my idea of an experience of a Linux Distro.

My idea at the moment is to go pay the $100 bucks for a new XP and be done as in more searching of all Linux disros, the dialup is an issue with all distros, not because they do not try, but because modem makers do not cooperate. The help you get for dialup on all distro forums makes me intellectually inadequate and makes my brain go into freeze mode. Unfortunately I have dialup because that is what I can afford, and hi speed connection for me is about a 45 min. drive. As much as I hate the thought, it looks like windows will have to do. I really hope Linux makes strides to make their distros compatible to all users regardless of their means of connection.:(
Thanks to all who have replied.External modems for dial-up have always been the best way to go with dial-up and Linux. I still have a Zoom modem over 13 yrs old that will still work under any operating system. It has been the best solution to the problem your addressing and is a much better modem than any internal. Not for everyone I guess.

---

### Post by crustyasp on 2010-09-20
> **jtarin said:**
> External modems for dial-up have always been the best way to go with dial-up and Linux. I still have a Zoom modem over 13 yrs old that will still work under any operating system. It has been the best solution to the problem your addressing and is a much better modem than any internal. Not for everyone I guess.

Yes, i agree, I have looked locally, for an external hardware modem with no success, The only modem I could find that says compatible with Linux and is a dial up, is a US Robotics USB that seems to have the dial up components in the stick, if I knew for sure that this would work I would get it. But being on a limited budget, I do not want to throw $90 down the drain.

---

### Post by t0p on 2010-09-20
If you can get over the hurdle of finding drivers for your winmodem, there are a couple of programs you'll need to do the dial-up thing - **wvdial** and (if you want a nice GUI instead of doing stuff in terminal) **Gnome-PPP**.

Unfortunately, some time ago the Ubuntu devs, in their infallible wisdom, decided not to include wvdial and Gnome-PPP on the installation CD any more.  You can stil get them, from [packages.ubuntu.com]("http://packages.ubuntu.com/") (just search for "Gnome-PPP" under the relevant version) but that requires internet access.  And that's the thing you're trying to get, right?  Also, installing software in this way might tip you over into dependency hell... and that's one hell you *don't* wanna end up in!

One of those USB stick modems might work for you, depending on modem model and the quality of 3G/HSDPA coverage where you live.  You can often insert the USB modem and it'll just work thanks to the busy beavers who do network-manager. And 3G/HSDPA speeds ain't too shabby. But if you buy a modem that doesn't just work... I think you know the score.

If you really want to continue down the dial-up route, I advise you to: 1.  Get yourself a real, hardware modem rather than a crappy winmodem; and 2.  Get onto the Ubuntu devs and tell them to include wvdial and Gnome-PPP in future releases.  The devs think that no one needs to use dial-up anymore, and they'll continue thinking that unless dial-up users tell them otherwise!

Oh, you could write the drivers for yourself, if you're adept at coding.  That's the beauty of Free software: you're free to screw around with it as much as you like.  But I'm guessing from your previous posts that you're not a programmer.

One more last thing: what do you mean when you say you can't do anything with your Ubuntu-running computer?  Look under Applications and you'll see a whole heap of programs.  What exactly is it that you want to do, apart from play solitaire?

---

### Post by jtarin on 2010-09-20
> **crustyasp said:**
> Yes, i agree, I have looked locally, for an external hardware modem with no success, The only modem I could find that says compatible with Linux and is a dial up, is a US Robotics USB that seems to have the dial up components in the stick, if I knew for sure that this would work I would get it. But being on a limited budget, I do not want to throw $90 down the drain.
[Here's what I would recommend if you have a serial port.]("http://www.zoom.com/products/dial_up_external_serial.html") They also have other options (USB) but I only have experience with the serial port one.

---

### Post by crustyasp on 2010-09-20
> **jtarin said:**
> [Here's what I would recommend if you have a serial port.]("http://www.zoom.com/products/dial_up_external_serial.html") They also have other options (USB) but I only have experience with the serial port one.

Thanks, I went to their home page and now searching for a place to order the Zoom here in Canada. there are three places listed, now to find the best deal. Again thanks a lot for the info, hopefully soon I'll be able to rock on with Ubuntu. This is a roller coaster for my emotions!:guitar:

---

### Post by jtarin on 2010-09-20
Also....ZOOM is or was the only modem guaranteed to be lightning-proof. Like during a thunderstorm when your phone line can transmit lightning-charges. Usually they survive throughsuch things when a US Robotics fails. I remeber their headquarters used to be in Florida which has more lightning than any place in the world.

---

### Post by sandyd on 2010-09-20
> **crustyasp said:**
> Thanks, I went to their home page and now searching for a place to order the Zoom here in Canada. there are three places listed, now to find the best deal. Again thanks a lot for the info, hopefully soon I'll be able to rock on with Ubuntu. This is a roller coaster for my emotions!:guitar:
$25/ mo [http://www.acanac.ca/DSL.html](http://www.acanac.ca/DSL.html) / [http://teksavvy.com/en/res-internet.asp](http://teksavvy.com/en/res-internet.asp)

Thats the cheapest you can get here in canada.
Its unlimited, bandwidth usg.

they also sometimes have promotions, check this forum regularly -> [http://forum.smartcanucks.ca/70522-cheap-internet-provider-19-per-month-acanac-canada/](http://forum.smartcanucks.ca/70522-cheap-internet-provider-19-per-month-acanac-canada/)

I got T1 to the house here in the US, and its still rediculusly expensive (but less expensive and WAY more reliable than comcast)

---

### Post by Rasa1111 on 2010-09-20
Yeah I think you definitely need **gnomePPP **and/or **wvdial**. 

When I still had dial up.. 
I found offline installers for them, downloaded them through windows, 
and then went back into ubuntu and installed them.
but nothing would recognize my internal modem. 
so it was fruitless. lol

that USB modem stick sounds interesting..
kinda steep though.

---

### Post by GregA on 2010-09-21
The "dial-in" answer may just be to get either an external serial modem, or an external USB modem and get a 4 dollar serial-to-usb adapter plug.  You might want to look at the auction sites or tech/sales sites because these modems can often be found for under 20$ on eBay or similar.   Mostly, the setup is automatic for a serial modem, the KPPP application (using Kubuntu) makes it easy.

---

