---
title: "Installing Hardy on older pc - unresponsive monitor"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by japhyr on 2009-01-28
I am playing with a computer that was given to me, trying to install ubuntu.  The computer is a micronpc and it had windows 98 on it, but I believe it has 1G of RAM.  The windows os was wiped before it was given to me; I'm not sure how it was wiped.

With the computer power off, the monitor is blank and the monitor power led flashes.  When I turn the computer on with the Hardy installation cd inserted, I hear the disk spinning but see no change in the monitor's behavior - the led flashes, but the screen stays blank.  I know the cd is good, because I used it to install Hardy on my laptop.

Does this mean the computer itself is toast?  Shouldn't I see some bios stuff on the screen, even if the OS was wiped off the hard drive?

---

### Post by Jose Catre-Vandis on 2009-01-28
Can you try another monitor first, this will check out if it is monitor or PC related?

---

### Post by cariboo on 2009-01-28
It sounds like you have a bad video card, if the video adapter was working you would see the led on the front of the monitor turn from flashing amber to steady green during post, and if the monitor was defective, you wouldn't see the flashing amber led.

Jim

---

### Post by japhyr on 2009-01-28
Thanks.  I'll open it up tomorrow and take a look at the video card.

---

### Post by robert shearer on 2009-01-28
Does it have onboard video as well as a video card installed.one of them will have been selected in bios as first on boot so try both.

 (or even a card that was installed and now removed. Possibly by the previous owner before they passed it on to you.Can you check)

If so then the bios has probably been set to initialise the card first. As there is now no card you cannot see the POST or access the bios.

Try putting in a card and and connecting the monitor to it.

Also if you unplug the monitor from the computer and switch the monitor on with no connection it should give a "out of range" or "no input" message.

As a last resort you may have to open a jumper on the motherboard to reset the bios to the factory defaults.
This will usually default to the onboard video if there is one.

 Google the manual for the motherboard to see how to do this. Keep it as a last resort measure though

---

### Post by japhyr on 2009-01-29
> Does it have onboard video as well as a video card installed.one of them will have been selected in bios as first on boot so try both.

Thank you, there was a second video connector on the back of the PC that I didn't notice until I opened the case.

I changed the bios settings to boot from cd, but nothing happens when I shut down and turn it back on, with the livecd in the drive.  I just see a screen with some information about the system (hd, ram, processor, etc) and "Press F1 to Run SETUP" at the bottom of the screen.

Is there a way to tell it to boot, or should that be happening?  I have seen messages that the CMOS battery is low, and it says CMOS Date/ Time Not Set.  Would a low CMOS battery keep it from booting?

---

### Post by egalvan on 2009-01-29
> **japhyr said:**
> Thank you, there was a second video connector on the back of the PC that I didn't notice until I opened the case.

I changed the bios settings to boot from cd, but nothing happens when I shut down and turn it back on, with the livecd in the drive.  I just see a screen with some information about the system (hd, ram, processor, etc) and "Press F1 to Run SETUP" at the bottom of the screen.

Is there a way to tell it to boot, or should that be happening? ** I have seen messages that the CMOS battery is low, and it says CMOS Date/ Time Not Set.**  Would a low CMOS battery keep it from booting?

I hope you gave the machine a good cleaning when you opened it up.
dust bunnies play heck with cooling.

So, the BIOS complains that the battery is low.
Change it.
It will be a CR2032, buy it anywhere watch batteries are sold.


The BIOS settings may not hold between boots if the battery is low.
Normally the power must be cut for the cmos to clear, but I have seen some that will partially clear with just a re-boot.

The fact that the Date/Time is not set indicates at least some re-setting of the cmos.
Ditto with the "Press F1 to Run SETUP".

And if it really has 1GB of RAM, you will have a nice machine, well-capable of running Ubuntu.

---

### Post by Jose Catre-Vandis on 2009-01-29
you should be able to bypass the "F1 to Run setup" request and then the PC should start booting. Alternately if you press F1 then F10 to save out you should also go to boot

---

### Post by egalvan on 2009-01-29
> **Jose Catre-Vandis said:**
> you should be able to bypass the "F1 to Run setup" request and then the PC should start booting. Alternately if you press F1 then F10 to save out you should also go to boot

True, but if the BIOS is being re-set, it will probably boot from the floppy or hard drive first, depending on the age of the machine.

He needs to stabilize this situation first, then start changing the boot order.

A new battery should run $2-$5 depending on where you buy it.

ErnestG

---

### Post by wickedbadawesome on 2009-01-29
A low cmos battery will not prevent you from installing ubuntu or any other operating system for that matter. ubuntu will yell at you that the time is wrong - u can deal with that, that cmos battery though is important for correct date time. And many programs call to that info. 

What are your plans for this machine?
It occurs to me that everyone should have at least one machine at home running linux of some kind, but what will you do with it?

---

### Post by egalvan on 2009-01-29
> **wickedbadawesome said:**
> A low cmos battery will not prevent you from installing ubuntu or any other operating system for that matter. 

It may, if the cmos is being reset between re-boots because of low cmos voltages.

The boot order will keep changing to default order, and this almost never has the CD drive as first-in-line.
(note.. I have never seen a consumer bios default to anything other than floppy or hard drive as first-in-line)

ErnestG

---

### Post by robert shearer on 2009-01-29
Yes, sort out the cmos first.
Replace the battery as egalvan suggests and set time date first-boot etc.

Then, when you install Ubuntu, if you have any problems we will know that they are not bios related.
( always fix the upstream problems first before tackling the downstream ones);)

---

### Post by japhyr on 2009-01-30
I replaced the CMOS battery, and after changing the boot order and exiting bios it immediately started booting from CD.  It's running a memory check right now.  It sure feels good to bring a computer back from obsolescence.

I am in a graduate MEd program, and I started an independent study course on open source applications in education.  I am doing several things with this machine:  reviving an older machine, which schools are full of; trying out edubuntu; installing various programs for evaluation, without filling up my own machine; sharing linux more with my family and then with coworkers and students.  I may also try to set up a small thin client network.

---

### Post by Jose Catre-Vandis on 2009-01-30
:)

---

### Post by robert shearer on 2009-01-31
:) +1

---

### Post by japhyr on 2009-04-17
I set this project aside for a while, but I have picked it back up.  I am trying to install HH 8.04 on the computer, and I am not sure which option to choose on the screen "Prepare disk space".

There are 3 hard drives in the computer - a 20G, 82G, and 82G.

I tried the first option - "Guided - resize SCSI2 (0,0,0), partition #1 (sdc) and use freed space".  Then it said "partition too small", and I realized that option is used to keep Windows on one part of the disk.  I want to erase Windows (Windows 98!) on this machine and do a full Ubuntu install.

The second option is "Guided - use entire disk." But there are three radio buttons, and I'm not sure which to choose.  There is "SCSI1 (0,0,0)(sda) - 20.0 GB ATA ST320414A", "SCSI1 (0,1,0)(sdb) - 82.0 GB ATA Maxtor 6YO80L0", "SCSI2 (0,0,0)(sdc) - 82.0 GB ATA Maxtor 6YO80L0".

The third option is "Guided - use the largest contiguous free space".

The fourth option is "Manual".


Which of these options should I select, and if it is "Guided - use entire disk", which radio button should I choose?

Thank you.

---

### Post by robert shearer on 2009-05-12
Just looking over some older threads and noted this.
I see your post was 3 weeks ago and assume you started a new thread when this got no replies??.

If not then post again here.

For automated install use 'Guided use entire disk' and choose either of the 82G drives.
This will install ubuntu to that drive and leave the other two untouched.

To use all the disks for Ubuntu you will need to use manual Partitioning.There are several good guides to do this,many searchable on these forums, Google will help.

---

