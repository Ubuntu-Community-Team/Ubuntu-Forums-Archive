---
title: "building a machine for ubuntu"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by X pensive windows on 2009-09-09
[SIZE=2]Hey all.

I'm new to Ubuntu. Using 9.04. About a month in now and loving it for all the obvious reasons. I couldn't have gotten off the ground without the help I found here on this site, so thanks for that first of all.[/SIZE]

[SIZE=2]I'm going to be building another computer to be used solely for internet browsing and as a jukebox to playback a media library.

Working backwards from that, what would be the most reliable, most supported and most economically sensible components to use? Keep in mind, no gaming or any other high demand activities will need to be accomplished on this machine.

Thanks in advance for any help.

Cheers.
[/SIZE]

---

### Post by Darkwing-Duck on 2009-09-09
I did something of this sort when I did a *nix only computer. I went online and found a basic barebones system from a place like tigerdirect or newegg and went from there. For the non highend stuff most of what you get will be supported. If you want to make sure before you buy (or build) your system take a note of what hardware you want to get for it and go to the [LaunchPad Supported Hardware List]("http://https://blueprints.launchpad.net/ubuntu/+spec/supported-hardware-list"). 
 
If you have any other questions please let us know! Good luck with it.

---

### Post by halitech on 2009-09-09
I'd be looking at something like this (not sure where you are but its an idea)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4195811&CatId=336](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4195811&CatId=336)

I'd add an Nvidia video card instead of using the onboard intel video and maybe a better PSU but otherwise, seems like a good deal for the buck.

---

### Post by imjafo on 2009-09-09
I bought on of those Systemax units about 4 months ago. The very same one you linked to. I added an Nvidia 9400 GT to it. They come with a Seasonic 350 Watt power supply, which handles the Nvidia card pretty good (requires 300 watt psu). It has an Asus P5KPL-CM motherboard, Intel socket 775 CPU. I also added 2 80mm fans one above and one below the HDD for extra cooling, pointing to the back of the case. It has preformed flawlessly. I ordered directly from Systemax and got the unit in 5 days. It is a pure ubuntu machine. It works with 8.04 and 9.04 with no problems and all hardware was recognized from the start, even the onboard Intel graphics. Systemax has distribution centers all over the world as well, so it is possible to get that system pretty much anywhere. By the way, systemax owns tiger direct. I would suggest going to their web site to look at their offerings. I have no complaints or regrets about this unit.
Edit: they also have AMD based units as well with no OS if you refer AMD. It has 3G of ram, versus the Intel with 4G of ram.

---

### Post by tuxxy on 2009-09-09
nvidia for the video card without doubt.

---

### Post by X pensive windows on 2009-09-09
[SIZE=2]Wonderly, your link doesn't work for me. I'll see if I can hunt it down. A supported hardware list seems exactly like the resource I'm looking for, but I'm still pretty green when it comes to launchpad and most of the other support avenues. I've been drenched in Windows all my life and I'm still drying off.:)

imjafo, thanks for the detail. Thanks to everyone for the links and ideas. 

The help is really appreciated. Keep it coming.

Cheers:guitar:
[/SIZE]

---

### Post by earthpigg on 2009-09-09
> I'm going to be building another computer to be used solely for internet browsing and as a jukebox to playback a media library.

assuming the media library already exists on an external hard drive or something, 32gb SSD as your primary hard drive. enjoy 10 second boot times.

2gb of ram. i would recommend 1gb, but ram is so damn cheap you may as well get 2 or more the days of 'if you can only afford one upgrade, get more ram' are gone because ram is so cheap, but more still doesn't hurt and - as i said - its freaking cheap..

take your pick of any video card listed as completely compatible with 9.04 [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport") ... go sale hunting. don't go insanely crazy cheap, and you will be fine.

extend the life of the ssd: no swap partition. 2gb of ram will be plenty given the uses you listed.

skip the optical drive. those are for proprietary non-free fascist-ware. skip the floppy drive. consider getting an SD/etc card reader.

make sure the case has a usb port or two in front.

any modern dual core CPU will be fine. take your pick. usually you build the computer around the CPU and motherboard... so, tell us what motherboard/CPU you are looking at, and we can get more specific.

when it comes to cpu, dont forget this often overlooked factor: *external speed* aka *front side bus*? how fast the CPU talks to the rest of the computer.

done, and done.

---

