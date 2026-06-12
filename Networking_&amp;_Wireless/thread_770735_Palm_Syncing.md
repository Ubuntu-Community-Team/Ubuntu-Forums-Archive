---
title: "Palm Syncing"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by AmpersUK on 2008-04-27
Greetings,

I have borrowed a Palm from a friend as if I can get the syncing working I may invest in a new Palm PDA/Phone.

I connect it to the USB cable, and ***made sure*** I click the USB option ***and not*** the Serial option but each time I get the following error message:[INDENT]*Failed to connect using device "Cradle" on port "/dev/pilot". Check your configuation as you requested old-style usbserial "ttyUSB" syncing, but do not have the usbserial "visor" kernel module loaded. You may need to select a "usb" device.*
[/INDENT]This is happening on a desktop x86 using a dual boot with[COLOR=Red]** Ubuntu 8.04**[/COLOR] and a Palm Tungsten E, and a USB cable fitted directly to the front of the PC. Not to a separate USB plug.

Any ideas would be greatly appreciated.

---

### Post by kam.samji on 2008-04-29
Hi. I have a Palm TX and using it with 8.04 and have the same problem. I have used it with various premutations of "USB", "Serial" etc, but with no avail.

Is Gnome Pilot the only software we can use? What does it actually do?

---

### Post by AmpersUK on 2008-04-29
> **kam.samji said:**
>  Is Gnome Pilot the only software we can use?

It seems to be,** I hope someone can answer this** as I would like to get the phone.

At present I have a great little HTC S710 but nothing seems to work with it.

---

### Post by deh1963 on 2008-04-29
> **AmpersUK said:**
> Greetings,

I have borrowed a Palm from a friend as if I can get the syncing working I may invest in a new Palm PDA/Phone.

I connect it to the USB cable, and ***made sure*** I click the USB option ***and not*** the Serial option but each time I get the following error message:[INDENT]*Failed to connect using device "Cradle" on port "/dev/pilot". Check your configuation as you requested old-style usbserial "ttyUSB" syncing, but do not have the usbserial "visor" kernel module loaded. You may need to select a "usb" device.*
[/INDENT]This is happening on a desktop x86 using a dual boot with[COLOR=Red]** Ubuntu 8.04**[/COLOR] and a Palm Tungsten E, and a USB cable fitted directly to the front of the PC. Not to a separate USB plug.

Any ideas would be greatly appreciated.

I just went through this process with my Tungsten C.

At the Device Settings screen, click the radio button for USB and then click the down arrow at "/dev/pilot".  Select "usb:" from the pull-down menu.  That should fix the problem (or at least that's what I did).

---

### Post by AmpersUK on 2008-04-30
> **deh1963 said:**
> I just went through this process with my Tungsten C.

At the Device Settings screen, click the radio button for USB and then click the down arrow at "/dev/pilot".  Select "usb:" from the pull-down menu.  That should fix the problem (or at least that's what I did).

**Thank you very much for that. It is now working very well.**

*I am now contemplating buying an up to date one with WiFi and Bluetooth. And changing my phone for something that just makes and receives telephone calls. So that I can rely more on the phone battery to always be charged :-)*

---

### Post by mshumer on 2008-05-06
I use Ubuntu 8.04 on a Sony R505DL laptop and had the same problem connecting my treo 755p to jpilot. usb: worked perfectly the first time.
Thanks!

---

### Post by rohan1 on 2008-05-31
Thanks for the usb: info...finally managed to set up the palm tungsten with j pilot....anyone aware of a handbase alternative that works on ubuntu

---

### Post by bgoody on 2008-05-31
Hi.  If you have a TX or other wireless Palm and you want to get really groovey you can sync it wirelessly.  Go to the Preferences, Serial Port= Other and in the space where you usually put the USB0 or whatever put     net:any

I think it the router will ask you for your password the first time but it's been awhile so I can't remember but it works VERY well without wires, settings etc.

Brian

---

### Post by LaneLester on 2008-06-01
> **bgoody said:**
> Hi.  If you have a TX or other wireless Palm and you want to get really groovey you can sync it wirelessly.  Go to the Preferences, Serial Port= Other and in the space where you usually put the USB0 or whatever put     net:any

Wow! Thanks for that, Brian. I just compiled the latest pilot-link and jpilot 1.6.0 and the usb: setting didn't work for me. But net:any did with my Tungsten C!

I had to give the Palm the static IP of the computer where I had jpilot installed, and then the sync proceeded flawlessly.

Lane

---

### Post by bgoody on 2008-06-01
Hi.  I remember the first time I tried it and heard it connect via wireless to sync.  What a sound!  It's amazing that that method is so hidden.  jPilot too is a hidden gem.

I was never able to get the stock Ubuntu Palm sync working.  I think it's because it's tied up too closely with Evolution.

If you use Google calendar there's a way to sync your Palm over the air to it although it does cost a little bit.

Brian
> **LaneLester said:**
> Wow! Thanks for that, Brian. I just compiled the latest pilot-link and jpilot 1.6.0 and the usb: setting didn't work for me. But net:any did with my Tungsten C!

I had to give the Palm the static IP of the computer where I had jpilot installed, and then the sync proceeded flawlessly.

Lane

---

### Post by LaneLester on 2008-06-02
> **bgoody said:**
> I was never able to get the stock Ubuntu Palm sync working.  I think it's because it's tied up too closely with Evolution.

Considering the popularity of (x)Ubuntu, it's surprising the Jpilot people don't support it better.

> If you use Google calendar there's a way to sync your Palm over the air to it although it does cost a little bit.

I quit using my Palm calendar, even though I have the slick Agendus, because I prefer Google Calendars. Based on your comment, I googled a free alternative which I still have to test: [http://www.goosync.com/]("http://www.goosync.com/")

Later: OK, I got it going, but it's not very useful for me. The power of Google Calendar is multiple calendars, and you can only sync your personal calendar for free. To do multiples, you have to sign up for a 19.95 pounds ($31) annual subscription. Too expensive. Too bad.

Lane

---

### Post by Ichido on 2008-06-09
> **deh1963 said:**
> I just went through this process with my Tungsten C.

At the Device Settings screen, click the radio button for USB and then click the down arrow at "/dev/pilot".  Select "usb:" from the pull-down menu.  That should fix the problem (or at least that's what I did).

What Software/Program are you referring to?
I have a Zire 72 I'm trying to sync with my Ubuntu 8.04.
Evolution wants to know what Device?
I do not see any 'Radio' buttons, just a blank window to type in a connection.
I've tried /dev/pilot, /dev/usb,but I get only "Error; no such device"!?
I could not do any better with jpilot.

---

### Post by danbodoh on 2008-06-09
Ichido,

There's some confusion here about gnome-pilot (packaged with Ubuntu) and JPilot (you get get it through synaptic or sudo apt-get install jpilot).

Gnome-pilot syncs its data to Evolution, and you can set it up under "Preferences...PalmOS Devices".

I prefer JPilot myself.  It has its own GUI like the Palm Desktop on Windows; it does not sync to Evolution.

Dan Bodoh

---

### Post by Ichido on 2008-06-09
> **danbodoh said:**
> Ichido,

There's some confusion here about gnome-pilot (packaged with Ubuntu) and JPilot (you get get it through synaptic or sudo apt-get install jpilot).

Gnome-pilot syncs its data to Evolution, and you can set it up under "Preferences...PalmOS Devices".

I prefer JPilot myself.  It has its own GUI like the Palm Desktop on Windows; it does not sync to Evolution.

Dan Bodoh

You are correct when you say that I am confused!
I've tried jpilot, but it seems that Evolution 'takes over' the sync!?
Should I "Uninstall/Remove" Evolution/Gnome-pilot first?
Where do I find this "Radio Button" to select USB, is it in jpilot?
Is the apt-get a "Better" jpilot than the "Synaptic" version?
Any help would be appreciated!

---

### Post by danbodoh on 2008-06-09
> **Ichido said:**
> 
I've tried jpilot, but it seems that Evolution 'takes over' the sync!?
Should I "Uninstall/Remove" Evolution/Gnome-pilot first?

I was able to disable gnome-pilot (The Evolution sync) with "Preferences...PalmOS Devices...Devices" and then delete the items in the list

> **Ichido said:**
> 
Where do I find this "Radio Button" to select USB, is it in jpilot?


In JPilot, go to "File...Preferences...Settings" and type "usb:" (no quotes, but with the colon) into the 'serial port' field.

> **Ichido said:**
> 
Is the apt-get a "Better" jpilot than the "Synaptic" version?


They are one and the same.  'apt-get' and 'synaptic' are two different programs that essentially do the same thing.

Dan Bodoh

---

### Post by Unix_Slayer on 2008-06-09
Too bad Rim is so far behind putting out software for linux. First time I would say, you Palm guys are lucky. I would love to sync my Blackberry.

---

### Post by bgoody on 2008-06-10
Hi.  You can sync your Blackberry and/or your Palm and Google contacts but it cost $50+- a year.  GooSync.  You can only do one at a time.  I did my Palm first, then the Blacberry and then Google.  Brian

> **Unix_Slayer said:**
> Too bad Rim is so far behind putting out software for linux. First time I would say, you Palm guys are lucky. I would love to sync my Blackberry.

---

### Post by kaligus on 2008-07-18
> **rohan1 said:**
> Thanks for the usb: info...finally managed to set up the palm tungsten with j pilot....anyone aware of a handbase alternative that works on ubuntu

FWIW and after spending two months looking, I installed my handbase desktop in wine and all is well except the inability to sync the databases (which I never used anyway so not out anything here :lolflag: )

You have to manually load the handbase.prc if its not already installed, and I havent upgraded to 4.x yet.

---

### Post by jande9 on 2008-07-20
> **deh1963 said:**
> I just went through this process with my Tungsten C.

At the Device Settings screen, click the radio button for USB and then click the down arrow at "/dev/pilot".  Select "usb:" from the pull-down menu.  That should fix the problem (or at least that's what I did).

Thanks for this info because that is my problem too, but where exactly is this "device settings" screen.  I managed to get my Tungsten E working using the info later on in this thread with j-pilot, but I prefer to use Evolution.

I am using 7.10.

Thanks

---

### Post by Ichido on 2009-03-06
> **danbodoh said:**
> I was able to disable gnome-pilot (The Evolution sync) with "Preferences...PalmOS Devices...Devices" and then delete the items in the list



In JPilot, go to "File...Preferences...Settings" and type "usb:" (no quotes, but with the colon) into the 'serial port' field.



They are one and the same.  'apt-get' and 'synaptic' are two different programs that essentially do the same thing.

Dan Bodoh

Every time I try to Sync, I'm told that The USER ID is Different!
I tried a FULL Uninstall of all jpilot and jppy, then Reinstall, but no good. Still not working.

---

### Post by mattmanb on 2009-07-06
i've a treo 755p with jpilot (ver 1.6.0) on an eee pc1000h running ubuntu 8.10  i had to set the jpilot settings to "usb": at 57600 baud with the "palmos devices" (in the prefferences tab) to "usb" @ 57600 baud and device to "/dev/pilot" (this is the part that finally made it work.)  prior to sync i run the "modprobe visor" in the terminal.  works like a champ!
as an aside i run "usb modem to tether the 2 together to browse the web under linux.  i use pdanet to tether them in windows.  i've an unlimited data plan with verizon.  so when i'm  on the road i browse for free...
best of luck

---

