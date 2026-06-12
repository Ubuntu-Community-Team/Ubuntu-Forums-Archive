---
title: "I killied it. I think I destroyed my computer."
date: 2011-07-17
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-07-17
Well I must have done something to the thing because now I don't seem to even have bios.  

 When I bought this machine I paid $50 for it; and, after the person who sold it to me tore out the door I discovered it was full of cockroaches. Cockroaches! (No kidding! Chock-full of them). So, until recently I hadn't 'thoroughly' cleaned it but the other day I took the whole thing apart (labeled everything - where it came from), cleaned everything up with denatured alcohol and put it back together but adding more stuff from the other units I have sitting around (3 expansion cards, an additional disk and two disc drives). 

 Today, I got to remembering how, when I tried to install Linux on that machine before I had all kind of problems and it would not complete the install (I had tried like 5 different distos at that time). It then sat for months, until now. I also remembered what someone said to me recently regarding those install problems and that he had said they were running across a lot of HP machines where there was some problem between the system clock and the clock in Linux. 

 I got to looking over the specs for my mobo again on HP's site . . . 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604) 

 . . . and I saw that there is instructions at the bottom of that page on clearing cmos using a jumper on the mobo. I put 2 and 2 together (so I thought) and followed the procedure (for both clearing cmos and password - 2 separate jumpers). 

 When I turn the machine on it get no output to the display at all and all it does is the fans run like a bat out of hell. When I try to use the power button to shut down it does not respond. I have had to remove the power cord from the back of the machine to power off.

HP Pavilion a1253w Media Center, or so it started. Everything is stock except for adding a hard drive, replacing the disc drive with two different ones, and replacing the modem card plus two other expansion cards. Here is a link to the system specifications on HP's web site and further system info follows that.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)


System Details: 

 Model: HP Pavilion a1253w Media Center (changes have been made, though that's where it started). 
 CPU: an AMD 64 3400+ (circa 2002? 2005? - part of the original machine) 
 RAM: 2 x 256 MB pc 3200 ddr sdram 400 MHz 184 pin 
 Mobo: an old Amberine board (4 slots for RAM - up to 4 GB but I'll have 2 - 2.5 GB)(onboard sound and graphics) 
 Expansion Slots: ATA (ATA?) and one pcie 
 Drive Types: all ide (2 X disk drives - one WD 80 GB is primary and one Maxtor 100 GB is slave. 2 X disc drives both ide). 
 Other: Because it's an old media center machine it has the 5? in 1 card reader and a thing with a few extra usb ports and other stuff (out the front of the machine). I'd like to keep those. (I'd attach a pic but I'm not seeing how to do that with this bb). To see the "other thing" - http://i.ebayimg.com/10/!CE!mJVQEWk~$(KGrHqF,!lsEz+4J5i0DBNQdftvG!Q~~_35.JPG 

 The expansion cards themselves: 

 1 x Modem = Gateway GVC SF-1156IV/ R9A (Gateway p/n: 6001260) @ [http://pjcomputers.net/gatewaygvcsf-1156ivr9ar6795-11gateway600126056kdatafaxvoicepcimodem.aspx](http://pjcomputers.net/gatewaygvcsf-1156ivr9ar6795-11gateway600126056kdatafaxvoicepcimodem.aspx) 

 1 x Audio card = Ensoniq Audio PCI 9740 (chipset es1370; Assembly NO: 01 rev. e) (can't find a link for details) 

 1 x Wireless NIC = Motorola Wireless PCI Adapter WPC810G (upc: 6 12572 09533 1) @ [http://www.geeks.com/details.asp?invtid=WPC810G](http://www.geeks.com/details.asp?invtid=WPC810G)


If anyone has any ideas I'd love to hear them. I need to be cautions though since this thing is really all I've got for this.

Thanks in advance for any help.


Jake

---

### Post by Mark Phelps on 2011-07-17
You probably won't believe it, but I had exactly the same motherboard in an HP unit -- that just up and "died" one day.

I replaced everything but the CPU, and it would not boot up no matter what I did.

This was a while back (year or more ago) but even then, it was impossible to find a 939 chipset board (I think that's what is was) to replace this one and keep all the parts.

Ended up replacing it with a new AMD board that I got for $50.

---

### Post by wep940 on 2011-07-17
The first thing I would do is remove all the updates you did  and then see if you at least get a screen.  If you don't get a screen then, you may have to make sure you set the jumper back to where it was before you moved it to clear the BIOS.  If so, very carefully follow the instructions once more for clearing your BIOS (though I doubt this will help).  Try booting again.  If it still fails, I believe you may have killed your BIOS.
 
To post a picture to a thread just click on the paper clip icon on the top menu line of the message  box.
 
If  you are able to get it to boot, try adding just 1 thing at a time and rebooting until you find the one that hangs things up.

---

### Post by grahammechanical on 2011-07-17
Did you remember to hold down f12 when you switched on? Just checking. No offence meant. Those instructions do not mention removing the on-board battery before moving the pins. My motherboard user guide says to remove the battery. Perhaps this battery has discharged over so long a time.

Regards.

---

### Post by ClientAlive on 2011-07-17
Sorry for the delay. I'm self employed and have to deal with phone calls whenever they come in. What follows is what I wrote but was trying to take a few pics to attach.

By the way, that cable in the one pic is plugged in. I unplugged it for the pic and then plugged it back in.

I'm gonna try a couple the things that were suggested (to do with the F? key)
------------------------------------------------------


> **wep940 said:**
> The first thing I would do is remove all the updates you did  and then see if you at least get a screen.  If you don't get a screen then, you may have to make sure you set the jumper back to where it was before you moved it to clear the BIOS.  If so, very carefully follow the instructions once more for clearing your BIOS (though I doubt this will help).  Try booting again.  If it still fails, I believe you may have killed your BIOS.
 
To post a picture to a thread just click on the paper clip icon on the top menu line of the message  box.
 
If  you are able to get it to boot, try adding just 1 thing at a time and rebooting until you find the one that hangs things up.


Do you think expansion cards could do something like that?

I should maybe give more details (this may be important).

Both those hared drives are nothing but unallocated space. I had dd'ed them before taking everything apart, cleaning and reassembling the other night. I have run live cd's in it in that state though. Well in a similar state.

There are two hard drives in it. The one that came with the machine is the Maxor 100 GB. When I ran live cd's (Ubuntu 10.04, Knoppix, Live Boot CD, and Parted Magic) it only had that drive in it; and, of course it's jumper was set as Master.

After reassembling the other night I added the WD 80 GB drive but I also switched the order so that the WD drive is set as the master and the Maxtor is set as the slave.

Then there's the three expansion cards. To begin with it had one, stock, modem card. That was removed and replaced with a different one and a wireless NIC and a sound card were added.

In the meantime, since my first post in this thread, I discovered there was one wire coming from the power supply I believe that I had neglected to plug in. It still had it's little masking tape label on it and I plugged it in where it goes. There's only one plug shaped like it on the board so there's no way to mistake that. Powered up again, no change. Have to pull the power cord to get it to shut off.

Well, I shouldn't say "no change" I heard what sounded to me like the hard drive or drives, not 'spinning' down because of the way I have to pull the plug to power off like that - but it sounded like a drive when it's power is cut off. It had been spinning.

So all that and no change.

One thing, I do recall something just like this while working on this machine before. At that time I hadn't realized I didn't have the RAM in the board and powered up. It did the same thing. I inserted the RAM (back then/ that time) and everything worked fine. I've been over and over it and every single plug and jumper and everything (including the rectangular white plug for the mobo's power) is where it should be. I don't really want to wreck something by not powering off safely - over and over.

There is also that there are 4 slots for RAM. Two of those slots are paired next to one another and are colored blue. The other two are next to them, also paired, and are colored black. I wonder if the RAM has to go in the black ones when there is only two sticks? They are in the blue ones now.


> **grahammechanical said:**
> Did you remember to hold down f12 when you switched on? Just checking. No offence meant. Those instructions do not mention removing the on-board battery before moving the pins. My motherboard user guide says to remove the battery. Perhaps this battery has discharged over so long a time.

Regards.

It said F1 on that page at the link (the one with the system specs on HP's site). Is it supposed to be F12 though? They could be wrong. Wouldn't surprise me. I also know I've used the esc key before to enter the boot menu.

I did try pressing F1 just immediately after hitting the power button, but maybe I'm supposed to depress it before touching the power button and then hit the button with the F key depressed?

I thought it mentioned in that link that I'd have to reset some settings in the bios after I cleared things like that. I had been wondering what to expect. This, is what I got.

---

### Post by ClientAlive on 2011-07-17
GLORY GLORY GLORY HALLELUJAH!!!

I don't know why. I just -have-no-idea-at-all . . .  But after it sat and while I was taking those pictures and answering the phone - after all that I plugged the cord back in and it fired right up! It was weird because I never touched the power button. Merely applying juice to it from plugging in the cord and raaaorrr there it went! I'm in the bios setup and the clock is running. Just need to . . . well I need to have a smoke before anything, but then I'll configure the bios and see how well it shuts down using the power button.

I'll let you guys know how it turns out.

Hang on . . .


:D

---

### Post by ClientAlive on 2011-07-17
Well I'm not sure I know how to set a couple of these settings - since the hardware has changed. It's obviously recognizing all the major stuff (both hard drives, both disc drives, the cpu, the onboard audio and video, etc). I'm not sure if I should have "Plug and Play OS" enabled though. Isn't that only for Microsoft? I'll be running Linux. And I need to find and config the expansion card if I can.


My cpu fan was revving for some reason. My first assumption is I washed whatever grease or lube out of it when I cleaned with denatured alc. I had to "save and exit" and shut down for right now. I think, if it is the lack of lube thing, that I don't burn it out. I wonder how I can check the fans and replace any needed lube if it's needed?

I gotta go outside and have a smoke. Back in a few.

Thanks guys.

---

### Post by 1clue on 2011-07-17
I'm really sorry about your bug box, but you need a reality check.

Just to put all this into perspective, a guy at my company just put together a 6-core AMD box with 16G RAM for USD$800.

Keep in mind that when I put my home box together, it cost over $3500.  The box we put together at work was extremely minimal, without a keyboard, mouse or monitor even.  Even so, for the type of benchmark that we were building the thing for it roasts my i7 alive.

It amazes me that people will go through weeks of effort to resurrect something that has less CPU power than the average modern cell phone.

If you're familiar with Linux and hardware and know what's going on, and you're bored and just want to see if you can make it go, then that's one thing.  If you actually expect it to perform a useful task after you get it done then it's an entirely different scenario.

It's actually cheaper to go get new hardware if you consider your time to be worth minimum wage.  That way you're pretty sure your hardware works and the only unknown is the software.

---

### Post by ClientAlive on 2011-07-17
> **1clue said:**
> I'm really sorry about your bug box, but you need a reality check.

Just to put all this into perspective, a guy at my company just put together a 6-core AMD box with 16G RAM for USD$800.

Keep in mind that when I put my home box together, it cost over $3500.  The box we put together at work was extremely minimal, without a keyboard, mouse or monitor even.  Even so, for the type of benchmark that we were building the thing for it roasts my i7 alive.

It amazes me that people will go through weeks of effort to resurrect something that has less CPU power than the average modern cell phone.

If you're familiar with Linux and hardware and know what's going on, and you're bored and just want to see if you can make it go, then that's one thing.  If you actually expect it to perform a useful task after you get it done then it's an entirely different scenario.

It's actually cheaper to go get new hardware if you consider your time to be worth minimum wage.  That way you're pretty sure your hardware works and the only unknown is the software.


Well I just don't have $800 1clue. I wish I did. Except for the base computer, which I paid $50 for almost a year ago, I got all the other stuff free from donations to the cause. It's the best I can do right now. I'm self employed; and, because I'm just getting started (started like a month ago) it's not bringing in the kind of money yet that I hope to see. It is picking up though, slowly but surely. I just got off the phone 20 min ago with another $15/ hr project. I'm sure it won't be long I can have that $800 box (probably even better). I just don't want to sit on my thumb in the mean time. There's still stuff I can do now with what I have. After all, I do it in my spare time.

Thanks for all your help man. I'm really new to all this and am just learning as I go. Sometimes I need the help.

---

### Post by bcschmerker on 2011-07-17
> **ClientAlive said:**
> ...System Details: 

 Model: HP Pavilion a1253w Media Center (changes have been made, though that's where it started). 
 CPU: an AMD 64 3400+ (circa 2002? 2005? - part of the original machine) 
 RAM: 2 x 256 MB pc 3200 ddr sdram 400 MHz 184 pin 
 Mobo: an old Amberine board (4 slots for RAM - up to 4 GB but I'll have 2 - 2.5 GB)(onboard sound and graphics) 
 Expansion Slots: ATA (ATA?) and one pcie 
 Drive Types: all ide (2 X disk drives - one WD 80 GB is primary and one Maxtor 100 GB is slave. 2 X disc drives both ide).... 

 The expansion cards themselves: 

 1 x Modem = Gateway GVC SF-1156IV/ R9A (Gateway p/n: 6001260) @ [http://pjcomputers.net/gatewaygvcsf-1156ivr9ar6795-11gateway600126056kdatafaxvoicepcimodem.aspx](http://pjcomputers.net/gatewaygvcsf-1156ivr9ar6795-11gateway600126056kdatafaxvoicepcimodem.aspx) 

 1 x Audio card = Ensoniq Audio PCI 9740 (chipset es1370; Assembly NO: 01 rev. e) (can't find a link for details) 

 1 x Wireless NIC = Motorola Wireless PCI Adapter WPC810G (upc: 6 12572 09533 1) @ [http://www.geeks.com/details.asp?invtid=WPC810G](http://www.geeks.com/details.asp?invtid=WPC810G)....Being a Socket 939, your system appears to be two generations older than *my* current LinUX box, an Everex® TC2502 upgraded with a Gigabyte® MA78GM-S2HP (AMD® 780G chipset and planar Radeon HD 3200 GPU), Athlon 64 X2 5600+ MPU (Socket AM2, two 2.9 GHzCPU cores), 500W Athena® PSU, and Creative Laboratories® SB0350 PCI audio card. 

From a JPEG in the [POP listing at Epinions.com](http://www.epinions.com/prices/ASUS_A8AE_LE_Motherboard), the Asus® A8AE-LE is a Micro-ATX board with three PCI 1.0 slots (rather than the IBM 5170xxx-compatible, alias ATA, slots used prior to PCI), and an 8x AGP slot (as PCI-Express was in development at your system's time of manufacture).  (My current Windows box is also an Asus® product, three generations younger than the A8AE-LE:  A CM1630-06, which shipped stock with an M4A76-VM-family mobo (AMD® 760G chipset and planar Radeon HD 3000 GPU; one PCI-Express x1, one x16, and two PCI 2.0 expansion slots), Athlon II X2 220 (Socket AM3,two 2.8 GHz CPU cores), and probably a 350W top-fan ATX PSU.)

---

### Post by Swagman on 2011-07-18
Hey for $50.. what's that.. about £30 ish ?

You can't grumble at that although I do know what you mean about resurrecting old hardware. A friend at my works gave me his old comp. It's a Packard Hell p3. I scrubbed the drive and installed Lubuntu on it.

It's still dog slow but as it's only  purpose is a Ch00nZ box to replace the slowly dying k7 in my garage then it doesn't really matter.

I guess I shoulda tried Peppermint on it but I hadn't heard of Peppermint at the time.


Oh.. Why a Ch00nZ box in my garage ?
My garage is setup like a gym.. Treadmill, various weights etc.

---

### Post by wep940 on 2011-07-19
I used to run Ubuntu up until last October on a old MSI motherboard, AMD 64 3200+ and 512mb of memory and it ran fine.  Ignore any of the comments regarding getting something newer, either by purchase or donation.  Some of us know what it's like to not have even $10 to spare, so you do the best with what you've got - exactly as you are trying to do.
 
The reason I mentioned removing the additions and going back to how it used to be, then adding the additions 1 at a time is in that way you can hopefully find at what point you start having problems.  When you get to that point, stop and post back with the steps you did until it failed again.
 
Dave ;)

---

### Post by ClientAlive on 2011-07-19
> **wep940 said:**
> I used to run Ubuntu up until last October on a old MSI motherboard, AMD 64 3200+ and 512mb of memory and it ran fine.  Ignore any of the comments regarding getting something newer, either by purchase or donation.  Some of us know what it's like to not have even $10 to spare, so you do the best with what you've got - exactly as you are trying to do.
 
The reason I mentioned removing the additions and going back to how it used to be, then adding the additions 1 at a time is in that way you can hopefully find at what point you start having problems.  When you get to that point, stop and post back with the steps you did until it failed again.
 
Dave ;)


Thanks Dave. I don't know why I didn't deal with it the other day when I had the setup for bios up but I didn't. I'm a dumbass. I'm not even sure if the date and time in cmos not being set could cause the issue. I'm going to try what your talking about. I let it sit these last couple days and now it's back to the same stuff. Now I've gone and started a different thread about it since I'd marked this as solved before and since it says in a post here that I'd got it worked out. I thought I did but I was wrong.

I have had a few thoughts on what could be gong on though.

1> Maybe it could be trying to draw more juice than that power supply can handle (It's a 250W power supply and now I've got 2 disk drives, 2 disc drives, 2.5 GB of RAM, and 2 expansion cards hooked up).

2> I talked to a guy at a local computer shop and he suggested I do the same thing only in the reverse way of what you said. He said unplug everything but leave the cards in and only have the power to the mobo plugged in, then try it, if it works plug in one more thing, and repeat, etc, etc. The way he explained it is if one thing failed it would take out the whole sytem (kind of like with a closed circuit when you take something out of the circuit it kills the whole thing). That sounds funny to me but I guess he knows more about it than I do.

In any case, I'm gonna try what you mentioned. What else can I do? I'm just worried about damaging a drive by not shutting down properly and doing that over and over too many times.

---

### Post by Rasa1111 on 2011-07-19
<snipped - b.>

Glad you got it going C.A. 
Good luck with your business. :KS

---

### Post by ClientAlive on 2011-07-19
> **Rasa1111 said:**
> 
Glad you got it going C.A. 
Good luck with your business. :KS


Thanks but no, I was wrong. It's back to the same thing. Just got my 2 GB RAM in the mail too (like an hour ago).

@Dave

So I did like you said. I started at the bottom of the row of drives; and one by one, unplugged both the power and the data cable for that one, then the next - powering up (if you could call it that) after each time. Took away one disk then the next disk then a disc then a disc. Then I started in on the expansion cards. One at a time and powered up after each removal for a total of 3 card. Still no difference.

Currently, the only things left plugged into the mobo are RAM, the CPU, 3 plugs that trace to the card reader and this other thing with audio jacks and a couple usb ports on it, this smallish square plug (white, about 1/2 inch X 1/2 inch, 4 prongs), the plug for each of 2 fans, and the power to the mobo.

I'm wondering if it's safe to power up after unplugging those kind of things. If I kept going I would eventually get to a point where all that's left is the power to the mobo.

I am starting to have a lot of thoughts though. In addition to the couple in my last post:

~ Maybe it's the power button itself
~ Maybe I somehow got some moisture underneath the CPU where the pins go into the socket (some chemicals are hygroscopic (absorb water from the air ethyl alcohol may be one of them).
~ Maybe it's just the monitor is going bad and the thing really is doing fine but not displaying. I have other monitors sitting around here. I'm gonna try that next with one I know works.

So what next guys? Is there anything left to hope for?
-------------------------

Edit:

Swapping the monitor has not changed the situation. Doesn't mean that isn't also part of the problem, just that it didn't change anything now.

Will bios still technically work with everything unplugged like that? I know it will without any hard drives because I've seen that before. It just doesn't report any disk because there's nothing there.

---

### Post by waveOSBeta on 2011-07-19
I'm new to this, but have you tried putting the hard drives in another computer? Just a thought.

EDIT: You kill*i*ed it? XD

---

### Post by ClientAlive on 2011-07-19
> **waveOSBeta said:**
> I'm new to this, but have you tried putting the hard drives in another computer? Just a thought.

EDIT: You kill*i*ed it? XD


I "killied" it? Lol. I'd laugh, but it hurts too much to do even that. Thanks for injecting a little humor into the whole mess though.

There's no other computer to put them in. The computer I'm typing on is my laptop and the only functional computer I have right now. I don't own a drive enclosure. The main point behind this was to have a second computer I could safely experiment and grow on. I have to take care of this one when it comes to trying new things. Thanks though. It's a nice idea, just not possible for me right now.
--------------------

Edit:

Lmfao! Well I guess I did killie it. Lol. I didn't realize I'd misspelled that until right now. If it was killie though, wouldn't that make it awesome? And to be awesome (or killie) it would have to at least run right.  :)

---

### Post by Detroit_Bad_Boy on 2011-07-19
I kind of scanned quickly through the replies and don't know if this was stated or not. Here is what you can do to check for physical problems. Look at the motherboard. There are tiny little canisters on it. Those are capacitors. If you see yellowish or whitish gooey stuff around them, then chances are you have a blown motherboard. 
  The only 2 options are as follows:


1. If you are good at soldering, then unsolder the suspected caps (capacitors), take them to radio shack or another electronics shop and get them replaced. Be sure to remember where they came off of the mobo (motherboard) and solder the new ones in place taking care not to put too much solder on the connections as this can cause 2 points to short out.

2. Buy another motherboard and bolt it into the case. Re-connect all the cables in their proper places. Re-insert the proc(processor) and fan and restart the machine. If your bios is wiped out you can download it from the computer makers site or from another site.
  Then wipe down your hard drive and install an OEM copy of the exact same windows program and when it asks for the CD key, use the one from the certification sticker on the side of the machine. Now you have your machine back in order and ready to use. OR install your favorite distro of linux. That OS is free and easy to use.
  
These 2 methods are a little more time consuming but WAY cheaper.

---

### Post by wep940 on 2011-07-20
And now that I've had my rant which I should get in trouble for (it's against forum rules), on  to help that ClientAlive is trying to find.
 
- with that number of drives, a 250 watt power supply is too small.  I would go with at least 400 watts minimum.  It may have caused some problems in your power supply now.
 
- as far as the suggestions I made, what I was getting at is if you put the PC back to the state it was in before you made ANY changes and you still have problems then the problem is deeper - perhaps your PS, motherboard, etc.
 
- if it's okay back at it's original state then make your changes 1 at a time and try booting each time.  As soon as the problem occurs you know a few things - either the PS can't handle it, the devices are configured incorrectly, maybe another type of hardware problem, even things we haven't thought of.  I won't make the claim of knowing what is causing your problem because I don't, but my troubleshooting would be starting at the beginning when things were working, and then working things up until the problem occurs.  That's just my way - someone else will probably have other ideas that are just as valid as well.

---

### Post by wep940 on 2011-07-20
I also just checked the pictures you had posted - I missed those.  The 4 pin cconnector you are showing as "was unplugged" does need to be plugged in to the appropriate jack on your motherboard as it provides other power for your CPU.  Things normally don't work at all without that cable plugged in.

---

### Post by ClientAlive on 2011-07-20
Thanks WEP940. It's probably going to be tomorrow evening before I can get to it. It's like past 2 am here now and I have to work in the morning.

I have an idea what a good way to go about this might be but I'd like to get a review/ critique before I set my hand to it again.

Here's what I'm thinking:

What I'd like to do is take the whole thing apart again and lay everything out. This time though, while I have it apart, I'd like to pull the CPU. I just want to make sure it doesn't have some moisture under it. I live in Sioux Falls, SD; and, if you look at the weather here for the last few days it's been very hot and extremely extremely humid.

When I cleaned it with the denatured I kinda went for it using a new but cheap paint brush. I was real liberal with it though and I didn't pull the cpu at that time (if you've read one of my earlier posts you understand why). So, I'm thinking, the combination of that and the weather and the fact that I did it all outdoors (on the balcony) may warrant a CPU inspection.

So then my plan I guess is to do all that plus I want examine the mobo very thoroughly for any cracks or the white stuff Detroit_Bad_Boy mentioned. The thing he said happens if something burns out.

If I spot anything obvious on the mobo I'll know that's at least part of the problem. I've never done any soldering that I can recall but if the little parts are cheap I'll give it a shot. I've seen it done before and I figure the hardest part is choosing the right guage of wire to use. I can practice putting a few spots on something else first just to get the hang of it (if it even comes to that).

So if everything looks good on the main board I'll reassemble it exactly the way it was before starting with the CPU. The only difference would have to be that the original disc drive stopped working way back when I first got it (about a year ago now I think). So I'll put it back as it was except for an optical drive- even with only 512 of RAM like it had when I got it.

I'm not sure if there's a best order regarding the type of component to add first but I figure RAM is pretty important to me - so if I get er' going when it's back as it was maybe I should start by adding more RAM one stick at a time. All goes well and I'll go after the second hard drive. If we're still good after all that I'll see about expansion cards starting with what I need/ want the most.

I'd also like to check the power button itself somehow (though I really don't think that's the issue it does seem odd the way it was acting). I don't own an electrical tester, nor have I ever used one, but maybe I know someone I can borrow one from. Google can probably show me how to use it.

What keeps bugging me though is the way it's acting is exactly like this one time. I fired it up but didn't realize that the RAM was still sitting on the table next to me (not in the machine). I imagine the way it's acting could be pretty common though and caused by a lot of things. I wouldn't know, this is my first experience with this kind of thing.

Another thing is something I noticed. On the Ethernet card I'd put in there (the NIC for cat 5 cable not the wirless NIC), it has a little place for a plug in one corner on the bottom of the card. It's white and looks just like the plug for the fans (4 prongs in a straight row, a very small, rectangular plug). I've wondered if it isn't supposed to get one of the leads from the psu.

What doesn't make sense about that theory though is that it was never plugged in and I did get bios setup the other day (with it not plugged in). Just something I noticed and kept thinking about. There is a way that theory might make sense though. I'm not sure how a psu is wired and I don't know if mine is a "switching" psu or even what that means if I did know. What I've thought though is that maybe plugging it in is optional (by design) because it can draw power through the pci slot (complete guesses so far) but that by opting to plug it in to it's own line it somehow lessens or balances the load on the psu?? Complete and total guesses but it 'sounds plausible' to me.

Anyhow . . .

I always write these long posts. I guess I can't help myself. Sorry.

But if you see anything I've talked about here that doesn't seem right or is just not optimum - please don't hesitate to let me know. I'll check here before I put my hand to it again.

I'll post back when I know something more too.

Thanks again WEP940. Catch you in a while man.


Jake

---

### Post by bapoumba on 2011-07-20
Couple removed posts, couple edits (snipped quotes/comments of gone posts).

---

### Post by wep940 on 2011-07-20
Sounds like a good way to start.  Not sure about the jack on the network card - I haven't seen that myself but to be honest I've worried more about wireless so I usually don't check the network card.
 
bapoumba:  thanks for cleaning some things up here, it was appreciated!

---

### Post by 1clue on 2011-07-20
The card reader and the audio/usb panel can be disconnected.

In fact, you should be able to power it up without RAM and at least get a signal (that should be in your motherboard owner's manual) that there's no RAM installed.  I THINK you can do it without CPU too, but I'm not sure I would want to pull an already-installed CPU.  I've never done it.  I think my current board handles this from actually reading the manual (yes, I'm a nerd) but not sure if all of them would.

Some of the ... biological mess ... might be stuck under your CPU somehow.  You might need to risk that.

I already told you what I think about using old equipment, but the good news is that if your hardware is roasted you aren't out much.  And you could always get another donation.  Old equipment is cheap, although you may have to go through a lot of it to get anything decent.

Best thing to do is ask around.  In fact, you might consider asking at businesses.  Tell them you're recycling and want to take their old equipment, they'll probably be glad to give it to you.  You might get actual server hardware that way, which will be big ugly and hot but quite possibly still a screaming workstation.

One IT guy I know has some quad core systems sitting on a floor in the corner because nobody wants them.  I don't because they're 32 bit.

One thing that asking at a big business might do is get you a machine that has never met a cockroach, never been overheated and never seen real abuse.

Don't talk to anybody but the IT head.  Keep in mind that in order to get rid of a computer they need to either sell it or pay somebody to take it.  Some equipment that is better than what you're talking about is just not interesting enough to a corporate environment to have somebody buy it.  Which means that they can give you some of it or pay somebody to haul it off.

---

### Post by ClientAlive on 2011-07-20
> **wep940 said:**
> Sounds like a good way to start.  Not sure about the jack on the network card - I haven't seen that myself but to be honest I've worried more about wireless so I usually don't check the network card.
 
bapoumba:  thanks for cleaning some things up here, it was appreciated!


I made a mistake about what that was. I looked at it this morn again and it was the data/fax/voice/modem card. It looks real old. Anyhow, doesn't change what I need to do I guess. Just wondered about that. I'll let ya' know what I find out.

:)


> **1clue said:**
> The card reader and the audio/usb panel can be disconnected.

In fact, you should be able to power it up without RAM and at least get a signal (that should be in your motherboard owner's manual) that there's no RAM installed.  I THINK you can do it without CPU too, but I'm not sure I would want to pull an already-installed CPU.  I've never done it.  I think my current board handles this from actually reading the manual (yes, I'm a nerd) but not sure if all of them would.

Some of the ... biological mess ... might be stuck under your CPU somehow.  You might need to risk that.

I already told you what I think about using old equipment, but the good news is that if your hardware is roasted you aren't out much.  And you could always get another donation.  Old equipment is cheap, although you may have to go through a lot of it to get anything decent.

Best thing to do is ask around.  In fact, you might consider asking at businesses.  Tell them you're recycling and want to take their old equipment, they'll probably be glad to give it to you.  You might get actual server hardware that way, which will be big ugly and hot but quite possibly still a screaming workstation.

One IT guy I know has some quad core systems sitting on a floor in the corner because nobody wants them.  I don't because they're 32 bit.

One thing that asking at a big business might do is get you a machine that has never met a cockroach, never been overheated and never seen real abuse.

Don't talk to anybody but the IT head.  Keep in mind that in order to get rid of a computer they need to either sell it or pay somebody to take it.  Some equipment that is better than what you're talking about is just not interesting enough to a corporate environment to have somebody buy it.  Which means that they can give you some of it or pay somebody to haul it off.

Well that sounds like an idea. I'll have to check into that. Thanks.

---

### Post by 1clue on 2011-07-20
> **ClientAlive said:**
> 
Well that sounds like an idea. I'll have to check into that. Thanks.

Fair warning:  Server hardware is inevitably noisy, as in it might sound like a jet engine in a small office.  It may also run hot, since it is generally designed for what people think is freezing cold and dry as a bone.

It Will Not have low power consumption.

I'm guessing though that server hardware is what you'll have to settle for.  I think that desktop hardware is probably kept around until it is completely dead, because somebody can always use it for a Remote Desktop client.  Unless you want to take a bunch of systems and try to make one good one.

---

### Post by waveOSBeta on 2011-07-20
For the power button, you can hook it up to a battery and a lightbulb as a test. :P

---

### Post by 1clue on 2011-07-20
Oh yeah.  If you don't have some micro probes you can take some phone wire with the ends stripped to go in one on each side of the switch, to see if that powers it up.

---

### Post by ClientAlive on 2011-07-21
> **1clue said:**
> Oh yeah.  If you don't have some micro probes you can take some phone wire with the ends stripped to go in one on each side of the switch, to see if that powers it up.

> **waveOSBeta said:**
> For the power button, you can hook it up to a battery and a lightbulb as a test. :P

Right on. Didn't really occur to me but yeah. Either of those would work. The lightbulb trick would probably be the simplest and most visible.


Pictures: [http://clientalive.shutterfly.com/pictures#n_5]("http://clientalive.shutterfly.com/pictures#n_5")


Whatever the value of old hardware, I must say that is a mighty pretty board. Looks fine as far as I can tell visually. No scorch marks or melted white stuff. If I wasn't gonna use it I'd turn it into a piece of art to put on the wall.

As for progress, the pictures pretty much say it all. I tore the whole thing down. The only thing left in the case is the PSU, the card reader, audio dock and the power button/ switch. I'm letting it sit out, apart for a while, to try and be sure it's totally dry of any moisture before I reassemble it.

You know, it's kinda funny. When I work on that thing I kinda get this nostalgic feeling. Lol. It's almost like fixing up an old car or something. Not that, that was the greatest machine even in it's hey day, but it is kinda neat to fix something up. Think about it, if you were an old computer wouldn't you want someone to fix you up and get you going again? Sure a brand new *** kicker would be awesome but there's something kind of neat about fixing an old computer up.

Even if I get a new computer I think I'd keep doing this just for kicks. Give em' away to some kids with Linux on it. Egg em' on to learn bash scripting and network admin and all kinds of cool comp sci stuff. These kids are smart these days. Start and 8 year old out on computers and by the time he's twelve he's got 3 programming languages down like a champ an a whole slew of other stuff.

I'll probably re-assemble the thing tomorrow, once I'm sure everything is good and dry. We'll giver er' another shot and see what happens. I'll do like was suggested by putting it back exactly as it was when I got it. Hopefully that does the trick and I can safely add to that to get a little batter set up.

Have a great night guys. Thanks for all your help.


Jake

---

### Post by 1clue on 2011-07-21
Do I see a picture of your RAM and CPU sitting on paper?  Even with old hardware that's really a bad idea.

Seriously, no matter what I said before if you get a kick out of resurrecting old hardware then by all means do it.  At that point the cost effectiveness of it is irrelevant.

---

### Post by 1clue on 2011-07-21
You should look up electrostatic sensitive device handling safety.

If you don't have a workstation then lay out a piece of aluminum foil, rest the case on it so that metal touches metal.  All your unplugged devices go on that.  Your work area is that.  Before you directly touch anything, touch both the chassis and the foil, then the device.

ESD damage is cumulative.  A little shock stays there forever, and when you reach the limit the device is dead.  That's a big part of my opinion about using old equipment, it might work fine but somebody drags their feet across the carpet and touch the keyboard and suddenly some device dies because it finally crossed the "finished" line.

---

### Post by waveOSBeta on 2011-07-21
Well, hope it works. :)

---

### Post by Swagman on 2011-07-21
Just earth yourself on a bare radiator pipe or such regularly

[Touches wood]

I've never had an issue with static on ANY computer I've ever built or worked on.

I don't know about the US but here in the uk our plugs (outlets) have a central earth pin. I usually leave the kettle lead connected to the mains but switched OFF at the outlet, this means the Earth is still connected so just touching the case discharges yourself.

I recently had a little problem with my daughters comp... She switched it on and it immediately switched off and stayed off.. Brand new psu so it wasn't that.. Dragged it into the garage for heart surgery.

See that scorch mark at the top of the mobo.. That wasn't even where the cpu resides but it still killed it.

[[IMG]http://img708.imageshack.us/img708/1332/pic0698.th.jpg[/IMG]](http://img708.imageshack.us/i/pic0698.jpg/)

view of the "proper" side
[[IMG]http://img191.imageshack.us/img191/3577/pic0693.th.jpg[/IMG]](http://img191.imageshack.us/i/pic0693.jpg/)

Replaced the dead Abit M2 with a cheap AsRock so I could transplant all the bits.. Kinda looks lost in that case doesn't it !

[[IMG]http://img849.imageshack.us/img849/685/pic0692.th.jpg[/IMG]](http://img849.imageshack.us/i/pic0692.jpg/)


In regards to that Athlon64 3200 your playing with.. thats EXACTLY what was in my machine until late last year when I upgraded to this Phenom II x4.

My brother promptly "claimed" my old gubbins and put it in his case and it's been running ever since... I'll see if I can find a pic of it on build day

[Edit]

Found it.. Took me long enough and then I found it by accident. I was actually looking for a pdf of installing debian on an AmigaOne !!

[img]http://img402.imageshack.us/img402/535/42c7.jpg[/img]

---

### Post by 1clue on 2011-07-21
I've definitely had issues with both static from improper ESD technique and with lightning, on different systems.  I also spent part of my college days working in a factory that made ESD-sensitive components.  Not following the proper procedure earned you the right to go find another job.

You never know if or how much any particular "static event" is going to mess your system up, or if it did, until you have a dead component.  It's also possible to mess a component up enough that it behaves erratically but still functions in some close-to-normal way, and it happens fairly often.

---

### Post by anewguy on 2011-07-21
> **1clue said:**
> I've definitely had issues with both static from improper ESD technique and with lightning, on different systems.  I also spent part of my college days working in a factory that made ESD-sensitive components.  Not following the proper procedure earned you the right to go find another job.

You never know if or how much any particular "static event" is going to mess your system up, or if it did, until you have a dead component.  It's also possible to mess a component up enough that it behaves erratically but still functions in some close-to-normal way, and it happens fairly often.
Hey, first off this is wep940 - I've just had my old account reactivated.

I couldn't agree more!  I've seen devices killed over time and some just at the "snap of the fingers" by ESD.  I've always used a mat with proper grounding and a grounding strap on me attached to that mat.  You can never be too careful.  These "amazing little devices" do some interesting things, but tolerating ESD isn't one of them.

1clue:  I apoligize for our earlier disagreement.

Dave ;)

---

### Post by 1clue on 2011-07-21
I had to look back to see if there was something worth apologizing for and I don't really see it.  Did a moderator delete something?

Yes, I saw the name change bit.

I don't expect everyone to believe me.  Some people agree with me, and others are wrong.  It's how the world works.  :D

---

### Post by bapoumba on 2011-07-21
> **1clue said:**
>  Did a moderator delete something?


Yes I did a page back.
[http://ubuntuforums.org/showpost.php?p=11066480&postcount=22](http://ubuntuforums.org/showpost.php?p=11066480&postcount=22)

---

### Post by ClientAlive on 2011-07-21
@1clue

Wow. Aside from someone just outright telling you about how ESD works, what are the chances of coming across something like that. Thanks. Oh, by the way, I do believe you about setting your components on foil, but on first impression that does sound a bit counterintuitive.

@wep940

You talk about a, what did you call it, a grounding line or something. I had no idea it is that serious (or that it is something that builds up over time). My entire apartment is carpeted too (even the balcony). That being the case it's probably a place one would need to take extra extra precaution. I wonder if ESD is something you would actually feel - like when you touch something and get a static shock - or if it can still be transferring to components and not even feel it, not even realize that it is.

So, I got my hands on lithium grease. Specifically it is called, "white lithium dielectric grease." I have been told before that a thin layer of lithium grease is supposed to be applied to the top of the CPU to help with heat transfer or something like that. I want to make sure I confirm this before I apply anything to that CPU though. Not just that applying something to the top of it is something that should be done; but, more specifically, whether it's the correct type to use. It's this word "dielectric" that has me wondering. I'll do a little googling on it right now.

This ESD thing also. So there is no way to remove what has built up? Even if there is, I guess it would only matter when the part is still functioning. Once it's dead, I don't imagine there's much that can be done. I was just curious.

You know, it's these things, the stuff about ESD and how it works and about putting grease on top of a processor that seem to me to be things you can really only get by it being passed along by others with experience. I could be wrong but I just get the impression these are little details that one isn't just going to see any old place.


> **Swagman said:**
> Just earth yourself on a bare radiator pipe or such regularly

[Touches wood]

I've never had an issue with static on ANY computer I've ever built or worked on.

I don't know about the US but here in the uk our plugs (outlets) have a central earth pin. I usually leave the kettle lead connected to the mains but switched OFF at the outlet, this means the Earth is still connected so just touching the case discharges yourself.

I recently had a little problem with my daughters comp... She switched it on and it immediately switched off and stayed off.. Brand new psu so it wasn't that.. Dragged it into the garage for heart surgery.

See that scorch mark at the top of the mobo.. That wasn't even where the cpu resides but it still killed it.

[[IMG]http://img708.imageshack.us/img708/1332/pic0698.th.jpg[/IMG]](http://img708.imageshack.us/i/pic0698.jpg/)

view of the "proper" side
[[IMG]http://img191.imageshack.us/img191/3577/pic0693.th.jpg[/IMG]](http://img191.imageshack.us/i/pic0693.jpg/)

Replaced the dead Abit M2 with a cheap AsRock so I could transplant all the bits.. Kinda looks lost in that case doesn't it !

[[IMG]http://img849.imageshack.us/img849/685/pic0692.th.jpg[/IMG]](http://img849.imageshack.us/i/pic0692.jpg/)


In regards to that Athlon64 3200 your playing with.. thats EXACTLY what was in my machine until late last year when I upgraded to this Phenom II x4.

My brother promptly "claimed" my old gubbins and put it in his case and it's been running ever since... I'll see if I can find a pic of it on build day

[Edit]

Found it.. Took me long enough and then I found it by accident. I was actually looking for a pdf of installing debian on an AmigaOne !!

[img]http://img402.imageshack.us/img402/535/42c7.jpg[/img]

Pretty board you have there. So, with that other one, the one with the scorch mark, what caused that in the first place? That was just from ESD??

As for the AMD processor - I know it isn't anything compared to modern CPUs; but I get the impression that, for what it's worth, it's a really great CPU. That isn't based on any documentable fact or special knowledge on my part, it's just the feeling I get about it. Don't really know why. I think mine is the one that has 1 MB cache (rather than the 512 KB one). Yeah, it is, I just looked at /proc/cpuinfo.

Cool pics, and and amazingly clean and tidy work area. Now that's something for me to look up to and to shoot for myself. Thanks.

---

### Post by ClientAlive on 2011-07-21
From Wikipedia:

> Because dielectrics resist the flow of electricity, the surface of a dielectric may retain stranded excess electrical charges. This may occur accidentally when the dielectric is rubbed (the triboelectric effect). This can be useful, as in a Van de Graaff generator or electrophorus, _or it can be potentially destructive as in the case of electrostatic discharge._

Source: [http://en.wikipedia.org/wiki/Dielectric#Some_practical_dielectrics](http://en.wikipedia.org/wiki/Dielectric#Some_practical_dielectrics)

Underline is mine. Now that doesn't sound good.

---

### Post by anewguy on 2011-07-21
Don't put lithium grease on the top of your CPU.  There are specific products made for this link between the CPU and the heatsink.  Some are inexpensive, others can be costly.  I personally just use Artic Silver, and it's available at Radio Shack if you have one near you.  There are a LOT of these products, so others will tell you what they use as well.

2 things you should know about electo-static discharge and the buildup of static electricity:

- Pc's have grounded cases (or at least the frame) which is why metal is used.  The motherboard mounts to that metal through screws that complete continuity between the motherboard frame ground and the case.  The power supply is grounded via it's mount to the case and of course to the mains power.  As long as nothing comes in between these things, ESD is not normally a problem.  However, remove the case sides, unplug the power and start messing inside, and you're looking for a problem.  I know Radio Shack sells some version of a grounding strap but I have no idea if it's any good or not - I still use the 1 I've had for eons.  This strap is normally a piece of fabric with a covered wire snapped onto it.  The strap goes around you wrist, the other end of the cable goes to ground.  I have a mat which I ground and then snap the end of the wire onto it.  I don't know if you can walk into some electronics parts store and get the mat or not - I got mine many years ago when I bought a large tool kit for computer repair.

- carpet is your enemy when working on electronic equipment.  Static builds up easily, particularly if you are in bare or stocking feet.  If you touch the "internal" of something like your computer and you get the type of static "shock" you would get touching something like another person or a light switch, chances are very very good you blew some part in your equipment.

---

### Post by waveOSBeta on 2011-07-21
So, how's it going?

---

### Post by 1clue on 2011-07-21
Wow.

Lots of info about ESD out there, and about all this stuff.

ESD damage is just that:  damage.  It can't be fixed.  It's not storage of electrons somewhere, it's burning of the circuit so it can't function anymore.

Grounding straps help, but if you're really in a pinch you can do pretty well with just keeping constant body contact between the part and the case of the computer.

Electrostatic sensitive devices are sensitive to transfer of voltages that are higher than the circuit is capable of handling.  To protect the circuit you need to keep everything at the same "potential" meaning you need to make sure electricity flows easily across the whole project.

Paper and carpet, and anything else which is not conductive, can have wildly different voltages right next to each other.  When the component touches the paper it can get a small but potent electrical shock.  Yes, just like the shock you feel when you get zapped.  And yes, the ESD device is sensitive to shocks that you can't feel.

If I'm in a hurry or don't care that much about he equipment, I do this:  Before I take anything apart, I blow off as much dust as I can.  Make sure there's a convenient spot on the chassis bare metal that is clean enough to get a good contact when my hand rests against it.  Before I touch any component, I touch the chassis.  I try to be touching the chassis every moment that I'm touching a component.  If I put a component down I try to put it somewhere on the chassis, or the power supply or whatever.

Grease:  Use something made for it.  You can either by CPU heat sink grease separately or when you buy the CPU and heat sink there's usually something in there with it.  It's ridiculously expensive if you measure price per unit volume but not as expensive as buying another CPU.

Some people say leave the power supply plugged in when you work.  It's sound advice but some people say no.  I think it doesn't matter much.  On the one hand, plugging it in causes the chassis ground to be linked to the electrical ground for the house, but I think it doesn't matter so much unless you're touching things with something else that's plugged in.  On the other hand, plugging it in also charges some of the wires and possibly energizes a component, which can also be hazardous.

---

### Post by anewguy on 2011-07-22
+1, and an addition regarding your power supply:

the reason it is normally recommended to unplug it is that even with the computer "turned off" with modern components all that really means is that the main power to the motherboard and components has been removed.  However, power is still present - this can be seen on some motherboards that have 1 or more status LEDS onboard.  Even with the power "off", you'll still see that LED lit, showing that the power supply voltage is present.  So, the true way to remove the power is to be sure the switch on the back of the PC on the power supply itself is set to off.  Modern power supplies always have this switch, however some older PCs did have power supplies with no external switch.  The only way to remove power was to unplug the power supply.  As already mentioned a few times, leaving it plugged in does maintain the frame ground to the mains, and this does provide more protection.  However, best practice has always said unplug the PC - it's the safest and recommended way before opening the case, especially for the non-technician.

---

### Post by ClientAlive on 2011-07-22
> **anewguy said:**
> Don't put lithium grease on the top of your CPU.  There are specific products made for this link between the CPU and the heatsink.  Some are inexpensive, others can be costly.  I personally just use Artic Silver, and it's available at Radio Shack if you have one near you.  There are a LOT of these products, so others will tell you what they use as well.

2 things you should know about electo-static discharge and the buildup of static electricity:

- Pc's have grounded cases (or at least the frame) which is why metal is used.  The motherboard mounts to that metal through screws that complete continuity between the motherboard frame ground and the case.  The power supply is grounded via it's mount to the case and of course to the mains power.  As long as nothing comes in between these things, ESD is not normally a problem.  However, remove the case sides, unplug the power and start messing inside, and you're looking for a problem.  I know Radio Shack sells some version of a grounding strap but I have no idea if it's any good or not - I still use the 1 I've had for eons.  This strap is normally a piece of fabric with a covered wire snapped onto it.  The strap goes around you wrist, the other end of the cable goes to ground.  I have a mat which I ground and then snap the end of the wire onto it.  I don't know if you can walk into some electronics parts store and get the mat or not - I got mine many years ago when I bought a large tool kit for computer repair.

- carpet is your enemy when working on electronic equipment.  Static builds up easily, particularly if you are in bare or stocking feet.  If you touch the "internal" of something like your computer and you get the type of static "shock" you would get touching something like another person or a light switch, chances are very very good you blew some part in your equipment.

Wow. This is getting expensive really quick. Obviously all these things are very necessary when working on computers - I can tell that. I just had no idea it was so . . . complicated. Based on what you've said I've basically done everything wrong a person can do up to this point. It would be a wonder if there is anything left to salvage at all.

That I can recall I have not felt/ experienced that static shock feeling yet while working on the thing but I have been working on it in the worst of conditions and in the most foolish way. I simply had no idea these things were so important. I wouldn't be surprised if I have fried my mobo and/ or some other part. I can only pray that isn't the case.

> **waveOSBeta said:**
> So, how's it going?

It is precisely because I don't have nor can I afford all these little extras that it's taking me so long. I don't see that I have any choice but to continue working on it as I have and hope for the best. At the very least I will attempt to find some makeshift items to use to ground myself (such as a piece of rubber to stand on) and to work more carefully (by discharging myself by touching metal before touching any component) and just hope for the best outcome, It is what it is right now. I wish I could do more and more quickly but I can't do anything more about my circumstances than what I already am (and they are changing, slowly but surely, as I continue to work hard to change them).

The ironic thing is that this was part of a plan to do exactly that. You see, I had this crazy idea that if I learned my stuff really well, could prove it, and went about it in the right way, I could maybe get a job doing something I love that pays better than what I make now (working with computers). That's one of the major reasons I was trying to get this other computer running - so I could study real hard and work, hands-on, to learn more. That and the fact that I'm pursuing a technology business idea of my own.


> **1clue said:**
> Wow.

Lots of info about ESD out there, and about all this stuff.

ESD damage is just that:  damage.  It can't be fixed.  It's not storage of electrons somewhere, it's burning of the circuit so it can't function anymore.

Grounding straps help, but if you're really in a pinch you can do pretty well with just keeping constant body contact between the part and the case of the computer.

Electrostatic sensitive devices are sensitive to transfer of voltages that are higher than the circuit is capable of handling.  To protect the circuit you need to keep everything at the same "potential" meaning you need to make sure electricity flows easily across the whole project.

Paper and carpet, and anything else which is not conductive, can have wildly different voltages right next to each other.  When the component touches the paper it can get a small but potent electrical shock.  Yes, just like the shock you feel when you get zapped.  And yes, the ESD device is sensitive to shocks that you can't feel.

If I'm in a hurry or don't care that much about he equipment, I do this:  Before I take anything apart, I blow off as much dust as I can.  Make sure there's a convenient spot on the chassis bare metal that is clean enough to get a good contact when my hand rests against it.  Before I touch any component, I touch the chassis.  I try to be touching the chassis every moment that I'm touching a component.  If I put a component down I try to put it somewhere on the chassis, or the power supply or whatever.

Grease:  Use something made for it.  You can either by CPU heat sink grease separately or when you buy the CPU and heat sink there's usually something in there with it.  It's ridiculously expensive if you measure price per unit volume but not as expensive as buying another CPU.

Some people say leave the power supply plugged in when you work.  It's sound advice but some people say no.  I think it doesn't matter much.  On the one hand, plugging it in causes the chassis ground to be linked to the electrical ground for the house, but I think it doesn't matter so much unless you're touching things with something else that's plugged in.  On the other hand, plugging it in also charges some of the wires and possibly energizes a component, which can also be hazardous.

Thanks for the advice. I will certainly remember that and be sure to, at least, work on it like that (making sure to always have that part of my body touching the case whenever touching any component). I'll be sure to get the proper equipment as quickly as possible too.

As far as ESD goes, I'd never heard it mentioned in connection with this. All it had ever been was something you laugh about after you drag your feet across the carpet and then touch your friend to give him a little shock. We didn't call it ESD either. We didn't call it anything, It was just a joke. I had no idea so I wouldn't have known to look it up.

I'll look for the proper product to use for that CPU also. Thanks.


> **anewguy said:**
> +1, and an addition regarding your power supply:

the reason it is normally recommended to unplug it is that even with the computer "turned off" with modern components all that really means is that the main power to the motherboard and components has been removed.  However, power is still present - this can be seen on some motherboards that have 1 or more status LEDS onboard.  Even with the power "off", you'll still see that LED lit, showing that the power supply voltage is present.  So, the true way to remove the power is to be sure the switch on the back of the PC on the power supply itself is set to off.  Modern power supplies always have this switch, however some older PCs did have power supplies with no external switch.  The only way to remove power was to unplug the power supply.  As already mentioned a few times, leaving it plugged in does maintain the frame ground to the mains, and this does provide more protection.  However, best practice has always said unplug the PC - it's the safest and recommended way before opening the case, especially for the non-technician.

The first thing that comes to mind when I hear about having the PSU plugged in while working is the thought that maybe I touch something that holds a charge and get hurt. If it were a choice I think I'd go the route you're saying and not have it plugged in. That just seems safer to me.

------------------

At this point, while I'd like to be working on the thing, what I'm hearing tells me it may take me some time to get the things I need. Hell, for all I know it may well be too late, for this unit anyhow. If nothing else I'll know for in the future. If I can't get this one up and running I'm just gonna concentrate on saving for some new components.

@1clue. I do get what you were talking about before. We all make choices about how to spend our time and time is limited. The wiser the choices one makes about how to spend that time the more profitable their life may be. Perhaps the more prudent choice for me is to spend more of my effort earning money - even if it takes 14 or 16 hour days 7 days a week. Perhaps the wiser choice is to spend the time I would be using working on this old beater to work on working. I don't know. I had just thought that in the time I had that I wasn't working I would try and get it going. Maybe there is no easy way out. Maybe I'll have work hard labor for a few more years and then I'll have the time to spend learning something better. All I can do is try.

---

### Post by anewguy on 2011-07-22
Hey, don't give up!!!!  Keep trying, and there is no need to rush - we'll be around when ever you need help, be it tomorrow or next year.

Keep that dream alive!  While some education is a good thing and I would strongly recommend it, you also need hands-on experience.  Doing something like this can give you that and you can learn.  If it doesn't work - so what?  You've learned a lot already - just keep in mind that failure is a teacher, not a bad thing.

I also believe it was 1clue who already mentioned this - there is a thing called electrical potential [if you think this is important to understand do a search on the web], and what you mainly want to do is keep yourself and what you are working on at the same level - when it's balanced you won't have static or overload.  As they stated, and others have mentioned, at a minimum touch the box on some piece of exposed metal, then don't go scuffling your feet or anything - just stay there and work on the PC.  Touching the machine releases any static.  Normally as long as you are touching the ground side of things first before handling a piece of equipment you should be fine.  Just don't do something like touch the components on or the card edge connector of a component without being certain you have grounded yourself.  It's also best not to touch those places anyway - the oils in your skin can start to play havoc on connectors, solder joints, etc..  Best to always handle things by the edge.

Really - don't give up!  Even if it fails you ARE learning!

---

### Post by 1clue on 2011-07-23
So how much are you learning with this build?

FWIW I thought you knew a bit more than you do when I said buy new parts.  The things you're learning now, some of them it's better to learn on used hardware.

My opinion is based on the possibility of having a bunch of stuff wrong, which is not nearly as likely with new hardware as it is with old hardware, especially if you're piecing it together.  A single problem is hard enough to diagnose, what if there are 5 things wrong?

The expensive things are worth it, but not absolutely necessary.

You don't want a rubber mat.  It won't help at all.  If you work on your kitchen table maybe, that might be enough.

Contact with the chassis is need not be continuous.  Before you touch a component you want to discharge any static that may have collected on your body.  So you touch your skin to the chassis, grab the part, remove the part and then let go of the chassis.  Don't walk around if you don't have to.

While holding the component, first touch the chassis with your skin, then while touching the chassis insert the part and screw it down.

When you're holding a component, try to hold it by the non-conductive parts.  For a card (network, video, whatever) hold it by the back metal panel piece or by the green fiberglass board part.  But the back metal piece is supposed to contact the chassis, so if you're touching the chassis while holding the card then the card is grounded.

The human body conducts electricity pretty good.  Not nearly as good as wire, but much better than wood or plastic.  When you contact the chassis then all the electrons hanging around on you (static electricity) move to the chassis in a relatively controlled fashion, to the part that is actually designed to handle it.  It lets the charge dissipate without causing any component's charge to drop too fast.

The thing that is most dangerous about static electricity and ESD is that you can totally ignore the procedure and still have a functional system one time, and another time just one mess-up and it's trashed.  The newer the equipment the more sensitive it is likely to be, because as chips get faster they use smaller and smaller circuit paths, which amounts to using thinner wire.

You hear a lot of people saying something like, "I never pay attention to that junk because I built my whole system on the rug and it worked fine."  That system may work fine, but chances are there is some significant damage and one or two more times may do it in.  You never know, because you never know exactly how much static is on that carpet or how much that specific component can handle.  You know it's broken when it doesn't work at all, or when it works erratically.

Good luck and have fun.

---

### Post by anewguy on 2011-07-23
And understand that when I mention the mat (not rubber by the way) it is because I worked at the component level on boards - not just cards themselves but the actual components on those boards.  A lot of this came from my mainframe days when certain components there, such as the things handling current mode logic, where extremely sensitive.  But if you leave things like a table cloth on the work surface that's when you'd also want a safe place to put the cards, etc., while you work.  A ground mat is really handy at these times.

Yes, for the average Joe working on something like the kitchen table or more preferably a work bench (just in case you just want to walk away from it for a day or 2 ;) ) is perfectly fine.  The important thing is to ground yourself to the chassis (case) prior to working on it.  Occasionally touching it again while working may not help, but it sure won't hurt!  But this is also where a grounding strap works best - you can clip it to the chassis and eliminate having to keep touching the chassis and can use both hands freely.

BTW - nobody replying here is "God" so be sure to read everything and take away from them all what you need to help you.  Some people like to post things and contradict another because they think their experience outweighs another.  Don't be fooled by one persons humility into thinking the other guy must be "better".  Some people just believe more in the idiom of walk quietly and carry a big stick.  This applies to this entire forum - but do try to pay attention when you see a forum admin or monitor posting.  You'll get used to certain names here as the ones who supply the best information - I don't claim to be one of those.  Don't rely on any one persons view, and remember to always lean on the side of caution.  There really are some best-practice rules for these situations, but the main thing is to use common sense when handling any of this equipment.

Just stay at it, don't be afraid of mistakes, and learn as much as you can.  While I'm sure you'd like to have a working PC, if your interests lie in knowing more about tear down and build up and perhaps some trouble shooting, this is a great opportunity.

Don't give up - have fun with it, and don't be afraid to just walk away from it for a few days (or more).  You have no real rush here and sometimes it helps just to take things in step and take some time away.

---

### Post by ClientAlive on 2011-07-23
> **1clue said:**
> So how much are you learning with this build?

FWIW I thought you knew a bit more than you do when I said buy new parts.  The things you're learning now, some of them it's better to learn on used hardware.

My opinion is based on the possibility of having a bunch of stuff wrong, which is not nearly as likely with new hardware as it is with old hardware, especially if you're piecing it together.  A single problem is hard enough to diagnose, what if there are 5 things wrong?

The expensive things are worth it, but not absolutely necessary.

You don't want a rubber mat.  It won't help at all.  If you work on your kitchen table maybe, that might be enough.

Contact with the chassis is need not be continuous.  Before you touch a component you want to discharge any static that may have collected on your body.  So you touch your skin to the chassis, grab the part, remove the part and then let go of the chassis.  Don't walk around if you don't have to.

While holding the component, first touch the chassis with your skin, then while touching the chassis insert the part and screw it down.

When you're holding a component, try to hold it by the non-conductive parts.  For a card (network, video, whatever) hold it by the back metal panel piece or by the green fiberglass board part.  But the back metal piece is supposed to contact the chassis, so if you're touching the chassis while holding the card then the card is grounded.

The human body conducts electricity pretty good.  Not nearly as good as wire, but much better than wood or plastic.  When you contact the chassis then all the electrons hanging around on you (static electricity) move to the chassis in a relatively controlled fashion, to the part that is actually designed to handle it.  It lets the charge dissipate without causing any component's charge to drop too fast.

The thing that is most dangerous about static electricity and ESD is that you can totally ignore the procedure and still have a functional system one time, and another time just one mess-up and it's trashed.  The newer the equipment the more sensitive it is likely to be, because as chips get faster they use smaller and smaller circuit paths, which amounts to using thinner wire.

You hear a lot of people saying something like, "I never pay attention to that junk because I built my whole system on the rug and it worked fine."  That system may work fine, but chances are there is some significant damage and one or two more times may do it in.  You never know, because you never know exactly how much static is on that carpet or how much that specific component can handle.  You know it's broken when it doesn't work at all, or when it works erratically.

Good luck and have fun.

What I started doing is keep one hand on the box, touch the other to it once or twice (tips of my fingers), reach over with that hand (other hand still holding the box) and grab my part, then rest both elbow on the edge of the box while I do what I need to do. It's not uncomfortable and is easy to do. Based on what you just said maybe it's slightly over-kill but I think it's worth it for safety sake.

Your right about learning my lessons on old stuff. When I started this project I didn't know a thing about ESD or other unsafe practices (working on the carpet for example). I think I did everything wrong a person can do - even to the point of placing components on a piece of newspaper. Luckily, the mobo seems ok (I got er' fired up, but more on that at the end of this). So, yeah, if I was gonna learn the hard way, which seems to be the case here, I would rather do it on donated, old parts than when I get nice components that are new (and I will soon, I'll see to that).

All in all this is very exciting. Different strokes for different folks, but I'm definitely computer folks. I love the feeling I get from doing this. Coolest thing on earth.  :D  It thought it beat me, and maybe it has, I'm not to the finish line yet; but, so far, I'm winning.

BTW, I'll tell you something intersting - though probably not a surprise. I talked on the phone today to the guy who does the builds at a local computer shop. I brought up this thing about ESD and kind of ran down everything I've been hearing in this thread. I wanted to hear what he had to say. He told me he never wears a ground strap and that the stuff about keeping contact with the box is not necessary. He doesn't stand on any mat. He thinks that the newer components, "anything 4 years or newer" is not as sensitive to ESD. FWIW I, personally would feel more comfortable using the grounding strap and standing on the mat and all of that - especially if it's my money that paid for those parts. Now, personally (and of course I'm no expert) after hearing that I'm not sure I would purchase a computer from them. Compared to what I've been told here the guy sounded reckless; and, truth is, when you buy a computer from someone, it is your money going into those parts.

Just thought I'd share that.


> **anewguy said:**
> And understand that when I mention the mat (not rubber by the way) it is because I worked at the component level on boards - not just cards themselves but the actual components on those boards.  A lot of this came from my mainframe days when certain components there, such as the things handling current mode logic, where extremely sensitive.  But if you leave things like a table cloth on the work surface that's when you'd also want a safe place to put the cards, etc., while you work.  A ground mat is really handy at these times.

Yes, for the average Joe working on something like the kitchen table or more preferably a work bench (just in case you just want to walk away from it for a day or 2 ;) ) is perfectly fine.  The important thing is to ground yourself to the chassis (case) prior to working on it.  Occasionally touching it again while working may not help, but it sure won't hurt!  But this is also where a grounding strap works best - you can clip it to the chassis and eliminate having to keep touching the chassis and can use both hands freely.

BTW - nobody replying here is "God" so be sure to read everything and take away from them all what you need to help you.  Some people like to post things and contradict another because they think their experience outweighs another.  Don't be fooled by one persons humility into thinking the other guy must be "better".  Some people just believe more in the idiom of walk quietly and carry a big stick.  This applies to this entire forum - but do try to pay attention when you see a forum admin or monitor posting.  You'll get used to certain names here as the ones who supply the best information - I don't claim to be one of those.  Don't rely on any one persons view, and remember to always lean on the side of caution.  There really are some best-practice rules for these situations, but the main thing is to use common sense when handling any of this equipment.

Just stay at it, don't be afraid of mistakes, and learn as much as you can.  While I'm sure you'd like to have a working PC, if your interests lie in knowing more about tear down and build up and perhaps some trouble shooting, this is a great opportunity.

Don't give up - have fun with it, and don't be afraid to just walk away from it for a few days (or more).  You have no real rush here and sometimes it helps just to take things in step and take some time away.

First off, thanks for your earlier encouragement. Life really can be an up-hill battle sometimes.

There's one thing that still doesn't make sense to me, but I'm sure I'll find out about it. This thing about setting components on a piece of aluminum foil. That just seems counterintuitive to me. Maybe I'm understanding that wrong but metal is conductive right? I would think that's something you don't want to do, not something you want to do. Again though, I'm probably not understanding it correctly.

Now on to the good news (so far anyhow). I got my hands on some CPU compound from a local shop (it came in a syringe - weird). Got the CPU, heat sink, the 512 of orig RAM in there, mobo bolted down, plugged in the power to the mobo (big rectangular plug), and that other plug (the little square one), and it fired up. First thing it told me was the CPU fan failed and it was powering down. (I hadn't put either fan in at that point yet). Well, I didn't think about that being monitored like that (though I've heard of it). So, I learned two things right there on the spot. I learned (1) that it would fire up as I had it assembled and (2) that the thing that monitors the fans was working. I decided to push the line forward a bit more. I powered off, unplugged the cord, and inserted the rest of the RAM (2 X 1 GB) - taking me up to a grand total of 2.5 GB. More importantly than that though, that two sticks of memory (the 2 GB) was RAM I recently bought off ebay. It fired up again. Now I learned another thing. The ebay RAM I have works. Of course, with no fans it did that same (powered down because it thinks the fans failed). So I unplug and put the fans in (both of them). The thing is sitting there running now, quiet as a mouse. Everything, so far, is working. We'll see what happens as I move forward.

I need to make sure I set the bios up right. I'm in setup now and prob shouldn't be dallying about making my settings. I just want to make sure I make the right choices since, I think, some of it is Windoze specific. (Plug N Play for example). I don't want to turn off anything important but I don't want to enable anything that may cause a problem either. It need to be 'just-right'. My baby needs to be just right. Lol.  :D

So, here I go. I'll let ya all know how it goes.

Oh, one other thing I've been wondering about, have done a little googling on it (though it seems to be a big topic) and have asked a couple techs over the phone - what the compatibility is of components vs. PCI 1x. For some reason I just don't feel comfortable with the information I've gotten so far. Kinda vague; or, give you the impression the person doesn't give a rip to answer one way or another. What they tell me is, if the card fits in the slot it will work. If that's true then fine, I'm happy. But to hear someone say that is a little . . . err . . . disconcerting.

Ok, here I go. CMOS set up time.

:popcorn:
-----------------------------

Edit:

Well, so there's some settings in setup here that I'm not so sure of. I only say that because the the next thing, if I can get this machine fully functional, is to do a stage 3 Gentoo build then Xen. Gentoo gets to be my dom0. That was the plan from the start.

So, what I'm thinking is if I'm going to be compiling a kernel, and all the config settings involved in that, I wonder if having settings in bios similar to config in kernel is going to be important. For instance, bios has a setting for USB legacy support. I'm guessing that this is also going to come up in my kernel config and that it is something that needs to be included (no matter what the other hardware specific settings are that you choose). If, for instance, it were not enabled in bios maybe it would cause a problem even if it were compiled into the kernel. Maybe even cause some real trouble. Now that was just something I chose for an example - I don't know the terminology so I don't know how else to communicate it. So, that being just an example, what about the other things? Things like, onboard 1394 for firewire. I don't see a firewire port on the machine anyway. Or what about the "SATA Adapter" it says is "Enabled"? I'm using all IDE drives and there is no floppy. And I'm only at the second of five tabs in the bios settings.
---------------------------

Edit 2:

OMG!! I have more questions than I can shake a stick at! + both hard drives. Power up and enter setup. Both drives shown as "First" Channel Device (one is 0 and one is 1). In the list there is also a "Second Channel" a "Third Channel" and a "Fourth Channel). I wonder what these channels are? I wonder if they are in any way connected to where that flat cable is connected on the board? Google . . .

Just, I don't know, just sharing my thoughts/ experiences I guess. For what it's worth (prob not much).

---

### Post by anewguy on 2011-07-23
Have fun.  I've stated my piece and it is founded in 35+ years of low-level technical support on everything from large mainframes down to micros.  Someone else wants to contradict everything?  Let them play God.  I'm outta here.  Contrary to someone, I'm not on here to say I'm good, I'm the best, I'm right.  I'm purely on here to help.

Want to be able to use 2 hands and not have elbows resting on the case?  Try a grounding strap.  Enough said.

---

### Post by Swagman on 2011-07-24
That sounds like you're using IDE drives and not sata.

IDE uses the long flat cable and should have 3 connectors. One going to the Mobo the other two as Master & slave


The IDE connectors on the Mobo will be labelled IDE 1 ,2 ,3 etc
Seriously, get your magnifying glass out as they are marked.

The blue wire on on the flat IDE cable always goes to pin 1 but these days the connectors are keyed so you cant plug them in the wrong way anyway.

The furthest end on the connector is usually "Master" and the one in the middle is slave, which is usually opposite to what you want !!

Master being boot drive, slave being cdrom (or Optical these days). If that is the case then you wont have to mess around with drive jumpers setting master & slave (drives are usually pre-set to master so you would only need to alter one to slave)

If you are using more than one IDE drive on the same lead you usually **WILL** need to set one hard drive to be slave although some O/s's can now auto detect drive no.s

When I started Non Linear Video Editing I used a Mobo ([**Asus CUBX**](http://www.tomshardware.com/reviews/bx-flagship,193-2.html) <--- Link to Mobo) that had FOUR IDE connectors on the mobo (2 blue & 2 black) meaning I could use EIGHT IDE drives <--- That was quite rare for a Mobo in those days.

If you need any help...Just shout

---

### Post by ClientAlive on 2011-07-24
> **Swagman said:**
> That sounds like you're using IDE drives and not sata.

IDE uses the long flat cable and should have 3 connectors. One going to the Mobo the other two as Master & slave


The IDE connectors on the Mobo will be labelled IDE 1 ,2 ,3 etc
Seriously, get your magnifying glass out as they are marked.

The blue wire on on the flat IDE cable always goes to pin 1 but these days the connectors are keyed so you cant plug them in the wrong way anyway.

The furthest end on the connector is usually "Master" and the one in the middle is slave, which is usually opposite to what you want !!

Master being boot drive, slave being cdrom (or Optical these days). If that is the case then you wont have to mess around with drive jumpers setting master & slave (drives are usually pre-set to master so you would only need to alter one to slave)

If you are using more than one IDE drive on the same lead you usually **WILL** need to set one hard drive to be slave although some O/s's can now auto detect drive no.s

When I started Non Linear Video Editing I used a Mobo ([**Asus CUBX**](http://www.tomshardware.com/reviews/bx-flagship,193-2.html) <--- Link to Mobo) that had FOUR IDE connectors on the mobo (2 blue & 2 black) meaning I could use EIGHT IDE drives <--- That was quite rare for a Mobo in those days.

If you need any help...Just shout


Hi Swagman,

Well, I'm making progress but now have run into another obstacle. I suspect it has to do with configuring those drives correctly (the whole master/ slave thing and which channel for what). I started a different thread for it though. I'm really inexperienced with this stuff and so, a lot of times, I end up starting some thread and it goes all over the place content wise. I also had never used a forum before coming here, so that's another thing.

Here's a link to the other thread I started. I guess no one is around that can help or something cause it's just been sitting there for a while.

[http://ubuntuforums.org/showthread.php?t=1810879](http://ubuntuforums.org/showthread.php?t=1810879)

---

