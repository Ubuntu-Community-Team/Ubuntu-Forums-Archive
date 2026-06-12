---
title: "Partitioning issues"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by kpiper1993 on 2009-07-24
Hi, I am trying to install ubuntu 9.04 on my laptop and I am having trouble with the installation.  When I am installing, I get the error, "input/ output error during read on /dev/sda". Furthermore I get the error "creation of swap space in partition #6 of scsi1 (0,0,0) (sda) failed"
as u can see I'm having partitioning problems and any help would be greatly appreciated.

---

### Post by louieb on 2009-07-24
1st thing to do make sure your install CD is good. 
Select the Check Media for Defects option. Should come back error free. If any errors are detected you will need to burn another CD. All it takes is a few twisted bits to give weird results.

---

### Post by kpiper1993 on 2009-07-24
Test result=disc is error free
thanks though

---

### Post by celticbhoy on 2009-07-24
Can you post a copy of the current partition table?

---

### Post by LewRockwell on 2009-07-24
> **kpiper1993 said:**
> Hi, I am trying to install ubuntu 9.04 on my laptop and I am having trouble with the installation.  When I am installing, I get the error, "input/ output error during read on /dev/sda". Furthermore I get the error "creation of swap space in partition #6 of scsi1 (0,0,0) (sda) failed"
as u can see I'm having partitioning problems and any help would be greatly appreciated.

it might be helpful to know the make, model, and part/build number of your laptop

then we might be curious about whether you'll be single booting, dual booting, or even triple booting...and if so, what other OSes do you have or plan on installing

.

---

### Post by louieb on 2009-07-24
With the disk read problems and swap creation problems. Just sounds like a hard drive going bad. Do you have a working OS on the laptop now?

```
sudo lshw | less
```this will list hardware look for the disk section looks something like this:
```

           *-disk
                description: ATA Disk
                product: ST9160821A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: n/a
                serial: 5MAD137C
 

```go to the hard drive manufactures web site and see if they have diagnostic software  (most do).

---

### Post by kpiper1993 on 2009-07-24
right now i have two partitions, one is ext3 primary "/" and the other is a swap space.

I do not have a working os right now.  my computer crashed and would not boot up again.  i looked for the reinstallation disc but could not find it.  i heard about ubuntu and wanted to try it.

i think i am having problems with my hard disk but how can i check that? should i do it over the live cd? ill see if that works.

i will be single booting obviously unless i find my disc, which i doubt.

i have AMD turion 64 x2 dual core mobile technology TL-50

thanks for u guys help, let me know if there is other info u need.

---

### Post by mapes12 on 2009-07-25
So, you just need to install Ubu onto your laptop and don't have a need for any other OS on the HDD. I did the same the other day on a Thinkpad T30 which had XP on the HDD. First thing I did was completely wipe the HDD by booting from a Live Killdisk CD: [http://www.killdisk.com/](http://www.killdisk.com/)

For some reason my laptop does'nt like the Ubu Live CD's so next I used an [alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") Ubu installation CD and just followed the on screen instructions/prompts. Personally, I like 8.04 for the Long Term Support but given that you have nothing critical on your machine it may be worth trying different versions to see which you like best.

At some point it's good practice to have your /home on a separate partition. If you need further help with this then post a new thread. Also, take a look at the link in my sig file for more help.

---

### Post by louieb on 2009-07-25
IF you still get disk errors after trying the alternated CD. 
There is a Linux tool available: smartmontools
> The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks. It is derived from the smartsuite package, and includes support
for ATA/ATAPI-5 disks. It should run on any modern Linux system.It can be installed and run from the Ubuntu live CD. However for someone new to Linux i recommend using [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") it contains a graphical user interface for smartmontools. 

It still sounds like your hard drive has died and is going to have to be replaced. This tool can check the health of the hard drive.

more here : [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

---

### Post by kpiper1993 on 2009-07-25
good news - i found my problem
bad news -  my hard disc is dead

thanks for u guys help, it looks like ill be buying a new computer soon. or is there any way i could do something with what i have? idk at this point.

---

### Post by LewRockwell on 2009-07-25
> **kpiper1993 said:**
> good news - i found my problem
bad news -  my hard disc is dead

thanks for u guys help, it looks like ill be buying a new computer soon. or is there any way i could do something with what i have? idk at this point.

I didn't really come up with any laptops called a TL50 so it's hard to say what you might want to do

If you just decide to throw it away I can give you my mailing address and reimburse you for your time, packing materials, and shipping costs

.

---

### Post by mapes12 on 2009-07-25
> **kpiper1993 said:**
> good news - i found my problem
bad news -  my hard disc is dead

thanks for u guys help, it looks like ill be buying a new computer soon. or is there any way i could do something with what i have? idk at this point.
If it's just your HDD that has died then why not get a replacement? I guess it would be cheaper than a new PC! Besides, Linux usually has better support for hardware that has been around a while compared to new stuff.

---

### Post by mikechant on 2009-07-27
Lots of hardware problems are very difficult to resolve on laptops but disc drives are often the exception - usually it's just a standard 2.5" drive, quite accessable (under a screw-on plate) and just a unplug/plugin replacement.
See this example:
[http://www.fonerbooks.com/laptop_1.htm](http://www.fonerbooks.com/laptop_1.htm)
Replacement drives are pretty cheap. If you're not sure what replacement to get take the old one into a parts shop or post a photo of the spec plate/connector.

However, some laptops are not so easy and you need to take them apart to get at the hard drive.

---

### Post by egalvan on 2009-07-27
> **kpiper1993 said:**
> AMD turion 64 x2 dual core mobile technology TL-50


With a DualCore CPU, it's probably new enough to use a SATA drive,
so a new hard drive will be easy to find.

Even if it's the older PATA style, you can still find new drives.

Note.... some lappies have the drive installed in a "sled", with an adapter on the drive connectors,
others have a connector adapter only...
keep a sharp eye on this...

newegg.com is your friend in this, unless you live in an area not covered by their shipping policies.

And if you do decide to throw it away, then I'll see LewRockwell bid, and raise him $5 for your troubles :)

seriously, a replacement drive is not that expensive, or difficult to obtain... depending on your location, of course.

---

