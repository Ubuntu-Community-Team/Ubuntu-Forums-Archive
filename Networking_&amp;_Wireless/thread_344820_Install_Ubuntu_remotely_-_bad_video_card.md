---
title: "Install Ubuntu remotely - bad video card?"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by reberic on 2007-01-23
I'm trying to install Ubuntu 6.06 on a middle-aged PC that has previously run Ubuntu. Since then, there was a failed install attempt with another operating system, I think. 

I've been unsuccessful in reinstalling Ubuntu. Here are my problems: 

1) The bios appears to be skipping over the install CD. The CD has been successfully tested on my intel Mac Mini, so I don't think that's the problem. I have a Kubuntu install CD that I also know works. No luck with it either.

2) I can't access the bios because I can't get a signal from the computer to my monitor, which I've used before with this box. Monitor is a 19" Sceptre LCD. The PC has two VGA ports. One on the motherboard and a video card, which I think is a GeForce 440 or something like that. I've reseated the video card, checked cables, etc. 

I now have the PC connected to my Netgear router via an ethernet cable. My Mac Mini is also connected to the router. 

Any way I can try to do the install or fix the bios remotely from the Mac? 

My end goal with this box is to turn it into a simple Ubuntu server for home. 

Thanks for any help, suggestions or ideas.

---

### Post by dannyboy79 on 2007-01-23
i can tell ya that you can't "fix" the bios from another machine but you can perform an install from another machine but it sounds like your computer isn't even booting up??? have you tried the video card in another pci slot or is it a agp card?? you can try to replace the cmos battery which will clear the bios back to factory settings which may or may not help. you need video on this box so you can tell it what to boot first. or you may be able to boot the box, wait a long time till you thinks it's up, then try an over network install. can't help you with that though! i would try other monitors also.

---

### Post by reberic on 2007-01-23
Thanks for the reply.

I did try the vid card in another slot. No luck there. 

Also replaced the battery. I can pull it out and reinstall. Do you have to leave it out for a few minutes? I thought I read that somewhere. Sounds odd.

---

### Post by dannyboy79 on 2007-01-23
here's a link to a guy who used the mx440 which had tv-out on it, and used that install ubuntu. basically once you get a display, you can make sure your bios is setup to boot to a cd first.

[http://www.ubuntuforums.org/archive/index.php/t-22045.html](http://www.ubuntuforums.org/archive/index.php/t-22045.html)

---

### Post by reberic on 2007-01-23
Thanks for the link.

I'm stuck there. Only have VGA out on the card and no television (weird, I know). 

After the network PC is powered on, is there any way to tell whether it's running? I don't see anything in my Network list on the Mac. Any other ways to tell?

---

### Post by dannyboy79 on 2007-01-23
your mac wouldn't be able to see it unless that computer was a samba server or a windows machine. it might show up in your router's config page where it shows attached devices. can you ping it? I would like to point out that once you install ubuntu onto it that's not gonna fix your video out problem! you might just have to make this machine a monitorless home server. you can install ssh on it to admin it, once you have ssh on it, you can then install nx server and then you can finally do remote desktop using nx client. that's what I have used and it's awesome. it actually uses the same port and ssh does, 22, and it's encrypted unlike normal remote desktop software. good luck. i just thought of something though, i don;t know how in the world you'll be able to push the software onto your computer???? the normal network is made for computers that don't have a cd-rom and it uses a cd-rom from the network, or it loads an iso image. you're attempting to push the software onto it? you gotta figure out the video out problem. something really when neither the onboard video as well as the pci video card doesn't work. do you hear any beeping when you turn your computer on? have you tried turning it on and waiting until it's completely on and then pluging in the monitor?? i think you may be sol. sorry to say this.

---

### Post by mips on 2007-01-23
You might be able to access the pc via the serial port. Many Unix like OS's have this option to pipe terminal output to the serial port. This should allow you to configure the LAN and do a install that way. Think i saw something like this in the SPARC forum.

Thats assuming the rest of the pc is fine.

---

### Post by mal on 2007-01-23
Have you tried removing the PCI graphics card and connecting the monitor to the motherboard vga connector?

Mal

---

### Post by reberic on 2007-01-23
Thanks again for the suggestions.

I think maybe the motherboard has kicked the bucket. No luck with other VGA options, etc.

Cheers,

Eric

---

### Post by reberic on 2007-01-24
Success! 

After some more web sleuthing and spelunking inside the case I learned how to manually flash the bios by shorting two teeny tiny little pins in there. 

So now I've got video, a configuarable bios and looks like I should be able to get this sucker running.

Now to start wading through the server setup. I think this part will be easier.

---

### Post by dannyboy79 on 2007-01-24
just curous, how could you flash the bios with no video output??? the normal process of flashing a bios on most all motherboards consists of booting a floppy disc that contains the flashing program along with the new bios???? Do you mean you maybe cleared the cmos by putting a jumper on 2 pins? some motherboards won't clear the cmos by just taking out the battery you have to sometimes actually take a jumper and move it so 2 pins are connected, then the cmos battery is what's used as the power and the bios gets put back to factory state. could you maybe explain for others if they have this issue. thanks

---

### Post by reberic on 2007-01-30
You're exactly right -- I used the wrong term. 

I cleared the CMOS with a jumper. In this case I have a three-pin dealie right by the battery. I use a little plastic/metal jumper. The default position for it is on pin 2 and 3 (this is different on other motherboards, I think). By removing it and putting it briefly on pins 1 and 2 it clears the BIOS settings. I put it back on pins 2 and 3 and restart. 

But my BIOS problems persist -- I can't get the settings to save. 

I created a DOS boot floppy, flashed the BIOS and installed the most up-to-date version from the manufacturer (Gigabyte - ga-7vkml) according to instructions from their site. 

(Here's a handy tutorial "How to flash BIOS the Ubuntu way" I found on the forums: [http://ubuntuforums.org/showthread.php?t=318789&highlight=the+ubuntu+way](http://ubuntuforums.org/showthread.php?t=318789&highlight=the+ubuntu+way))

BUT I still need to clear the CMOS every time I want to reboot the computer, which is  impractical. I've tried altering the BIOS settings but they just won't save. Suggestions?

I've also attempted to rule out problems such as drives, cables, etc.

Any ideas or workarounds?

---

### Post by dannyboy79 on 2007-01-31
yeah, that's what I figured hence why I wrote that in my previous post. (move jumper so it makes 2 pins connect to clear cmos)

they won't save most likely because you either have the cmos jumper in the wrong location (prevents saves from occuring) or your cmos battery is weak and should be replaced. or there is another jumper somewhere which is actiing like a guard from changes. or there is a password for your bios and you're not entering it? I don't know, just trying to brainstorm so you figure this out.

---

### Post by reberic on 2007-01-31
Good suggestions.

I replaced the battery with a new one. No changes there.

Jumper, according to the MB manual, is in the right place. I've tried it in both positions and without. It appears to be in the correct spot. Won't power on at all if it's in the "short" position. If jumper is removed it doesn't seem to make much of a difference. 

I don't see or know of any other jumper that could be affecting this. Nothing noted in the manual. It does have two jumpers on some audio pins, but according to the manual they're in the right place. 

Doesn't appear to be password protected, but I'll go through those BIOS settings again to make sure. Doesn't ask for a password. I'll double check and report back.

---

### Post by dannyboy79 on 2007-02-01
are you using the latest bios? or maybe try one just previous to the latest. you can get them from the motherboard manufacturers website most of the time.

---

### Post by reberic on 2007-02-01
Thanks again for your continued help, DB. 

Yep, using the latest bios version. I did as the MB mnf suggested and upgraded them in stages. 

Per your earlier question, no passwords are set on the bios. No other jumpers to be found. 

I've got 6.10 installed now. 

So here's how the computer now boots. 
1) Clear CMOS by shorting pins 1 & 2 (per MB mnf)
2) Return jumper to pins 2 & 3, the default operating position.
3) Connect VGA cable to VGA connection on MB (not video card)
4) Power on. 
5) Get checksum/GP?? (can't remember second part) error. 
6) Select F8 to get to setup
7) Select F2 and get to choose which device to boot from -- CD, Floppy, IDE-0, or network.
8) Screen goes dark so I ...
9) Switch VGA cable to the video card connection
10) Everything operates normally.

---

