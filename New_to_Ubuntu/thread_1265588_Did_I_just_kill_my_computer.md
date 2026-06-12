---
title: "Did I just kill my computer?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by maxbox51 on 2009-09-13
Um...I was trying to get past grub error 21, which I believe means a disk was not being found.  However, things went from bad to worse to...dead?  In brief, pushing the power button no longer causes anything to happen.  :(  What I'd like to know is, how can I find out what I need to fix:  the power supply, the motherboard, or just some connection somewhere?

Some details:  I have a custom-built tower with a slot 1 motherboard, a 350 Mhz pentium II, almost a Gig of memory, and the Award BIOS.  This was built for me, but not by me; I'm not a hardware guy.  There are two disks and an ATAPI CD-ROM attached through the IDE ports.  I successfully used Windows 98 until 2003, then limped along on XP on this machine until yesterday.  I was hoping to turn it back into something useful by installing ubuntu on it.

After some fiddling with the BIOS and boot options, I was able to use ubuntu off of the live CD, and have been trying to move on to installing.  I completed the installation process, making both disks (one is < 20 Gb, the other about 80?) into ext4 file systems.  I assigned the 80 Gb drive to be / and the 20 Gb drive to be /usr (not necessarily a great choice, but that's what I did).  However, it wouldn't boot from the disk; I kept getting grub error 21, which apparently means it can't find a disk.

There was clearly some kind of problem with the configuration, because the BIOS HDD auto detect would detect the primary master, but would hang when trying to detect the primary slave; the CD-R was recognized correctly.  (XP was able to find all the disks the way it was set up, so it wasn't that anything was broken, just not quite correctly described in/by the BIOS to grub.)

Looking inside the tower, the two disk drives were connected to the same cable and IDE port; those must have been the primary master (20 Gb) and primary slave (80 Gb).  The CD-R was attached to the other IDE port.  So there was a problem recognizing the 80 Gb drive.  I reconnected the 80 Gb drive to the same IDE port/cable as the CD-R, and verified the CD-R was set to be a slave (it was the whole time; don't know why I didn't have trouble finding it before).  In the process I had to move the CD-R down a few bays to get the ribbon cable to reach it, and I ended up needing to disconnect all three peripherals to do it.  I also checked the jumpers on the 80 Gb drive, which appeared to have been configured as a slave (as it should have been)--so I moved the jumper to indicate it would now be the master of the secondary IDE bus.

At this point I tried it again.  The two devices on the secondary IDE bus were recognized, but now the primary master wasn't being recognized.  So I switched the secondary and primary cables to connect to the opposite ports and tried again.  Neither disk nor the CD-R were recognized.

It must be possible to connect an IDE cable to the motherboard port the wrong way around, because I noticed the ribbons came out of the connectors on opposite sides and I turned one around so they wouldn't.  So I'm pretty sure I either killed my motherboard or shorted out my power supply by hooking up the IDE connector(s) backwards.

At any rate, now the power button does nothing; I can't get the computer to do anything at all.

What is likely to be salvageable?

---

### Post by mapes12 on 2009-09-13
> **maxbox51 said:**
> Um...I was trying to get past grub error 21, which I believe means a disk was not being found.  However, things went from bad to worse to...dead?  In brief, pushing the power button no longer causes anything to happen.  :(  What I'd like to know is, how can I find out what I need to fix:  the power supply, the motherboard, or just some connection somewhere?

Some details:  I have a custom-built tower with a slot 1 motherboard, a 350 Mhz pentium II, almost a Gig of memory, and the Award BIOS.  This was built for me, but not by me; I'm not a hardware guy.  There are two disks and an ATAPI CD-ROM attached through the IDE ports.  I successfully used Windows 98 until 2003, then limped along on XP on this machine until yesterday.  I was hoping to turn it back into something useful by installing ubuntu on it.

After some fiddling with the BIOS and boot options, I was able to use ubuntu off of the live CD, and have been trying to move on to installing.  I completed the installation process, making both disks (one is < 20 Gb, the other about 80?) into ext4 file systems.  I assigned the 80 Gb drive to be / and the 20 Gb drive to be /usr (not necessarily a great choice, but that's what I did).  However, it wouldn't boot from the disk; I kept getting grub error 21, which apparently means it can't find a disk.

There was clearly some kind of problem with the configuration, because the BIOS HDD auto detect would detect the primary master, but would hang when trying to detect the primary slave; the CD-R was recognized correctly.  (XP was able to find all the disks the way it was set up, so it wasn't that anything was broken, just not quite correctly described in/by the BIOS to grub.)

Looking inside the tower, the two disk drives were connected to the same cable and IDE port; those must have been the primary master (20 Gb) and primary slave (80 Gb).  The CD-R was attached to the other IDE port.  So there was a problem recognizing the 80 Gb drive.  I reconnected the 80 Gb drive to the same IDE port/cable as the CD-R, and verified the CD-R was set to be a slave (it was the whole time; don't know why I didn't have trouble finding it before).  In the process I had to move the CD-R down a few bays to get the ribbon cable to reach it, and I ended up needing to disconnect all three peripherals to do it.  I also checked the jumpers on the 80 Gb drive, which appeared to have been configured as a slave (as it should have been)--so I moved the jumper to indicate it would now be the master of the secondary IDE bus.

At this point I tried it again.  The two devices on the secondary IDE bus were recognized, but now the primary master wasn't being recognized.  So I switched the secondary and primary cables to connect to the opposite ports and tried again.  Neither disk nor the CD-R were recognized.

It must be possible to connect an IDE cable to the motherboard port the wrong way around, because I noticed the ribbons came out of the connectors on opposite sides and I turned one around so they wouldn't.  So I'm pretty sure I either killed my motherboard or shorted out my power supply by hooking up the IDE connector(s) backwards.

At any rate, now the power button does nothing; I can't get the computer to do anything at all.

What is likely to be salvageable?Hi

This is a hardware issue which, whilst we will try to help, is not the place to post.

I can only comment from my own experience. If you have tried hot swapping any of those drives without powering down and unplugging then I think your motherboard has been killed. The drives themselves should be salvigable.

Mark

---

### Post by NoaHall on 2009-09-13
Try removing your ram and plugging them in one at a time until it boots. If this fails, remove everything, if you have a jumper cap, put it on the special "cmos clr" pins, or remove the battery, and add the ram on at a time.

---

### Post by maxbox51 on 2009-09-13
> **mapes12 said:**
> Hi

This is a hardware issue which, whilst we will try to help, is not the place to post.

I can only comment from my own experience. If you have tried hot swapping any of those drives without powering down and unplugging then I think your motherboard has been killed. The drives themselves should be salvigable.

Mark

Agreed, and if there is a policy against posting hardware issues that come up during attempts to install ubuntu in this forum, please let me know--and let me know how I can remove the thread.  

I haven't done anything inside the case with the power on, however in the past I have been told that leaving the machine plugged in while working inside grounds the chassis, so I always leave it plugged in while working inside.

I'm not expecting very much help.  As I see it I either need a new power supply, a new slot 1 motherboard, or both, and as this was an attempt to get an old computer to be useful again, I'm more likely to just abandon the project.

---

### Post by NoaHall on 2009-09-13
Do what I suggested. I expect that you have either disconnected the power button cable from the motherboard, or your RAM is no longer working.

---

### Post by gordintoronto on 2009-09-13
> **maxbox51 said:**
> Um...I was trying to get past grub error 21, which I believe means a disk was not being found.  However, things went from bad to worse to...dead? ...

What is likely to be salvageable?

Everything, assuming you turned off the power while you moved cables around?

There's a chance the power supply died along the way.  Do people ever put old computers on the curb where you live?  That's where I sometimes find power supplies.

More likely, while moving the other cables around, you accidentally disconnected the cable from your power button, where it plugs into your motherboard.

One tip: before doing anything inside the case, touch a piece of bare metal in the case, which should get rid of any static electricity you have built up.  If there was a "snap" of static electricity discharging at some point in what you did, there might be damage to any part of your system.

If it's dead, it's not a huge loss.  In Toronto, there are several places where one can buy a much better system than your (1998?) old one, for well under $100.  I assume that is also true in most cities.

BTW, if I were setting up that configuration, I would set the small drive as primary master and gparted it to be root, and set the other drive to be secondary master, as /home.  And the CD-ROM, I would set to be primary slave, since I would mostly copy data from /home to it.

---

### Post by theozzlives on 2009-09-13
I had that problem, but the HD was to big for the BIOS and GRUB to get along, even though the BIOS detected the drive properly.

I setup a 10 GB /, a 512 MB swap and the rest /home and it booted ok. I'd suggest you make your partitions like that (swap will depend on RAM) on the 80 GB, and make it master. The 20 GB can be slave and hold misc BS as now days 20 GB isn't big enough to hold much.

EDIT: Why would you invest in RAM without giving your drives a second thought?

---

### Post by maxbox51 on 2009-09-13
> **NoaHall said:**
> Do what I suggested. I expect that you have either disconnected the power button cable from the motherboard, or your RAM is no longer working.

Thanks.  I'm not sure why you're concerned about the RAM; is it one of the more sensitive parts?  I suppose it's closely connected to the disks via DMA, so it's reasonable.  I'll be doing something else the rest of today, though.

---

### Post by Mariane on 2009-09-13
The hard disk sounds likely to be OK, so you should be able to get your data back by plugging this into another computer. 

Apart from that I don't know. Best of luck. 

Mariane

---

### Post by NoaHall on 2009-09-13
Because when it won't power on, it's usually a RAM error. Or a disconnected wire.

---

### Post by maxbox51 on 2009-09-13
> **gordintoronto said:**
> Everything, assuming you turned off the power while you moved cables around?

There's a chance the power supply died along the way.  Do people ever put old computers on the curb where you live?  That's where I sometimes find power supplies.

More likely, while moving the other cables around, you accidentally disconnected the cable from your power button, where it plugs into your motherboard.

One tip: before doing anything inside the case, touch a piece of bare metal in the case, which should get rid of any static electricity you have built up.  If there was a "snap" of static electricity discharging at some point in what you did, there might be damage to any part of your system.

If it's dead, it's not a huge loss.  In Toronto, there are several places where one can buy a much better system than your (1998?) old one, for well under $100.  I assume that is also true in most cities.

BTW, if I were setting up that configuration, I would set the small drive as primary master and gparted it to be root, and set the other drive to be secondary master, as /home.  And the CD-ROM, I would set to be primary slave, since I would mostly copy data from /home to it.

Thanks.  I need a wireless card for it anyway, maybe I can find a deal on something better, quieter (it's a BIG empty tower with two noisy fans), and with a wireless card in it.

I tried to find the other end of the power button wires, without much luck.  I'm also going to try some of the other suggestions here before moving it to the curb.  :)

---

### Post by stderr on 2009-09-13
Hmm you can't normally rig up IDE cables the wrong way round due to a tiny plastic notch on one side of them. Maybe these didn't have the notch?

I really wouldn't have expected that to cause so much havoc though. As others have said, just make sure all the correct cables are in - trace back the power button wires, trace the leads eminating from the PSU (important one is ATX power to the motherboard). 

You may also want to test your PSU  - take it out and entirely disconnect it from your system, use the paperclip trick to get it running, rig up a voltmeter and check the voltages you're getting from the molex connectors to verify it's working. (You can find step-by-step guides for this online by searching for things like "psu voltmeter molex" and "psu paperclip"). Just be careful - you are dealing with a power supply rigged to the mains! And **make sure** the voltmeter is set to read **voltage**, NOT current.

If your PSU is outputting solid voltages on the important rails (molex: yellow is 12v, red is 5v, black is ground), and everything's hooked up OK, then your motherboard has probably taken a dive! I would have thought you should be seeing/hearing some signs of life if just your RAM, gfx card, HDD etc took a hit.

edit: The paperclip trick gets a PSU running when it's disconnected from a computer. (PSUs won't run without having the ATX connector plugged into a motherboard). You remove power from the PSU, and stick a bent paperclip (or other conductive thing) into the hole with the green wire (there should only be one - if there is more than one or no green wire, check a pinout for your PSU), and stick the other end into any hole a black wire goes to. That 'simulates' a connection to a motherboard.

Checking voltages with a voltmeter then entails connecting the PSU to the mains, getting it going, and setting the voltmeter to measure _VOLTAGE_, and sticking one lead into a hole in a molex connector where a black wire goes into, and the other into a hole in the same molex connector where a red wire goes into (voltmeter should read close to 5v), then removing the one in the red wire and connecting it to the yellow (should read close to 12v). 

Check some guides with photos first though, and make sure you're happy you know what you're doing! Be careful.

---

### Post by maxbox51 on 2009-09-13
> **theozzlives said:**
> I had that problem, but the HD was to big for the BIOS and GRUB to get along, even though the BIOS detected the drive properly.

I setup a 10 GB /, a 512 MB swap and the rest /home and it booted ok. I'd suggest you make your partitions like that (swap will depend on RAM) on the 80 GB, and make it master. The 20 GB can be slave and hold misc BS as now days 20 GB isn't big enough to hold much.

EDIT: Why would you invest in RAM without giving your drives a second thought?

Do you mean why would I have nearly 1 Gb RAM with such small disks?  There are reasons.  The human genome is < 4 Gb of read-only data; it's a lot easier to work with in 1 Gb RAM, but it will only ever take up < 4 Gb on disk.  Statistical analysis packages like R can also eat gobs of RAM.

Besides which, who says I didn't give my drives a second thought?
The machine started out with just the 20 Gb disk, I expanded it to 100 Gb around 2003.  In 2006 I bought another computer instead of upgrading this one further.  I had to move this one recently, so I thought I'd try to get it functional again.  Windows XP now expects too much of it to be usable.

I installed ubuntu twice with the same result.  The first time I accidentally installed it as dual-boot, with XP on the 20 Gb and / and /home in two partitions on the 80 Gb (reusing partitions that were already there for XP), the second time as described.  I got error 21 both times.  I don't think I can rule out what you're suggesting, though.

I regretted the partition assignments I made the second time, so when I try again I'll do something more like what you've suggested.

---

### Post by maxbox51 on 2009-09-13
> **stderr said:**
> Hmm you can't normally rig up IDE cables the wrong way round due to a tiny plastic notch on one side of them. Maybe these didn't have the notch?

I really wouldn't have expected that to cause so much havoc though. As others have said, just make sure all the correct cables are in - trace back the power button wires, trace the leads eminating from the PSU (important one is ATX power to the motherboard). 

You may also want to test your PSU  - take it out and entirely disconnect it from your system, use the paperclip trick to get it running, rig up a voltmeter and check the voltages you're getting from the molex connectors to verify it's working. (You can find step-by-step guides for this online by searching for things like "psu voltmeter molex" and "psu paperclip"). Just be careful - you are dealing with a power supply rigged to the mains! And **make sure** the voltmeter is set to read **voltage**, NOT current.

If your PSU is outputting solid voltages on the important rails (molex: yellow is 12v, red is 5v, black is ground), and everything's hooked up OK, then your motherboard has probably taken a dive! I would have thought you should be seeing/hearing some signs of life if just your RAM, gfx card, HDD etc took a hit.

Thanks...testing the PSU is a good idea.  I have a voltmeter, but I wouldn't recommend letting me use it on your stuff!

I truly get no signs of life when pushing the power button, it acts _exactly_ like the button is disconnected.  I'll try again to wade into the teeming mass of wires into which those disappear (most of which, I think, are loops of a far smaller number of wires, many of which are not actually in use in this box; there are waaay too many wires in this box for the hardware that is actually installed).

---

### Post by Whiffle on 2009-09-13
I had a similar problem the other day on my server.  In case you haven't already, unplug and replug all the power cables to the motherboard.

---

### Post by zerhacke on 2009-09-13
> **NoaHall said:**
> Because when it won't power on, it's usually a RAM error. Or a disconnected wire.

You can power on a computer with bad RAM or no RAM at all.  Ever hear of BIOS beep codes?

---

### Post by NoaHall on 2009-09-13
Not on every motherboard. On quite a few, they won't.

---

### Post by SaaTeeVaaGreen on 2009-09-13
so when you press the power button you are getting no response at all? the pc doesnt even perform the POST? seems terminal, but when this happened to me i eventually found a very simple solution!dont know if you have tried this yet, but it could very easily be simply a dead motherboard battery. have you tried replacing that?

---

### Post by zerhacke on 2009-09-13
> **NoaHall said:**
> Not on every motherboard. On quite a few, they won't.

I take it you can name them, then.

---

### Post by stderr on 2009-09-13
Hehe I know what you mean about the masses of wires. I have an old slot 1 box lying around here myself, haven't played around with it for a while though. I just opened it up for the heck of it, and indeed, the tiny IDE cables don't have any notches on the sides! There's a hole for a notch on the connector on the motherboard, but none on the damn cables. 

I wouldn't be too put off about testing the PSU yourself. I was never any great shakes at electronics, but if you find a good pictorial guide, it puts you at your ease a bit more. So long as you're careful, do some reading beforehand, and don't rush things, you'll probably find it a walk in the park. It's one of those "oh, I didn't realise it'd be so easy" things.

It's just I have to constantly say "be careful" because we're dealing with mains power... although if you follow a guide closely, you're never at any actual risk, and by disconnecting the PSU from the PC, the most you're ultimately risking is the fuse in the voltmeter, the PSU, and possibly the mains fuse - but that's all really worst case scenarios. Up to you though :)

---

### Post by NoaHall on 2009-09-13
> **zerhacke said:**
> I take it you can name them, then.

On several Gigabyte motherboards, there's no such thing. They tend just to sit there. I know mine is like that, and 6 or 7 others I've come across haven't had such things.

@stderr 

Some motherboards won't boot without ram. The older ones, anyway.

---

### Post by stderr on 2009-09-13
> **zerhacke said:**
> I take it you can name them, then.

I think he means the beeps. Quite a number of mobos don't have onboard speakers (certainly true for older mobos). But, you would typically still see some life from the PC anyway - fans should whirl up, that kind of thing.

---

### Post by maxbox51 on 2009-09-13
I think it's unlikely the battery died just then; the machine booted not ten minutes before.  The one thing that changed was I messed with the cables and positions of the disks and CD-ROM.  I have tried to follow the wires from the power button and failed; I will try again, though.

To confirm, the only thing that happens when I push the power button is the (spring-loaded, plastic) power button clicks.  There is no sign that the computer is an electrical device at all: no flickers of dummy lights, no recognition by the monitor that something is trying to connect to it, nothing.

---

### Post by NoaHall on 2009-09-13
Then connect the wires back up! You've probably pulled out the cable. Find your motherboard's manual and plug them up.

---

### Post by theozzlives on 2009-09-13
> **maxbox51 said:**
> Do you mean why would I have nearly 1 Gb RAM with such small disks?  There are reasons.  The human genome is < 4 Gb of read-only data; it's a lot easier to work with in 1 Gb RAM, but it will only ever take up < 4 Gb on disk.  Statistical analysis packages like R can also eat gobs of RAM.

Besides which, who says I didn't give my drives a second thought?
The machine started out with just the 20 Gb disk, I expanded it to 100 Gb around 2003.  In 2006 I bought another computer instead of upgrading this one further.  I had to move this one recently, so I thought I'd try to get it functional again.  Windows XP now expects too much of it to be usable.

I installed ubuntu twice with the same result.  The first time I accidentally installed it as dual-boot, with XP on the 20 Gb and / and /home in two partitions on the 80 Gb (reusing partitions that were already there for XP), the second time as described.  I got error 21 both times.  I don't think I can rule out what you're suggesting, though.

I regretted the partition assignments I made the second time, so when I try again I'll do something more like what you've suggested.

I your case, that may make sense. Most people here store movies, music, and virtual disks (including me) so as you see disk space is important.

My first experiance with Ubuntu was Gutsy on an old Compaq 400 MHz with 256 MB RAM and a 35 GB HD. When I had my problem was when I put a 160 GB into a 500 MHz Celeron with 256 (max) MB RAM. I always got error 21 unless I split my partitions and root was small (you don't need more than 10 GB if you have a separate /home).

BTW: error 21 just basically means GRUB can't find the files to boot.

EDIT: With 1 GB RAM you really don't need swap unless you hibernate.

---

### Post by oldfred on 2009-09-13
My system died a few months ago. I heard a pop one night & I was sure it was from the computer but it kept working. Next morning it was total dead. MB had no speaker, system seemed like I had no power. I kinder wanted better power supply anyway but that was not the problem.

It turned out that the capacitors on the video card blew. (7600gts) and I found on the Internet photos that looked just like my card with the ends of the caps open. New video card and everything worked just fine.

One more thing to check. But always check that all connections are tight. Once I thought I had the power cord in, but in moving computer it came out just enough to not work. Check & double check connections.

---

### Post by maxbox51 on 2009-09-13
Thanks, everyone.  I moved the computer to where I could watch a football game and fiddle, and now the power button won't turn the computer OFF.  However, it still won't say anything to the display.

At this point I'm giving up on this box.  As someone pointed out, I can probably get a better old computer for under $100, and as there are some capabilities I want that this box doesn't have even at its best (USB 2.0, wireless B/G, shorter than a desk, weighs less than a jockey) I've disassembled this one in the hope that I may be able to reuse some of the components in the next one.

Feel free to keep giving me suggestions, though, especially about how to make an old Pentium II or III-based computer usable.  I've learned a lot today!

---

### Post by Mariane on 2009-09-13
> **oldfred said:**
> 
Check & double check connections.



Yes, and not only visually. Press them in manually, too. Earlier on today I started trying to remember how you type a "mount" command because my external hard disk was not automatically detected by kde. It turned out kde was not at fault, the usb lead was plugged into the hard disk but not deep enough. 

Mariane

---

### Post by stderr on 2009-09-13
> **maxbox51 said:**
> Feel free to keep giving me suggestions, though, especially about how to make an old Pentium II or III-based computer usable.

*Personally*, I use my slot 1 box as a footrest. It's a nice upgrade from the old laptop I was using as a footrest before - slightly wider and a lot larger, so it gives a more appropriate height and surface area :-\"

Now for some proper suggestions ;)

WRT the power button, I sometimes find it easier when testing systems to disconnect the leads for the power button from the motherboard and use a conductive screwdriver or the like to connect the pins on the motherboard manually - creating my own switch, per se. This way, you discount the possibility of a problem with the switch. To shutdown, depending on BIOS settings, you usually hold for > 4 seconds. On the other hand, this could be construed as a bit of a pain in the backside...

---

