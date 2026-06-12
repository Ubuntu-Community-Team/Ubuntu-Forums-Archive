---
title: "Network with Belkin wireless g router?"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by rapattack1 on 2008-08-18
Hi I am totally new to networking and I have this router [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136493](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136493) .
I looked on that site above but I am not sure if I have restored the unit to it's factory settings. There is a reset button next to the power and a friend was trying to help me over the phone. He said I needed to get on the Belkin site but I don't see any relavent info there. I tried first off with communicating to my notebook as i have a pcmcia wifi card in it and I use wlassistant. Usually I use the notebook for wifi hotspots. wlassistant shows that the connection is locked. I hope I am explaining properly and I know I have missed something out. Primarily I will but using the Belkin device for wired connections but I might need the wireless thing occassionally for the notebook. I have two desktops as well.

---

### Post by Sam Lars on 2008-08-18
The reset button should restore everything to factory settings.
What are you trying to accomplish?  Are you trying to take off the wireless security?
Your documentation that came with the router (it really should be on the site you linked to, but it doesn't look very promising) should tell you how to connect to it and configure it.  I'd suggest using a wired connection at least at first.

---

### Post by rapattack1 on 2008-08-19
Yeah my friend there was some kind of timing issue when pressing reset buttons and that i was to find out from googling but I had no luck. I got this router from someone else and need to set it up with my system. I have never networked before. I tried with the wired connections too but no luck there.
Yeah that website doesn't have much info but as I don't know much about these devices I thought someone might see info there that is relavent.

---

### Post by Sam Lars on 2008-08-19
If you reset it, it should "just work."  At least with wired connections.
To configure, connect to it and point your browser to 192.168.1.1, 192.168.0.1, something like that.  It may ask you for a password; try "belkin," or try putting nothing in for it.

---

### Post by rapattack1 on 2008-08-20
Yeah I haven't tried again since the other day. So will look at this again tonight.

---

### Post by Sooner Al on 2008-08-20
Here is the procedure for resetting the router back to the factory defaults...

[http://www.belkin.com/support/article/?lid=en&pid=F5D7230-4&aid=1564&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D7230-4&aid=1564&scid=0)

Use [http://192.168.2.1](http://192.168.2.1) to access the Belkin router once you reset back to factory defaults.

Here are the support pages for that router...

[http://www.belkin.com/support/product/?lid=en&pid=F5D7230-4](http://www.belkin.com/support/product/?lid=en&pid=F5D7230-4)

...including user manuals...

[http://www.belkin.com/support/article/?lid=en&pid=F5D7230-4&aid=5999&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D7230-4&aid=5999&scid=0)

---

### Post by rapattack1 on 2008-08-22
Well the good news is I did get it happening. I don't know how. It seems it is working despite whatever I have done. I did download and read the Belkin info on what to do. It is odd though the set up I saw. I haven't got the modem plugged into the modem socket at the back of the Belkin device. I have it plugged into the first connection for the first computer if you know what I mean. The socket that says 'modem' has one of my pc's connected to it. and socket 2 has another pc connected to it. It this normal? Now I will try and see if I can get my notebook connected via wifi.
Well no luck on getting the wifi happening. I have followed the docs and I am getting no where.

---

### Post by Sooner Al on 2008-08-22
I think you need to start over. The modem (cable or DSL) should be connected to the modem/WAN/internet socket on the Belkin router. Your PCs should be connected to the LAN ports on the router. In all cases use straight through patch cables **NOT** crossover cables.

[http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp](http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp)

Carefully read the instructions in the user manual for your router for help connecting, powering on and configuring. You can use this Quick Start guide to get a basic wired internet connection up with your wired PCs...

[http://www.belkin.com/support/article/?lid=en&pid=F5D7230-4&aid=5028&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D7230-4&aid=5028&scid=0)

Good luck...

---

### Post by rapattack1 on 2008-08-22
I did read that manual and it says to do it like I have done it. I thought it was odd too but there it is. And it works.

I looked at that first link and the 2nd diagram is like mine I guess. I can take a picture actually....how do I tell if I have crossover cables or not. I think both of them are crossovers because when I first got hooked a friend got the cable and he mentioned that that is what he got. I didn't have a network then. I either hooked up one pc to the computer or the other and they have their own separate cables.

Here it is [http://i273.photobucket.com/albums/jj202/rapattack_album/img_0020.jpg](http://i273.photobucket.com/albums/jj202/rapattack_album/img_0020.jpg)

---

### Post by Sam Lars on 2008-08-22
Hey, if it works, that sounds like a very good thing.  I'm not sure that the labels are more than a guide
If you look closely at the ends of the cable, the side without the hook, with the end pointing up, from left to right it should be orange-white, orange, etc. on **both** ends.  A crossover will have green-white, green, etc. on one of the ends.
Some routers can negotiate and work on a crossover cable, but it's of course better to use regular patch cables.
I assume that from your picture the green is your modem and the yellow is a computer?  That looks right to me.

---

### Post by rapattack1 on 2008-08-22
[http://i273.photobucket.com/albums/jj202/rapattack_album/img_0020-1.jpg](http://i273.photobucket.com/albums/jj202/rapattack_album/img_0020-1.jpg)
[http://i273.photobucket.com/albums/jj202/rapattack_album/img_0019.jpg](http://i273.photobucket.com/albums/jj202/rapattack_album/img_0019.jpg)
[http://i273.photobucket.com/albums/jj202/rapattack_album/img_0018.jpg](http://i273.photobucket.com/albums/jj202/rapattack_album/img_0018.jpg)

Hi I am not sure if this what you mean by the colours on the cables?

The green is my primary pc and the yellow is the modem.

---

### Post by Sooner Al on 2008-08-23
> **rapattack1 said:**
> I did read that manual and it says to do it like I have done it. I thought it was odd too but there it is. And it works.

I looked at that first link and the 2nd diagram is like mine I guess. I can take a picture actually....how do I tell if I have crossover cables or not. I think both of them are crossovers because when I first got hooked a friend got the cable and he mentioned that that is what he got. I didn't have a network then. I either hooked up one pc to the computer or the other and they have their own separate cables.


The first link was to illustrate how to check if your using straight through or crossover cables. See the pictures at the bottom of the page.

The second link is for the Belkin quick start guide to help you connect the modem, router and PC(s) **correctly** and the correct power on order.

---

### Post by rapattack1 on 2008-08-23
Um I am unclear what you mean. I did read/download the Belkin manual. I followed what it said and ...............

I don't know what you mean about the 2nd thing either that is why I took pictures of the heads of the cables for confirmation that they are crossover or whatever.

---

### Post by Sam Lars on 2008-08-23
Is everything working like it should?  If it is, then I wouldn't worry about it.
If it isn't, then we do need to try to do something about it.  First, the cables should be plugged into the slots that they're labeled for.

---

### Post by rapattack1 on 2008-08-24
Yes everything is working fine but no the cables are not plugged into where they are supposed to according to the labels. That is the weird thing about it. The manual said to do it the way that this is. I had the cables into where they are labelled to go and it didn't work so then I went to the manual. I though it was weird but I have seen many strange things work so I did it. 
Anyway with this network thing am I also about to share files with the different pc's? I have never worked with a home network especially not Linux. I have seen somewhere it is possible in the system but not sure how to go about it. Thanks!

---

### Post by Sooner Al on 2008-08-24
> **rapattack1 said:**
> Yes everything is working fine but no the cables are not plugged into where they are supposed to according to the labels. That is the weird thing about it. The manual said to do it the way that this is. I had the cables into where they are labelled to go and it didn't work so then I went to the manual. I though it was weird but I have seen many strange things work so I did it. 
Anyway with this network thing am I also about to share files with the different pc's? I have never worked with a home network especially not Linux. I have seen somewhere it is possible in the system but not sure how to go about it. Thanks!

In **no** case does the Belkin F5D7230-4 *Users Manual* or the *Quick Install Guide* say to connect the modem to a LAN Port on the router or the computer(s) to the modem port. *Please* **reread** the documents closely. I also suggest starting over again by doing a hard reset (**return the router to the factory defaults**) of the router per the procedure in the Users Manual. Look in the ***Knowing your router*** section of the manual.

FWIW, I have a F5D7230-4 router here in my home office that I use for a wired/wireless home LAN with two windows machines and an Ubuntu laptop.

...and that is the last I have to say on this subject. ***Good luck***...

---

### Post by rapattack1 on 2008-08-24
Mmmmmm ok well the manual that i read did but I don't know if the link of the one you posted is the same thing. I will have to wait til a bit before I can download another manual as I have run out of internet usage.
I did do a hard reset actually as I wasn't able to do anything without doing that. I think i had to press the reset button for 10 seconds. It wasn't working at all the way I had it hooked up and as I said I thought it was really odd. I don't have the link of where I got the manual from as I have formatted and reinstalled Ubuntu since I got the modem. I should still have the manual though backed up on a cd. Will take a look.

---

### Post by rapattack1 on 2008-08-25
He he you won't believe what happened today. i couldn't get connected to the net. So I changed the cables to where they really should be connected and I am back on. Weird!!! Now I will try again and see if I can get connected wirelessly(with the notebook I have-it has Ubuntu too). The only thing is there are things to enter and it seems a bit more complicated.:)

---

