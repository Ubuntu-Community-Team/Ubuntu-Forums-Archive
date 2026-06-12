---
title: "Off-Brand Camera"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by bytescribe on 2010-01-22
I have an off-brand camera I've had for several years now. I tried using the USB cord that came with it when I was using Gutsy. Because it's off-brand (a DXG-380), F-Spot did not recognize it. 

I do not have the budget to get a fancy name-brand camera that's in the F-Spot list of "recognizability." So, does anyone have any useful techniques to get F-Spot to recognize ANY off-brand camera at all?

I know there is a "listing" in F-Spot for "other camera," but either I did not know what I was doing, or it just won't recognize my camera using that "listing", period.

So I'm thinking I needed to come here and get some info, in order to start fresh, with Hardy Heron.

Any help you can give me is appreciated. :-D

Thanks,
Kat ^.^

---

### Post by candtalan on 2010-01-23
Does the camera have a removable memory card? Because I find it much more convenient to use the card in a card reader than actually connect my camera directly. 

Cameras sometimes have a menu method of a setting for choosing which type of transfer to use, so that might be worth looking for.

And just a thought. Digikam is a clever app so it might be worth looking at for tests.

And of course keep ubuntu fully updated.
good luck

---

### Post by bytescribe on 2010-01-23
No, no removable card. It's not that fancy of a camera...I got it from a buddy of mine who was also on a budget. :-P

And it was originally Windows-based with a CD-ROM disk with somethin' called "Mr. Photo" on it...now if that's not off-brand, I dunno what is! :-P

But I'll remember to try Digikam, too...

---

### Post by HermanAB on 2010-01-23
The best cameras are the ones that connects over USB as a mass storage device (E.g. Olympus), in which case you don't need any special software, you just plug it in, it gets mounted like a disk drive and then you click-drag-drop your pictures somewhere.  

So, what happens when you plug the thing in?  Do you get an icon on the desktop?

---

### Post by cgroza on 2010-01-23
try picasa from google... it is in the repos...

---

### Post by anewguy on 2010-01-23
With the camera plugged in to USB, do the following in a terminal window (applications/accessories/terminal) and post the output back here:

sudo lsusb <press enter>


Some of the cheaper (and some not so cheap either in my book) use proprietary drivers in Windows.  A few of the cameras can be made to work in Linux, but usually not without a lot of work.

Try searching for flat-photo drivers (I *think* that's the name - came with some Radio Shack cameras) for Linux.

In the mean time, post back the output from above.

dave :)

---

### Post by bytescribe on 2010-01-23
> **HermanAB said:**
> The best cameras are the ones that connects over USB as a mass storage device (E.g. Olympus), in which case you don't need any special software, you just plug it in, it gets mounted like a disk drive and then you click-drag-drop your pictures somewhere.  

So, what happens when you plug the thing in?  Do you get an icon on the desktop?

Thanks for the recommendation...I have indeed considered getting an Olympus as they are a tried-n-true brand and for me, they are not as expensive as a Nikon. ;-) By the way, HermanAB, if you have an Olympus, is it a PowerShot, and what do you usually use it for? I love doing digital photography, but right now it's more of an enjoyable hobby just for the sake of finding artsy-looking setups in the natural world. ;-)

As for what my old, cheap-@$$ camera does? It doesn't even show an icon on the desktop...at least that's not the result I got with Gutsy Gibbon...because it did not work with Gutsy I have been hesitant to even try it with Hardy. :-P 

'anewguy' wrote: "With the camera plugged in to USB, do the following in a terminal window (applications/accessories/terminal) and post the output back here:

sudo lsusb <press enter>"

Considering my budget is super-tight, I will try ANYthing to get my old camera to work with Linux...
I will try anything to save myself some money!

---

### Post by anewguy on 2010-01-23
Please do post back the output from the command I posted.  It will return a string, including the manufacturer id and product id (xxxx:xxxx) that I need.

Also, try running one of the camera apps as superuser, i.e., open up a terminal window and type:

sudo f-spot <press enter> Note:  not sure if f-spot is the name - you may need to look at the properties for the menu entry to see what the name is (I'm in Windows right now or I'd look for you).  The reason to try this is that some usb devices get mounted as owned by root, and as a result aren't even visible to an application unless the application is run as root.  If running as root does work, I can give you what you'll need to do in order to just run as a regular user (if you run as root, any files created - picture images, etc. - will be owned by root and you won't be able to get at them with your normal logon).

Please post back the output from the command I posted, and try running as root and post back what happens with that as well.

Dave :)

---

### Post by no2498 on 2010-01-23
i have a cheep Polaroid $65.00
i need to turn it on before i plug it in the cam screen on the cam has a computer button  to push before it connects
may help may not its a shot

---

### Post by no2498 on 2010-01-23
also look on line for your cam see if you can find its manual
they have a lot of how two's in them

---

### Post by anewguy on 2010-01-24
You should also try, if you haven't already, loading the package for digicam and running it.  Sometimes it recognizes some off-normal cameras, as I think it has partial flat-photo driver support.

Please post back the output of the lsusb command - we need to start there to try to find a solution.  Please note that a search of the web via Yahoo, Google and Bing doesn't return much hope, but we may be able to get this going anyway - just post back the output we need.

dave :)

---

### Post by kayakfisher on 2010-11-27
Just had a need to connect my old DXG-308 camera to my Linux box and nothing.
Tried the "sudo lsusb" code and it returned:
Bus 003 Device 003: ID 1c4f:0002 SiGma Micro 
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 0d64:0108 DXG Technology Corp. Dual Mode Digital Camera
Bus 001 Device 011: ID 04a9:173a Canon, Inc. 
Bus 001 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So now what do I do with this?
In the mean time I think I will search for Picasa as also suggested.

---

### Post by no2498 on 2010-11-27
i just put this in google and got a lot of hits


ID 0d64:0108 DXG Technology Corp. Dual Mode Digital Camera


you should find something that helps

---

