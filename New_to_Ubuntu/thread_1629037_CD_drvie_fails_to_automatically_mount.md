---
title: "CD drvie fails to automatically mount"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by John Peschken on 2010-11-23
I have an external CD drive that neither Ubuntu nor Mint will automatically mount.  The drive works normally under Windows XP on the same machine.   

Nero for Linux sees it, and can use it without difficulty even though it never appears as a mounted volume.  
   
  Is there a way to encourage Linux to mount this thing so that it can be used with programs other than Nero?

---

### Post by cariboo on 2010-11-23
What is the output of:

```
dmesg | tail -n20
```

when you plug your device in?

---

### Post by John Peschken on 2010-11-23
> **cariboo907 said:**
> What is the output of:

```
dmesg | tail -n20
```when you plug your device in?

I'm at work now, away from the machine.  I'll try that code this evening and get back to you.

As far as when I plugged it in,  I forgot to mention an important fact.  It only fails to mount audio CD's.   It does fine with data CD's.  I installed Ubuntu from it, so it was plugged in from the start.  I have tried unplugging and re-plugging, rebooting, etc. but it behaves the same.  Data CD's work; audio CD's spin a few times but never mount.  Same symptom with Ubuntu 10.04, 10.10, and Mint 10.  I have installed some of these from a different drive, and attempted to use this drive later.  It makes no difference when I introduce this drive to Linux.

---

### Post by John Peschken on 2010-11-23
> **cariboo907 said:**
> What is the output of:

```
dmesg | tail -n20
```when you plug your device in?

Ah, sorry about that.  I took what you said all wrong.  I thought you were a person with limited English asking me when when I plugged the drive in.  Sorry.

Anyhow, here's the output when after I plug the drive in with an audio CD in the drive.

```

[38193.596900] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 c4 00 00 02 00
[38193.596937] end_request: I/O error, dev sr0, sector 784
[38193.909836] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[38193.909858] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[38193.909879] Info fld=0x0, ILI
[38193.909887] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[38193.909909] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[38193.909946] end_request: I/O error, dev sr0, sector 0
[38194.195085] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[38194.195106] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[38194.195128] Info fld=0x0, ILI
[38194.195135] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[38194.195158] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[38194.195194] end_request: I/O error, dev sr0, sector 0
[38194.480209] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[38194.480231] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[38194.480253] Info fld=0x0, ILI
[38194.480261] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[38194.480283] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[38194.480320] end_request: I/O error, dev sr0, sector 0
```Again, sorry about the misunderstanding,

---

### Post by John Peschken on 2010-11-26
If it's any help, ls-usb returns the following for this device.

Bus 001 Device 008: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
 
 It returns this only if I have a data disk in the drive.  If it's a music disc, the device does not appear is lsusb.  Nero for Linux can see it, but apparently Linux can not.  It seems that Nero goes around the OS somehow.  That might explain why it's so much faster ripping disks than Sound Juicer or other ripping programs.  

Although I can use this drive via Nero, I would still like to figure this one out.  Anyone?

---

### Post by coffeecat on 2010-11-27
> **John Peschken said:**
> If it's any help, ls-usb returns the following for this device.

Bus 001 Device 008: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter

It does indeed help. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

There are a few workarounds posted there for Maverick as well as some general discussion. Also a link to a bug report for this hardware which you might want to do a me-too on. Although I don't hold out much hope that this will ever get fixed in Maverick. By the way, you can probably skip over the OP's post. The relevant stuff is in the discussion between forum member mikolune and myself.

---

### Post by John Peschken on 2010-11-27
That discussion went right over my head on first reading.  I'll have to go back and try again later when I have more time.  Tried the: udisks --mount /dev.sr0 and sr1 thing to no result except an error.  I did discover that VLC can access the thing as Nero can. 

As for filing a bug report, I did try that once on a different problem.  It's a fairly daunting process for a newbie.  It ended when someone asked me to try an upstream back-ported something-or-other.  No idea what he or she was after, and requests for more explanation were ignored.  That's where it sits as far as I know.  The process did not encourage me to do it again.

Thanks for your help.  I'm pretty sure the answer is in that thread somewhere.  I just need to study it.

---

### Post by coffeecat on 2010-11-27
> **John Peschken said:**
> Tried the: udisks --mount /dev.sr0 and sr1 thing to no result except an error.

That should be:

```
udisks --mount /dev/sr0
```... or /dev/sr1, depending whether or not there is an internal DVD drive in your system. If you typed '/dev.sr0' that would make no sense to the system and would give you an error message. Also - that code only works with a data disc.

> **John Peschken said:**
> As for filing a bug report, I did try that once on a different problem.  It's a fairly daunting process for a newbie.

Agreed, but if you already have a Launchpad account, all you have to do is to go to the Launchpad link I provide in post #10 of that thread and click on the 'This bug affects...' line near the top to add your me-too. Having said that I remain fairly pessimistic that anything will be done. The only optimistic note is that you'll see that, so far, this device works OK in Natty.

---

### Post by John Peschken on 2010-11-27
> **coffeecat said:**
> That should be:

```
udisks --mount /dev/sr0
```... or /dev/sr1, 

Agreed, but if you already have a Launchpad account, all you have to do is to go to the Launchpad link I provide in post #10 of that thread and click on the 'This bug affects...' line near the top to add your me-too. Having said that I remain fairly pessimistic that anything will be done. The only optimistic note is that you'll see that, so far, this device works OK in Natty.

Actually, I ran the command correctly, just couldn't get it to copy/paste correctly, so I typed it and messed up.

I did go to Launchpad and add a me-to.  Most of the technical discussion is over my head.  I just don't yet understand enough to mess with it.  Do no harm.  I think I'll just sit back and hope it gets solved in Natty.  In the meantime, I have another drive that works, but it's a big honkin' DVD burner.  This one is slow and a CD reader only, but it fits in my netbook case and runs off the USB power.  I can at least use it with Nero and VLC.  It just doesn't show up in Gnome and other apps.  I'll survive.

I love the idea behind Linux and prefer it when stuff works, but there are irritations.  One needs a certain amount of dedication to stick with it.

---

### Post by coffeecat on 2010-11-28
> **John Peschken said:**
> In the meantime, I have another drive that works, but it's a big honkin' DVD burner.  This one is slow and a CD reader only, but it fits in my netbook case and runs off the USB power.

That's interesting. My affected one is my big "honkin' " one. It's a bare external USB enclosure that takes full-size DVD drives. I've tried a couple of different drives in it but with the same result. Whereas my external DVD drive that works OK with Maverick is one of those little ones using a slimline  drive that's powered from the USB. I guess the 05e3:0701 chipset that's the problem has found itself in a variety of different hardware types. You'll see from the link I posted that the problem 05e3:0701 is the enclosure firmware, not the actual DVD drive firmware.

> **John Peschken said:**
> I love the idea behind Linux and prefer it when stuff works, but there  are irritations.  One needs a certain amount of dedication to stick with  it. 	

Agreed. I've learnt to be philosophical when confronted by problems like this. When you consider the enormous range of hardware out there, most of which has only been tested by the manufacturers for compatibility with Windows, and when you consider that the Linux developer community has to create drivers often without the cooperation of said manufacturers, it's amazing that so much stuff does work just fine.

---

### Post by chippada2k10 on 2011-01-08
My Cd drive fails to automatically mount and when I typed "dmesg /tail -20, the following output is displayed.  Pl someone help me in correcting my problem

[13945.794608] sr: Sense Key : Hardware Error [current] 
[13945.794617] sr: Add. Sense: Media load or eject failed
[13969.442965] sr1: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[13969.442995] sr: Sense Key : Hardware Error [current] 
[13969.443003] sr: Add. Sense: Media load or eject failed
[13993.091298] sr1: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[13993.091329] sr: Sense Key : Hardware Error [current] 
[13993.091337] sr: Add. Sense: Media load or eject failed
[14016.739960] sr1: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14016.739992] sr: Sense Key : Hardware Error [current] 
[14016.740036] sr: Add. Sense: Media load or eject failed
[14040.387730] sr1: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14040.387763] sr: Sense Key : Hardware Error [current] 
[14040.387772] sr: Add. Sense: Media load or eject failed
[14064.035814] sr1: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14064.035845] sr: Sense Key : Hardware Error [current] 
[14064.035855] sr: Add. Sense: Media load or eject failed
[14084.699947] sr1: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14084.699980] sr: Sense Key : Hardware Error [current] 
[14084.699990] sr: Add. Sense: Media load or eject failed

---

