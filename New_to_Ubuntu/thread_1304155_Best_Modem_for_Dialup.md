---
title: "Best Modem for Dialup?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by frank cox on 2009-10-29
Could someone tell if anyone makes dialup modems that are Ubuntu friendly ?
I bought a driver from linmodems and it won't work. 
The time it takes to learn this stuff is more than most people have.

---

### Post by Zzl1xndd on 2009-10-29
I havn't used one in years but when I did US Robotics always worked the very best

[http://www.usr.com/products/modem/modem-product.asp?sku=USR5637&adv=homepage](http://www.usr.com/products/modem/modem-product.asp?sku=USR5637&adv=homepage)

---

### Post by HereInOz on 2009-10-29
Most of the old external serial modems will work well.  Internal Winmodems are precisely that - Windows modems - and generally are a heartbreaker if you try to get them working.

US Robotics should be fine, although I have found almost any external serial modem will work.

---

### Post by frank cox on 2009-10-29
> **tweakedenigma said:**
> I havn't used one in years but when I did US Robotics always worked the very best

[http://www.usr.com/products/modem/modem-product.asp?sku=USR5637&adv=homepage](http://www.usr.com/products/modem/modem-product.asp?sku=USR5637&adv=homepage)

Thanks, they did have modems compatible with Linux.

---

### Post by frank cox on 2009-10-29
> **HereInOz said:**
> Most of the old external serial modems will work well.  Internal Winmodems are precisely that - Windows modems - and generally are a heartbreaker if you try to get them working.

US Robotics should be fine, although I have found almost any external serial modem will work.

So you mean any USB Modem?

---

### Post by dj-toonz on 2009-10-29
I wouldn't bother with a dial up modem, If you can get a cheap HDSPA 3G modem on Pay as you go, faster speeds then dial up, & the phone line is free aswell & much cheaper then using the phone line to dial out with & they work out of the box with Ubuntu without setting anything up

I get 7.2 MEG from my HDSPA dongle about 700 KBS hell of a lot faster then Dial up 

IMHO

---

### Post by frank cox on 2009-10-29
> **dj-toonz said:**
> I wouldn't bother with a dial up modem, If you can get a cheap HDSPA 3G modem on Pay as you go, faster speeds then dial up, & the phone line is free aswell & much cheaper then using the phone line to dial out with & they work out of the box with Ubuntu without setting anything up

I get 7.2 MEG from my HDSPA dongle about 700 KBS hell of a lot faster then Dial up 

IMHO

I am out in the sticks, is this something I can get anywhere?
I will ask the phone company, I hate dialup but I love the sticks.

Thanks

---

### Post by coolbrook on 2009-10-29
> **dj-toonz said:**
> I wouldn't bother with a dial up modemBroadband modems won't fax over POTS.

---

### Post by ranch hand on 2009-10-29
If you go with dial up, I would make REAL sure that the modem you get is a "hardware" modem and use the usb type.  I have a USR5610c internal and it was a bugger to get working as Ubuntu just does not "like" internals.

"Software" modems are Winmodems and they will not work with out drivers that you need to pay for to get really crappy performance.

Hardware modems do not need drivers as they are self contained.

---

### Post by frank cox on 2009-10-29
> **ranch hand said:**
> If you go with dial up, I would make REAL sure that the modem you get is a "hardware" modem and use the usb type.  I have a USR5610c internal and it was a bugger to get working as Ubuntu just does not "like" internals.

"Software" modems are Winmodems and they will not work with out drivers that you need to pay for to get really crappy performance.

Hardware modems do not need drivers as they are self contained.


I bought a driver for my pastors winmodem from  Linuxent.com and I am having a problem installing it. 
I get to a point where it opens Firefox and ask me to put in the password created in terminal and use root as the login name.
I am a newbie and am not sure what they want. I tried using just the login name on the computer and then the franh@Ubuntu1 as it is in terminal but that did not work. Can anyone tell me what they want?

I am leaning toward the US Robotics USB modem, I can get one on E-bay for about 40.00 .
Tiger direct has a cheap one they say is Linux compatible. 

My problem is I give away a lot of computers I get for free and was hoping that Linus would work better on the older machines and be cheaper . It does work well on Hi-Speed which I have at the office but many of the people I help can;t get it. I will pay what I have to get a good one for the house but I need to find a cheap one to give away if that is possible.

I sure do appreciate the help that Ubuntu users have given me, thanks again.

---

### Post by ranch hand on 2009-10-29
Winmodems do not work well under Win JerryLewis Pro (or whatever they are flogging now).

We bought this box with Vista Home Premium on it and a connexant Winmodem.  It ran, on our remote connection 2.5 to 3.5Kb/sec.  I replaced it with the USR5610c internal and then it ran at 3.2 to 4.3Kb/sec.

Dumped Vista and under Hardy the bugger ran at 3.6 to 4.8Kb/sec (flat lined at 4.4 most of the time).

---

### Post by Irihapeti on 2009-10-29
frank cox, when you activate a Linuxant license, you use your email address plus an activation code that they have emailed to you. Once it's activated, you need to reboot. Nothing else should be necessary.

If that doesn't work, you might be best off asking for help from Linuxant. They have the usual "contact us" link on their website. They are quite helpful, though you might need to wait for a day or three to get a reply.

By the way, my internal modem is a D-link DFM-562IS. I've not needed to use it for a while so my memory is a bit hazy, but I seem to recall getting 4.5+ kB/s off it. That is, when every person in the neighbourhood wasn't hammering the net.

---

### Post by ranch hand on 2009-10-30
Linuxant is a pretty helpful bunch.

---

### Post by frank cox on 2009-10-30
> **Irihapeti said:**
> frank cox, when you activate a Linuxant license, you use your email address plus an activation code that they have emailed to you. Once it's activated, you need to reboot. Nothing else should be necessary.

If that doesn't work, you might be best off asking for help from Linuxant. They have the usual "contact us" link on their website. They are quite helpful, though you might need to wait for a day or three to get a reply.

By the way, my internal modem is a D-link DFM-562IS. I've not needed to use it for a while so my memory is a bit hazy, but I seem to recall getting 4.5+ kB/s off it. That is, when every person in the neighbourhood wasn't hammering the net.

The problem was I could not load the driver in the first place. Finally figured out they wanted the word root as the username so I got past that point but it still said it did not find the modem even though scanmodem did.
Hopefully they will get back to me soon.

I looked up the modem you have , it was not expensive but it only mentioned Windows drivers. Where do you get drivers for ubuntu 9.04 and does the fax feature , answering machine etc work?

Thanks!

---

### Post by Irihapeti on 2009-10-30
> **frank cox said:**
> The problem was I could not load the driver in the first place. Finally figured out they wanted the word root as the username so I got past that point but it still said it did not find the modem even though scanmodem did.
Hopefully they will get back to me soon.

I looked up the modem you have , it was not expensive but it only mentioned Windows drivers. Where do you get drivers for ubuntu 9.04 and does the fax feature , answering machine etc work?

Thanks!

I never had occasion to use the fax feature, nor the answering machine. I have an idea, though, that at least one of them doesn't work under Ubuntu.

The drivers are available on the Linuxant site. You need the hsf version and it has to match the kernel you are using. Therefore, it needs to be upgraded after every kernel upgrade.

A slight diversion, perhaps, but I was playing with a live CD of Puppy Linux 4.3 the other day, and I noticed that it detected the modem straight away. Not having dial up anymore, though, I can't test it.

---

### Post by _duncan_ on 2009-10-30
> **frank cox said:**
> So you mean any USB Modem?

Be careful when buying USB modems. Some are actually winmodems with an external casing. Make sure you are buying a full hardware modem.

---

### Post by Shazaam on 2009-10-30
FYI...
Linuxant (Conexant) distro specific .deb drivers currently support Ubuntu up to Jaunty (2.6.28.15) only. You will have to use their "Generic package with source" versions until they add drivers for Karmic.
The free version tops put at 14.4, to get full speed you will need to send them money.  :(
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)
You could pick up an external serial modem on Ebay for about the same price that Linuxant charges for their drivers.

---

### Post by Irihapeti on 2009-10-30
> **Shazaam said:**
> 
You could pick up an external serial modem on Ebay for about the same price that Linuxant charges for their drivers.

Depending on where you live. In my part of the world, you can't.

In fact, even an adapter cable would cost me more than the license charge.

---

### Post by frank cox on 2009-10-30
> **Irihapeti said:**
> I never had occasion to use the fax feature, nor the answering machine. I have an idea, though, that at least one of them doesn't work under Ubuntu.

The drivers are available on the Linuxant site. You need the hsf version and it has to match the kernel you are using. Therefore, it needs to be upgraded after every kernel upgrade.

A slight diversion, perhaps, but I was playing with a live CD of Puppy Linux 4.3 the other day, and I noticed that it detected the modem straight away. Not having dial up anymore, though, I can't test it.

I downloaded the driver for Ubuntu 9.04 and the modem i have but no dice.

I went ahead and ordered a couple of serial modems off of ebay.  
What is the big difference in using Puppy Linux and Ubuntu?

---

### Post by frank cox on 2009-10-30
> **_duncan_ said:**
> Be careful when buying USB modems. Some are actually winmodems with an external casing. Make sure you are buying a full hardware modem.


Thanks!

I bought a couple of serial modems off e-bay that are supposed to be flashed to 56k, I hope they work.
I am against government getting involved in business but in the case of broadband we are losing a big edge and that may be the only way to solve the problem.

I bought a couple of USR external modems Ububtu and Puppy found them-still have connection issues in Ubuntu.

---

### Post by Irihapeti on 2009-10-30
Puppy Linux is a lightweight distro that manages to cram quite a bit into an ISO file of about 100 MB. I keep it around for use on old machines, as a rescue OS and also for just playing with. It hasn't got the friendly package management of Ubuntu, and I've discovered it's not as good as Ubuntu for supporting languages such as Chinese that use non-Latin characters. One tends to end up doing a lot of compiling (or persuading someone else to do it for one). I enjoy some of that, but I can also understand those who don't. Each to their own, I guess.

---

### Post by Shazaam on 2009-11-05
Minor update for those who are interested...
Linuxant now has a .deb for Karmic kernel 2.6.31.14 generic.

---

### Post by frank cox on 2009-12-18
I finally gave up on the winmodems and hooked a usb to rs232 adapter and had no real difficulty setting up the USR Sportster external serial modem.

---

### Post by Extract_Here on 2009-12-18
flashback to the 90s

---

### Post by Extract_Here on 2009-12-18
ill go with the flow on this one and say us robotics

---

### Post by Silvertones on 2010-01-08
I've been trying to get this going for a week now with no luck.

   [IMG]http://www.usr.com/images/pixel.gif[/IMG]    [IMG]http://www.usr.com/images/pixel.gif[/IMG]                
**USR5637 56K USB Faxmodem**

---

### Post by Tom25624 on 2010-01-14
Frank: I here you frustration, I ended up with this Dell Mini with Ubuntu 8.04.1 installed. (A month later) To keep a long story short USRobotics Model 5686E External Modem, however it comes with a 25 pin to 9 pin Serial adapter so I had to buy a 25 pin to USB to get it to work.
 The connection speed is good, but I haven't figured how to tell what it is yet.
 Good luck and welcome back to the world of DOS

---

### Post by Bartender on 2010-01-15
I'm on a mission.

I want to buy a US Robotics 5610 internal hardware modem and see if I can get it to work.  It's a hardware modem, but there's still some kind of problem.  Reading some ancient posts, it appears that the modem wants to install itself to COM 5, which apparently causes trouble.

If anyone has some clear, step-by-step directions for the 5610's please post or PM me.

Thanks!

---

### Post by frank cox on 2010-07-17
> **Silvertones said:**
> I've been trying to get this going for a week now with no luck.

   [IMG]http://www.usr.com/images/pixel.gif[/IMG]    [IMG]http://www.usr.com/images/pixel.gif[/IMG]                
**USR5637 56K USB Faxmodem**

I am trying to help a fellow get his 5637 working, I assume you have yors working after all this time. With my serial modem the main problem was I needed to remove the Gnome-Network Manager and run the setserial script.
Would appreciate the info if you had success.

email me if you don't mind,TIA

---

### Post by lkraemer on 2010-07-17
Silvertones & Frank,
Here is a guide that should help.  It's for a SM56 but USR 5637
should be no problem.  Serial or USB to Serial and it just works.
 
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Posting #4.

PM, or post here if you need specific help.

lkraemer

---

