---
title: "ATI Radeon X1250 Configuration &amp; TV / S-Video out on Acer Extensa 4420"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-03-02
Hi Guys

Sorry, stupid, ill-informed, confused user here. Having some trouble enabling the S-Video / TV out on my ATI Radeon x1250 card on my Acer Extensa Laptop.

Tried a bunch of fixes I found listed in Ubuntu forums online, but all of them have kind of screwed me over to the extent that I could not bring up the usual Ubuntu desktop anymore, and the computer would only log into a prompt. Even the fixes I tried for this issue to restore the configuration didnt work, so I just reformatted.

I tried downloading ATI Catalyst Control Centre which basically told me that my card is not an ATI card. But of course the damn thing is because Ubuntu reads it as an ATI card, and so does Windows.

Here are the packages I have installed that are related to ATI, and in my process of attempting various fixes, I obviously might have a lot of crap that I do not need:

atitvout - ATI TV Out Support Program
xserver-xorg-video-ati X.Org X server -- ATI display driver wrapper
xserver-xorg-video-radeon X.Org X server -- ATI Radeon display driver
fglrx-kernel-source Kernel module source for the ATI graphics accelerators
xorg-driver-fglrx Video driver for the ATI graphics accelerators
radeontool utility to control ATI Radeon backlight functions on laptops
xserver-xorg-video-mach64 X.Org X server -- ATI Mach64 display driver
xserver-xorg-video-r128 X.Org X server -- ATI r128 display driver
fglrx-modaliases Identifiers supported by the ATI graphics driver

Can some generous soul please advise me which packages I need and which I can safely get rid off?

Then can someone please help me get my TV out working? I hate having to boot up in windows everytime I want to watch something off my computer on a TV.

---

### Post by 3rdalbum on 2010-03-02
You probably don't need anything related to fglrx. That's ATI's proprietary driver. ATI does not support the X1250 anymore on Linux, which is why the Catalyst control center told you that it wouldn't work with your card.

Usually for TV-out, you start up the computer with the S-Video plugged in and the TV turned on. Well, at least, that's how it's always worked for me. Sorry I can't be of more help.

---

### Post by seventhsamurai on 2010-03-02
Got rid of all the fglx stuff.

Tried the whole startup with the TV hooked thingy. No luck there.

---

### Post by Mark Phelps on 2010-03-02
Don't know how you got rid of the fglrx stuff, but the linked pages have some details on how to replace that with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by seventhsamurai on 2010-03-02
Hi Mark

I tried to follow the instructions on the page you suggested. But when I get to the point where it asks you to configure X.org, I dont seem to have an existing Xorg.conf file. When I key in the code 
sudo nano /etc/X11/xorg.conf

all I get is a blank file to type into. I checked the etc/X11 folder and there is no xorg.conf file.

---

### Post by thedomed on 2010-03-02
Hi I am having a similar problem with an X1300 
I found a way to get an xorg.conf file by restarting in recovery mode and selecting drop(i can't remember the rest, it was bottom of the list)
and typing in 
Xorg -configure 
This gave me an xorg.conf.new in root
then restarting as normal and copying root/xorg.conf.new into etc/xorg.conf

Though I don't think this is a solution.

I then tried the help at
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but became stuck at 
Driver specifies which driver you want to use. IT HAS TO BE ati and NOT radeon or fglrx

because my xorg.conf tells me that my driver is "radeon" but i don't know how to change this.
Any ideas?

---

### Post by seventhsamurai on 2010-03-02
Really shocks me why it is so difficult to this working on Ubuntu when everything else works just fine.

---

### Post by tom.swartz07 on 2010-03-02
> **seventhsamurai said:**
> Really shocks me why it is so difficult to this working on Ubuntu when everything else works just fine.

Yeah, its redic. I have almost the same card- mines a Radeon X1270 and I was in the same boat. ATI is whats causing the problems; Ubuntu and the community has no control over it, as the drivers and interfaces are proprietary and cant be tweaked too much.

Unfortunately, it seems that the s-video port is DOA in linux. 

BUT! There is a workaround! 

The best way that I have found is to use a device called a Scan Converter. [http://www.amazon.com/VideoSecu-VGA2TV-Computor-Presentation-Converter/dp/B000X3FAJU/ref=sr_1_1?ie=UTF8&s=electronics&qid=1267591138&sr=8-1](http://www.amazon.com/VideoSecu-VGA2TV-Computor-Presentation-Converter/dp/B000X3FAJU/ref=sr_1_1?ie=UTF8&s=electronics&qid=1267591138&sr=8-1)

It's only $18USD, and its rather small, about the size of an Altoids tin.

You plug in the VGA out on your computer and you can then run whatever cable you want to the tv- the model in the link is exactly the one I have and it has RCA video out, S-Video, and VGA out also.

If you just want to casually hook up a computer to a tv- or even use a tv as a second monitor (thats what i do! :D ) this would be a great bet. Its even small enough to toss in a laptop bag when youre on the run.

---

### Post by seventhsamurai on 2010-03-03
Thank you all for your inputs. Fortunately for now, I have a nice TV with a USB port which enables me to watch Divx movies off a flash drive. So the need isn't pressing. Just frustrated that I couldn't get it to work.

---

### Post by Mark Phelps on 2010-03-03
> **seventhsamurai said:**
> Really shocks me why it is so difficult to this working on Ubuntu when everything else works just fine.

Probably because the problems are NOT due to Ubuntu, but rather, to ATI abandoning the Linux community folks who made the mistake of purchasing their "legacy" cards (like me).

The Phoronix forum is reporting that AMD keeps releasing more and more of its video driver specs, allowing the open source community to enhance the open source drivers as a result.  But without the details, I would guess these specs are for the newer HD 3x/4x/5x series.  So those of use with the "legacy" cards will most probably see little or no improvement.

---

### Post by seventhsamurai on 2010-03-03
Good to know. Next time I buy a computer, I'll make sure it's not one with an ATI card.

---

### Post by waynefoutz on 2010-03-22
I have this card as well. If you don't mind rolling back to Hardy Heron, (8.04) Catalyst version 9.3 works fantastic with that card. 

Here is the 32 bit driver:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English")

This driver was the last one that supported this card. Unfortunately, it will not work with Jaunty or Karmic. The last version of Ubuntu it worked with was Intrepid. 

If you want to try another distro, check Distrowatch [http://distrowatch.com/]("http://distrowatch.com/") and check out other distros. Any one that has xorg-server version 1.5.2 or lower will work with the Catalyst 9.3 driver.

I've settled on Karmic for now. I was running intrepid, when jaunty came around it broke everything and I ended up rolling back to intrepid. The open source drivers are better now, but no where near as good as they were with Catalyst. About 90% of everything works. With Catalyst and Intrepid, it ran perfect. Unfortunately, Intrepid reaches end of life next month, but Hardy has another year.

---

### Post by CvdW on 2010-05-30
I have been struggling for the last week to get dual-monitors working on my ATI Radeon x1900 card. I have searched high and low for any clue why the secondary monitor simply refuses to power up. X thinks it is there and active but I can't for the life of me get it to actually power up. It works fine until X starts and then it just powers off. It works fine in Windows XP. It is really frustrating.
In the process of this I have learnt a lot though and it basically boils down to this - **STAY AS FAR AWAY FROM ATI AS YOU POSSIBLY CAN**.
ATI/AMD have shafted their customers badly by abandoning their "legacy" products. Did you know that they aren't even releasing Windows 7 drivers for these "legacy" products? "Legacy" my *** - my x1900 is almost brand new.

I will never buy another ATI or AMD product again and I will make sure that I spread the word to everyone I know about this fiasco.

Thankfully the Linux community will eventually fix the drivers - ZERO thanks for ATI.

---

### Post by sturmey on 2010-07-08
> **Mark Phelps said:**
> Probably because the problems are NOT due to Ubuntu, but rather, to ATI abandoning the Linux community folks who made the mistake of purchasing their "legacy" cards (like me).

Actually we can blame the coders that claim that the Radeon drivers are working with s-video out. It's clear that no testing was done to verify that the s-video works, but they put a check mark into the box on the wiki and hope that nobody actually wants to use that function.

I'm disappointed with the way linux and especially Ubuntu has progressed. Instead of making things easier it's getting harder and harder to get simple crap to work.

I would probably have better luck getting Windows 98 to do s-video out and it's 12 years old than to get Linux to do it.

---

### Post by Zoharc on 2010-07-16
I have that same model (acer extenza), with radeon x1250. Naturally, I am having issues with s-video too. However, using the default Monitor application, I was able to enable dual-screen, with screen expansion and clone, through s-video. 

The main issues occur when changing resolutions on alternate screen, but usually reverting and attempting again several times eventually works -- apart from the once or twice i lost both screens entirely, but removing the svideo cable and reloading the server usually works.

---

### Post by LowSky on 2010-07-16
> **CvdW said:**
> I have been struggling for the last week to get dual-monitors working on my ATI Radeon x1900 card. I have searched high and low for any clue why the secondary monitor simply refuses to power up. X thinks it is there and active but I can't for the life of me get it to actually power up. It works fine until X starts and then it just powers off. It works fine in Windows XP. It is really frustrating.
In the process of this I have learnt a lot though and it basically boils down to this - **STAY AS FAR AWAY FROM ATI AS YOU POSSIBLY CAN**.
ATI/AMD have shafted their customers badly by abandoning their "legacy" products. Did you know that they aren't even releasing Windows 7 drivers for these "legacy" products? "Legacy" my *** - my x1900 is almost brand new.

I will never buy another ATI or AMD product again and I will make sure that I spread the word to everyone I know about this fiasco.

Thankfully the Linux community will eventually fix the drivers - ZERO thanks for ATI.

I don't blame ATI or AMD for "shafting" customers. I look at it this way. AMD is a business. A business that has to stay competitive, and by doing so has to drop support for older products so they can divert resources to more competitive projects. No matter how new you may think they are.

> **sturmey said:**
> 
I'm disappointed with the way linux and especially Ubuntu has progressed. Instead of making things easier it's getting harder and harder to get simple crap to work.

I would probably have better luck getting Windows 98 to do s-video out and it's 12 years old than to get Linux to do it.

Stop living in the past. There is no need to support 12 year old hardware, for 99.9 % of the people. Most people don't even use S-Video any more. We have all moved on to HDMI, VGA and/or DVI.

I get people want to get the most out of the things they buy, but to complain that the world has moved on to better more capable equipment and discontinued support on legacy parts is laughable. You don't have to upgrade to a newer version of Linux, you can still use a version that supported your equipment. Find an 7.04 disk and install that if you really need it to work.

Your complaining about a free operating system that allows people to make changes. If you don't like something, change it, fix it,  buy parts that work and will work, or move on.

---

### Post by Zoharc on 2010-07-27
I am using ATI legacy (X1250 Radeon mobile) and I have had a working dual screen using the community supported drivers on Ubuntu 10.04. I have noticed that the Monitor Preferences will not respond while any desktop effects, or compiz, is enabled. 


You can set compiz back up (but it will only work on cloned view),

---

