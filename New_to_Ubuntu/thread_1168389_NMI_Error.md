---
title: "NMI Error"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by K7522 on 2009-05-24
I am having an issue on the latest Ubuntu release with the following code in /var/log/syslog.

I seem to be producing this lately. This will sometimes result in a system crash that requires a system reboot. I can't seem to pin down what the issue is even after extensive searches of the internet. I can receive anywhere from one per minute to 6 per second.


```
May 24 00:29:25 kurt-9 kernel: [  342.881456] Uhhuh. NMI received for unknown reason 2d on CPU 0.
May 24 00:29:25 kurt-9 kernel: [  342.881462] Do you have a strange power saving mode enabled?
May 24 00:29:25 kurt-9 kernel: [  342.881464] Dazed and confused, but trying to continue
```

This code will sometimes be "3d" on first line instead of "2d"

Thanks in advance for your help!

---

### Post by QIII on 2009-05-24
I've seen explanations ranging from hot cpus to fried components to graphics cards.

Since it just started happening with the new release, I'll discount the first two problems for now.

There may be some issues with your graphics card/driver, since there are known issues with some Intel cards, and there have been a lot of discussions on the boards in reference to ATI and NVidia drivers.

It might be helpful to have some hardware info about your machine, how old it is, etc.

---

### Post by K7522 on 2009-05-24
Sure thing.

I'm running Ubuntu 9.04 (jaunty)
kernel 2.6.28-11-generic

3GB of Corsair RAM, 1GB sticks each. About a year old.
Processor is an Intel Core2 Quad Core 2.33Ghz (Q8200) About a year old.
Not sure what the MoBo is. About a year old.
Graphics is an nVidia 8800GTS, a few years old. Running the 180 driver for it.

Two HDs, one Maxtor, one WD both a couple years old.

---

### Post by QIII on 2009-05-24
I've read a lot of posts lately about NVidia cards, and the 180 driver seems to be what everyone is saying you should be using.

Looking at graphic card/driver is just a WAG right now, anyway. 

But take a look at System>Admin>Hardware Drivers and see if there is a proprietary driver and whether or not it is enabled.

I'm off to bed, but you might want to post a reply for someone else to pick up on.

---

### Post by Didius Falco on 2009-05-24
I did a little googling around about this, just because it interested me. It appears to be a parity error, and the consensus is that it could either indicate damaged hardware (does not have to be inoperable, just not operating fully as expected, and reported to be very hard to trace unless the hardware fails completely) or a problem between the kernel and the BIOS ACPI.

You could try turning off ACPI in the BIOS and see if that resolves it.

Note that I an NOT a kernel guru, and I'm just parroting a few things I spotted during a google session.

Please report back if you get to the bottom of this - I for one would like to know the answer.

Good luck!

Regards,

Didius

---

### Post by K7522 on 2009-05-24
Thanks Didius, that's actually an interesting lead! Since I seemed to get hints at hardware issues, I decided to investigate my PC a little bit. If I disable ACPI, the computer loops at restart, it doesn't even get to GRUB. I don't really understand that! I'm no expert at all.

As for hardware issues, I lost about 12 sectors on one of my HD's earlier this year, but it hasn't seen any further issues since. I don't see that being an issue since I've isolated those bad sectors.

Thanks for the help QIII, I'll have to check out the drivers.

---

### Post by Didius Falco on 2009-05-24
I found this:

[http://en.wikipedia.org/wiki/Non-maskable_interrupt](http://en.wikipedia.org/wiki/Non-maskable_interrupt)

 > A **non-maskable interrupt** (**NMI**) is a computer [processor]("http://en.wikipedia.org/wiki/Central_processing_unit") [interrupt]("http://en.wikipedia.org/wiki/Interrupt") that cannot be ignored by standard interrupt masking techniques in the system. It is typically used to signal attention for non-recoverable hardware errors. (Some NMIs may be masked, but only by using proprietary methods specific to the particular NMI.) <snip>

I think the first thing I'd do is run memtest for a couple of hours - it could be as simple as a RAM problem.

Just a thought...

Regards,

Didius

---

### Post by K7522 on 2009-05-24
Well, I decided to go after the RAM since it seemed the easiest issue to address, since I could run it and work on the laptop. Here's the report.

I started the memtest and about five seconds in it started recording thousands of errors, I believe on the initial "looking" at the ram. I thought to myself I can't see how thousands upon thousands of kb could be bad on a stick of ram, so I decided to remove that particular stick and reboot. The computer started acting like it didn't have any RAM in there.

I'm starting to wonder if it's not the MoBo. After further trial and error, I could under random circumstances be able to boot again with it able to view the RAM. It doesn't matter how much RAM is in, or in what DIMM. That makes me believe that the MoBo is going out.

Any ideas or suggestions? The MoBo is about a year old

I think it's interesting that the error of it not booting at all, (not even sending a signal to the monitors), only began when I moved/removed RAM sticks. That's what led me to believe the DIMMs are going out on the MoBo.

---

### Post by QIII on 2009-05-24
I was hoping it would be something simpler than hardware!

Alas.

But it sure seems oddly coincidental that a hardware issue like a motherboard or memory problem would show up just as you went to Jaunty.

Did you open the case to add more memory just before you upgraded?

If you can get the machine past POST, can you get into your BIOS and see if it has amy hardware monitors, like temperature sensors, memory installed, etc?

---

### Post by Didius Falco on 2009-05-24
> **K7522 said:**
> Well, I decided to go after the RAM since it seemed the easiest issue to address, since I could run it and work on the laptop. Here's the report.

I started the memtest and about five seconds in it started recording thousands of errors, I believe on the initial "looking" at the ram. I thought to myself I can't see how thousands upon thousands of kb could be bad on a stick of ram, so I decided to remove that particular stick and reboot. The computer started acting like it didn't have any RAM in there.

I'm starting to wonder if it's not the MoBo. After further trial and error, I could under random circumstances be able to boot again with it able to view the RAM. It doesn't matter how much RAM is in, or in what DIMM. That makes me believe that the MoBo is going out.

Any ideas or suggestions? The MoBo is about a year old

I think it's interesting that the error of it not booting at all, (not even sending a signal to the monitors), only began when I moved/removed RAM sticks. That's what led me to believe the DIMMs are going out on the MoBo.

If you have access to another PC that can use that RAM, that'd be a good way to test it out. Put 1 stick at a time in and run Memtest for a while. Shouldn't take long, since you started getting errors right away on your PC.

Might be a good idea to test your video card in another PC as well.

Diagnosis of these kinds of hardware problems the actual fix is always is tough to do. for that matter, in all but the most obvious cases, diagnosis is 95% of the battle, and the actual fix is easy, if not always cheap.

Basically, the only way to really pin it down is to just tear the PC down to the basics and start adding stuff back in until something jumps out at you.

I do wonder, though - did this start happening right after you upgraded? If so, and if you have a few spare gigs on your HD, I think I'd reinstall 8.10 to a separate partition and see how it acts.

It could be that something in your PC and 9.04 don't play well together... all it'll cost you is a little time, and if you get the same problem, that would be a real good indicator that it's a hardware issue.

I just hate to see you replace 1/2 the components in your PC trying to figure out which one is throwing a hissy.

Good luck...

Regards,

Didius

---

### Post by K7522 on 2009-05-25
Well I saw the NMI error in Intrepid, I just ignored it because I could never find a good answer to what it was doing. I don't feel like it's Ubuntu anymore, which is both a positive and a disappointment. Software is easier to fix.

You made mention of pulling out the RAM and trying one by another. I did that, and that's when I started having an issue with it not even booting. It won't even send a signal to the monitor. That makes it sound like a hardware issue in teh way of the video card doesn't it?

Why though, would how it act change based on moving and changing RAM sticks? I tried switching out RAM one at a time, and I was able to get one RAM tested on the memtest alone before it started acting up and not even signaling the monitor.

I don't have another desktop to play with these things elsewhere, I'm on a laptop currently.

I'm going to play with the PC some. I don't have another compatable video card which is going to make it rough if it's the vid card, so cross your fingers. Any other tips during this are highly appreciated.

I found this too,
[http://blogs.msdn.com/oldnewthing/archive/2007/02/27/1769274.aspx](http://blogs.msdn.com/oldnewthing/archive/2007/02/27/1769274.aspx)

---

### Post by K7522 on 2009-05-25
Well to update, I went in the room and hit the power button, and it turned on for about 1/4 of a second then turned off. It wouldn't try to start again so I turned off the power to the PS and back on, and it repeated the same thing.

I started removing peripherals, sound card, video card, one of the hard drives, then the other, the RAM.. basically by the end all there was, was 1GB RAM and the CPU on the MoBo. It still did the same thing.

Clicking the power button, the fans spin for a second then stop. Does anyone agree that there is a MoBo issue? Maybe RAM too, but the computer seems to have degraded dramatically in the past two days.

---

### Post by Didius Falco on 2009-05-25
It's sounding more and more like that is the problem. Give the motherboard a close visual inspection; look for bulging transistors, burnt traces, that kind of thing.

Give it a good sniff or three, too. Often you'll smell a faint burnt odor. Sniff the CPU and the power supply too.

Please post back when you finally figure it out. My natural curiosity is definitely aroused now...

Regards,

Didius

---

### Post by Miljet on 2009-05-25
I don't think that I would rule out a power supply problem either. It's a bummer you don't have another system to swap out components. Sure would make troubleshooting easier.

---

### Post by K7522 on 2009-05-25
Yeah I thought about the PSU too, but it's fairly new for a PSU. I may look at getting it tested by an old friend. He should have the gear.

---

