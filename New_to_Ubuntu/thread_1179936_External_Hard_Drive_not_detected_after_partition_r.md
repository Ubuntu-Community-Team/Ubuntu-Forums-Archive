---
title: "External Hard Drive not detected after partition re-size"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by ben1986 on 2009-06-06
Right, I'm sure I will be laughed at for this but Ill tell you what I did.

I had a dual-boot with XP and Jaunty, never used the XP side, so thought great, I'll resize the Ubuntu partition and reclaim my laptops hard drive.

I booted into Live CD (Hardy version) and opened GParted. It hung on the scanning drives or whatever, and I realised my external hard drive was still plugged in. I closed GParted, unmounted the HD, reopened GParted, deleted the Windows partition, resized the Ubuntu partition, it all went fine.

Booted into Jaunty, and it doesn't see my external drive. If I plug in other external drives it sees them fine. I thought, ****, better restart. That did nothing. So I booted into the Live CD, thinking it might show up there again. Nothing. Even the BIOS boot menu doesn't see it. This is ~700Gb of films, music and photos that I would seriously grudge losing. I have looked everywhere but most problems involve something about internal drives not mounting, or new drives not mounting. But this one worked fine for months. Have I killed it?

I have seen references to something called fdisk -l, and I tried sudo mkdir /media/MyBook followed my mount /dev/sdc/ /media/MyBook (which I culled from another thread) but it said special device did not exist.

Please save my external drive, its was expensive :(

p.s. if not already apparent from my cack-handed destruction of the drive, I am a noob.

p.p.s. feel free to mock me

---

### Post by Sir Jasper on 2009-06-06
Hi,

After booting as normal with your external drive plugged (but without the CD loaded) start Gparted.

Near the top right hand corner of the Gparted screen is there a small dropdown arrow which lets you change the drive?

If yes, and if your external drive is shewn then click on it and tell us, as a starting point, what Gparted reports.

My regards

---

### Post by ben1986 on 2009-06-06
It only shows my internal drive /dev/sda1 when I click the arrow

had a look in the list of the drives, there is no longer an sda2 or sda4. sda2 was my old windows partition.

thank you for the rapid response.

---

### Post by Sir Jasper on 2009-06-06
Hi again Ben,

I cannot immediately think what my next step would in your circumstance so I suggest you await advice from a more experienced helper.

Good fortune

---

### Post by hexanol on 2009-06-06
We are talking about a USB external hard drive, aren't we ?

You could always give us the output of "sudo lsusb" command, if your external HDD is connected to your computer via USB. Before running this command, don't forget to plug it in/power on. :p

---

### Post by LewRockwell on 2009-06-06
sounds like it might be an unclean dismount after some sort of hang.

first, make sure your primary system is super A-OK and backed-up(SOP-standard operating procedure)

then use testdisk to fix your problem(s)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

read thoroughly FIRST, and there are additional links that you should probably read also BEFORE your attempt(s)

please make sure to follow up here after your procedures as a "pay-it-forward" for others.

Thanks!

---

### Post by ben1986 on 2009-06-06
The output of lsusb is:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


That was with only the external disk plugged in. And yes, it is plugged in and whirring away merrily on my desk :) 

Does this tell anyone anything?

Also, when I plug in my second hard drive, (a western digital My Passport, as opposed to the WD My Book which is the problem drive), it looks like this

Bus 001 Device 005: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And that was the same USB port. As you can see, the My Book just isn't seen by the computer, not even under BIOS...

Does this tell anyone anything?

Also, thank you for the test disk help, I will have a read when I have re-discovered my will to live.

---

### Post by Sir Jasper on 2009-06-06
Hi  Ben,

Lew's link is to the most versatile program I have personally seen but although the reference is to all hard drives it does not seem to specifically refer to external drives.

As Lew said post back with success or failure.

---

### Post by ben1986 on 2009-06-06
Test disk only sees the following drives with the My Book plugged in:

Disk /dev/sda - 58 GB / 54 GiB - ATA ST960822A
Disk /dev/sr0 - 552 MB / 527 MiB (RO) - _NEC DVD+-RW ND-6650A

With the My Passport it sees the following:

Disk /dev/sda - 58 GB / 54 GiB - ATA ST960822A
Disk /dev/sdb - 250 GB / 232 GiB - WD 2500BMV External
Disk /dev/sr0 - 552 MB / 527 MiB (RO) - _NEC DVD+-RW ND-6650A

This doesn't seem to be an anticipated state of affairs on the walkthrough. If Im being dense I apologise, thank you for the help so far. Im going to have a dig through my cupboards to see if I still have the documents that came in the box with it. Damn stuff is all in French....

---

### Post by -kg- on 2009-06-06
What this looks like to me is that you have a connection problem with the MyBook.  It is not even being detected as being plugged in, where the Passport is.  Whether the partitions on the MyBook are screwed up or not, the device should still be detected on hot connect (or on boot-up).

If it is possible, try another connector cable (or perhaps you have FireWire, or eSATA if you have that capability?) with the MyBook and see if it detects it.  It's possible that one of the wires developed an open in the cable.  Other than that, I hope the MyBook is still under warranty, unless someone else has another idea?

---

### Post by louieb on 2009-06-06
Really don't think re-partitioning the internal drive has anything to do with the problems your having with the external drive.  

Since you said there is no problem with the computer recognizing your other external. Sounds like the problem is with the my-book  drive. If it doesn't work on another computer and it not in warrenty may be time to open the case and install the the drive internally.  Haven't had to do that to a my-book but I've done it with a maxtor external that quit. 

[http://www.ransackery.com/western-digital-mybook-open-case-recover-data.htm](http://www.ransackery.com/western-digital-mybook-open-case-recover-data.htm)

---

### Post by LewRockwell on 2009-06-06
{{steps back into room}}

yep, looks like some sort of failure of the cable or the external drive/enclosure...

here's a link to a must-have item for the home technician:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

let us know how this turns out!

---

### Post by ben1986 on 2009-06-06
Haha, cheers guys. It seems like that might be the problem. I have a laptop so no idea how to mount it internally, but that's probably a question for another post. Good to see that all is not necessarily lost. I will see about another cable / mounting, and I will post here whether I eventually get the data back. I feel a bit like Icarus, reaching for an extra 25Gb and losing 1Tb doing so. Such is life.

Thanks again for all your help, this really is the reason I switched to Ubuntu, I was sick of Windows doing a "diagnostic scan" and saying "error: ^%$&^$£%^ contact your network administrator" no matter what problem I had, or going to a program's website for help and finding FAQs like "how can I tell all my friends how great this program is?" with no reference to possible flaws or problems...

---

### Post by ben1986 on 2009-06-06
solved!

Don't know why I didn't think of this before, just switched cables between Passport and My Book *et voila!*

I had no idea you could screw the cables up by unmounting volumes or whatever, but there is a lot I don't know about computers, shouldn't be surprised.

Thanks again guys.

---

### Post by louieb on 2009-06-06
> just switched cables between Passport and My Book 

:biggrin: Glad it was something simple. Now can you figure out how to mark this thread as solved?

---

### Post by hexanol on 2009-06-07
> **ben1986 said:**
> ...*et voila!*
I see that your french is getting better... ;)

> **ben1986 said:**
> I had no idea you could screw the cables up by unmounting volumes or whatever, but there is a lot I don't know about computers, shouldn't be surprised.
I couldn't say how the cable "screw up" but see it as a fatality, not as a consequence of unmounting a file-system or whatever. You were doomed from the start!

---

### Post by LewRockwell on 2009-06-07
all USB connectors are not created equal...

some are definitely better than others...

a brief visual inspection of all USB ports and plugs is essential to safeguarding your equipment!

for example:

brand new netbook and some dork tries to slide their thumb-drive into the USB port...

except that their thumb-drive has been riding around in their pocket/purse/whatever and has been damaged by another object...

and now the damaged plug damages your port(and perhaps even damages your main board due to a short circuit caused by the buggered plug)

as always, your mileage may vary...

---

