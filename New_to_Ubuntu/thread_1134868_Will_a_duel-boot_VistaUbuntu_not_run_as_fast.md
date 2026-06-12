---
title: "Will a duel-boot Vista/Ubuntu not run as fast?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by GumpTron on 2009-04-24
I am going to install Ubuntu on a 37GIG partition I made. I will list my system spec below and I ask that you tell me if Ubuntu will run any less efficiently in a duel-boot install. Thank you for your time.

PC Wizard 2008 Version 1.871
------------------------------------------------------------------------------------------

Owner: Microsoft
Organisation: Microsoft
User: The Boss
Operating System: Windows (TM) Vista Home Premium Home Edition 6.00.6001 Service Pack 1
Report Date: Friday 24 April 2009 at 01:14

------------------------------------------------------------------------------------------


<<< System Summary >>>

  > Mainboard : Unspecified JHL90

  > Chipset : Intel PM45

  > Processor : Intel Mobile Core 2 Duo P9500 @ 2533 MHz

  > Physical Memory : 4096 MB (2 x 2048 DDR2-SDRAM )

  > Video Card : NVIDIA GeForce 9600M GT

  > Hard Disk : Hitachi (250 GB)

  > DVD-Rom Drive : Optiarc DVD RW AD-7560S ATA Device

  > DVD-Rom Drive : UFCD AJK12N41A SCSI CdRom Device

  > Monitor Type : N154Z1-L02  - 15 inches

  > Network Card : Intel Corporation Intel Corporation

  > Network Card : Realtek Semiconductor RTL8168/8111 PCI-E Gigabit Ethernet NIC

  > Operating System : Windows (TM) Vista Home Premium Home Edition 6.00.6001 Service Pack 1

  > DirectX : Version 10.00

  > Windows Performance Index : 4.8

------------------------------------------------------------------------------------------
***** End of report *****

Thank you for taking the time to read this and for helping me out.

---

### Post by JK3mp on 2009-04-24
No in fact. Ubuntu will ALWAYS run faster in most cases. Linux in general is very lightweight and is less strenuouse on the hardware. Im dual booting right now. :)

---

### Post by jelle_ on 2009-04-24
if you install ubuntu using wubi, it will be slower than normal because it uses an windows-filesystem. if you install ubuntu from cd, it uses an linux-filesystem and it runs at normal speed

---

### Post by Bucky Ball on 2009-04-24
The two operating systems aren't running at the same time. No speed difference. Linux usually faster, occasionally slower to boot.

---

### Post by steve101101 on 2009-04-24
> **bucky ball said:**
> the two operating systems aren't running at the same time. No speed difference. Linux usually faster, occasionally slower to boot.

+1

---

### Post by GumpTron on 2009-04-24
1.)with this much RAM 4096 MB, what should I set the wap partition be set to?

2.)with 37GIGS allocated for this install. What should I set the root partition to?

3.)how much space should be set for the home partition?

---

### Post by Bucky Ball on 2009-04-24
1/ Two Gb all that is required on any Ubuntu machine.

2/ I normally set that to around 10Gb, you could probably get smaller.

3/ It really depends how you are going to use /home (you can even put it on another drive), but for your situation, I would have:

/ = 10Gb (or whatever you choose: 8Gb, 6Gb - check the minimum space required to install your chosen OS)
/home = 25Gb (+ anything trimmed off the '/ = 10Gb' allocation)
/swap = 2Gb

Good luck. Use 'manual partitioning' when you get to the partitioning option during installation. (not Auto)

---

### Post by Bucky Ball on 2009-04-24
Gumptron, please keep your posts on the thread so everyone can follow and learn. :)

That sounds fine but they are wrong about the swap. With four gig of RAM the swap will rarely be used (if ever, depending on what you do).

There has been a lot of debate about this and the following link agrees with your friend:

[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

To me, there is no point in a massive swap with plenty of RAM. The same link contains this:

> let's say that computers have changed a lot since swap was first used : 
[LIST]
[*]At first, swap was needed to extend real memory capacity. You would use swap so that the available memory would be the addition of the RAM space and the swap space.
[*]Nowadays, ***RAM are often big enough so that we could use the computer without any swap at all.***
[/LIST]
So, you get my point. With 4Gb of RAM, it is unlikely you will touch the swap anyhow. Try switching if off (sudo umount /swap) and you will see what I mean. Check in the system monitor when Ubuntu is running and notice the swap indicator shows no response.

Final word? Up to you, but you don't have a lot of disk space to play with for an 8Gb swap which you won't use anyway.

---

### Post by steve101101 on 2009-04-24
and +1 means I agree with whatever is quoted above or the prior post.

---

### Post by Carl Hamlin on 2009-04-24
> **GumpTron said:**
> Will a duel-boot Vista/Ubuntu not run as fast?

Well, that depends on a couple of factors, Gumptron.

If they're duel-booting at close quarters with blades, then running fast might win the day for the loser.

However, if they're duel-booting at 20 paces with pistols, running fast probably won't make much of a difference.

---

### Post by Bucky Ball on 2009-04-24
lol. Or boots with banjos squealing like little piggies! Oops, thinking out loud again!

---

### Post by steve101101 on 2009-04-24
very useful post.

---

### Post by jpyanowski on 2009-04-24
> **Carl Hamlin said:**
> Well, that depends on a couple of factors, Gumptron.

If they're duel-booting at close quarters with blades, then running fast might win the day for the loser.

However, if they're duel-booting at 20 paces with pistols, running fast probably won't make much of a difference.

:rolleyes: Oh really....? (sarcasm off)

---

### Post by abhishek dey on 2009-04-24
hi!!!!!!!!!
it's running as fast u want.
I am also using window7 and ubuntu8.04 in dual boot.

u do one thing put the ubuntu cd in cd-drive restart your machine
click install ubuntu
follow the installation guide
when the disk partition comes select manual disk partition
it will show the partition available in ur system select any pertition in which u r not having any important document, format it with ext3 filesystem and give the file mount point as root '/'
and press next.
follow the other nesecary steps.
now u can use both the OS as fast as u want but one at time.....

---

### Post by Ticketoride on 2009-04-24
> **GumpTron said:**
> 2.)with 37GIGS allocated for this install. What should I set the root partition to?
I have 2 GBs RAM, never been utilized, so I only gave it a 500 MB Partition subsequently.

---

### Post by Bucky Ball on 2009-04-24
Something else to think about Gumpton. Do you really need the /home that big also? If you have more than one drive in this machine and you already save music, pics and vid to that, not the one your OSs are installed on, your /home directory won't need to be very big as it will contain mostly documents. Not big files.

Just a thought. :)

---

### Post by Dileeshvar on 2009-04-24
nope I dont think there will be a problem because
of dual boot and you are using 4GB RAm which is moret than
sufficient for Ubuntu :)

---

### Post by JK3mp on 2009-04-24
> **steve101101 said:**
> very useful post.

can't say much for yours either. :p . Damn... and now mine too. Umm...(rattles in head for something useful....Zzzzzz) *falls asleep*

---

### Post by GumpTron on 2009-04-24
Thank you to everyone in this thread that helped me out, you know who you are.

Now that I have installed ubuntu and things seems to be working, is their some type of config i can post here that you can take a look at and tell me if i installed correctly?

---

### Post by Bucky Ball on 2009-04-26
Pleasure. In a terminal, paste/type:

```
sudo blkid
```... and post that and we'll have a look at what you ended up with. If you can boot into Windoze or Ubuntu from the grub menu, you are definitely heading in the right direction ... :)

Incidentally, to copy or paste in a terminal, same hotkeys but add 'control', ie

ctl/shft/c = copy
ctl/shft/v = paste

---

### Post by GumpTron on 2009-04-26
> **Bucky Ball said:**
> Pleasure. In a terminal, paste/type:

```
sudo blkid
```... and post that and we'll have a look at what you ended up with. If you can boot into Windoze or Ubuntu from the grub menu, you are definitely heading in the right direction ... :)

Incidentally, to copy or paste in a terminal, same hotkeys but add 'control', ie

ctl/shft/c = copy
ctl/shft/v = paste

/dev/sda1: UUID="9E1CA46E1CA442DF" TYPE="ntfs" 
/dev/sda5: UUID="988058ba-4330-442e-95da-e0847b11d98c" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="ab949054-dc8e-4ad0-bfe5-40e98f532413" 
/dev/sda7: UUID="723dd8d2-6f49-49c7-943f-44d969ac8297" TYPE="ext3" 
cky

Thanks for taking a look Bucky Ball.

---

### Post by Bucky Ball on 2009-04-26
Looks fine. Ideally, you would put the swap as the last partition but that is no biggy. I am presuming you have:

/dev/sda1: = Windows 
/dev/sda5: = /
/dev/sda6: = /swap
/dev/sda7: = /home

?

When you go to ´Places´ are you able to see the partitions? Do they appear as a name or as their size. ie:

25 GB Media

?

---

### Post by GumpTron on 2009-04-26
> **Bucky Ball said:**
> Looks fine. Ideally, you would put the swap as the last partition but that is no biggy. I am presuming you have:

/dev/sda1: = Windows 
/dev/sda5: = /
/dev/sda6: = /swap
/dev/sda7: = /home

?

When you go to ´Places´ are you able to see the partitions? Do they appear as a name or as their size. ie:

25 GB Media

?

I'll give ya what I can for now, because half the time I cant even log into ubuntu withouth the graphics being alll crazy and out of proportion.

1.Ubuntu generic
2.Ubuntu recovery mode
3.Ubuntu memtest
4.othe operating systems
5.windows vista boot loader

FYI: i keep getting "your screen, graphics card, and input devices could not be detected correctly". I get this 9 out of 10 times I try to load Ubuntu and I don't understand whats going on.

---

