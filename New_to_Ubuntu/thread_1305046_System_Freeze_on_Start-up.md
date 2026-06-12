---
title: "System Freeze on Start-up"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Ijtaba on 2009-10-29
Right Guys Ive tried my luck with ubuntu 8.10 and 9.04 on the X86 Platform.
I have installed it numerous times on a machine with some hardware changes...
Most times I used the install from inside windows option (few times on boot and LiveCd only with 8.10 but realised that was x64 :( )

My initial system was:
Intel Pentium 4 Socket 478, 2.8GHZ
d845bg motherboard
using onboard video
512 MB Ram only 1 stick by kingston ddr 333
120 GB hard disk Maxtor ide
TP-Link TL-WN353G Wireless lan card built in pci 
Sony CD-RW drive 52x

Then i found some stuff at a boot sale and changed

The mobo -d865perl
added a lan card - rtl8139 pci
and a new gpu ATI Rage 128 Pro 32MB AGP 4x (cause the thing doesnt have onboard video)
Even after the change the system still hung.

The precise moment of hanging is just after init(userland) loads and is about to ask for the password (or spend time on installation for first time runs). The mouse loads, and you can see the background, you could move it for 0-5 seconds then bang, the system freezes. 
Restarting X does not work (control+alt+backspace)
keyboard leds dont work
Even the magic keys dont respond (I think its a proper full system freeze)
But the reset button does..

Running LiveCD everything goes fine, but before it is about to go into userland, I get a black screen with a white flashing cursor...
Again at this stage no input, numlocks or magic keys work, but there seems to be consistant video output (maybe the kernel unloaded????)

Right now a list of things I have tried...
Kernel Paramaters:
-acpi=off noapic nolapic (acpi workarounds)
-irqpoll pci=noirq pci=noacpi acpi_irq_nobalance noirqbalance irqfixup noirqdebug (if the problem is with interrupts)
-acpi=noapic (Dont ask me why!! Its not in the kernel list but worked once! :D)
-xforcevesa (this was needed first time around as my 845 graphics controller would go overrange, but I can drop it with the ati rage pro (that bug is probably fixed))
-An array of curse words thinking the kernel could understand some ;)

NOTE: i've tried these combinations, together, seperately, randomly an uncountable number of times without recording which, where and when (you'd think the kernel needs everything spelt out for it...)

Please guys coming to this forum is my last resort to quit slack windows, I so want to be part of this cool community, but cant without a linux distro. Help Please!!

On a side note, The machine has never worked properly except for 1 time 2 months ago.  I kept trying hang after hang, untill the 333333rd time it did not hang, completes the setup, reboots, NO HANG, and it worked flawlessly on the machine for 2 hours, but hung again while using firefox and never started the same way again.

This was a really long message, thanks for your patience if you read this far. Now for some random tags:

System hang, System freezes, Machine freezes, hung, hanging, hangin' , will not not hang, unhang unheard of, Ubuntu 8.10, 9.04, NEED HELP QUICK, LITTLE TIMMY IS STUCK IN A WELL, If your name is little red riding hood, there is some big teethed grandma waiting for you on thread 325.

CHEERS!! (No really im p*ssed)

---

### Post by Xomm on 2009-10-29
I've had the same problems on Ubuntu 9.04 before.

(I use a USB keyboard+mouse)

It seems like the computer "disconnects" the mouse and keyboard, giving the impression that the system crashed, but since the power button works (soft shutdown).

I'm in no way a expert on this, but my advice would be to try 8.04 LTS (solved my problems), or 9.10 (haven't tried yet).

---

### Post by Ijtaba on 2009-10-29
Thanks for replying Xomm,

Yeah, that would be a good idea, but im bogged down with "Limited" internet for the month so no big downloads...
If it just disconnects the keyboard, mouse than something is probably running back there, 
Do you have the same mobo?
ill keep trying, just a quick question, isnt 7.04 more stable?

UPDATE: Not the same case, cant do a soft shutdown, thing's completely frozen.

---

### Post by billv6 on 2009-11-01
I've had the same problema here... :(

Someone found the fix for the problem?

Here is my hardware:

description: Motherboard
       product: PW-945GCX
       vendor: PCWARE

description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (04/02/2008)
          size: 64KiB
          capacity: 448KiB

description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU 1
          size: 1203MHz
          capacity: 1203MHz
          width: 64 bits
          clock: 200MHz

Thanks!!!

---

### Post by LewRockwell on 2009-11-01
could be hardware

stuff doesn't last forever

try installing another distro on it

a few we like:

Damn Small Linux(50MB distro and will Live-Run from CD)

Puppy Linux(100MB distro and will Live-Run from CD)

keep us posted and please use separate threads for each trouble-call
(otherwise mix-ups become common and cause future readers untold grief)

.

---

### Post by Xomm on 2009-11-02
I'm not sure if 7.04 is more stable, it very well might be, but since it's reached it's end of life, and 8.04 is a LTS release, 8.04'll have more support.

I've re-read your post, and seen that you installed using Wubi.

Sometimes stability is compromised while using Wubi, as it has to make a file within the Windows partition as a virtual hard drive. 

If you know how to install on boot, I'd recommend doing so, as this eliminates any problems that Windows may have caused. 

Since you've already tried that, give it one more go, making sure you're not slipping on any steps (use ext3 fs if you're keeping windows so you can access the partition, and don't kill off windows until you've succeeded).

If it still doesn't work, try LewRockwell's advice and try the small distros.

If you're still stuck, call for more help or wait out the month and try 8.04/9.10.

I'd hold off on a full system wipe until you've exhausted all possibilities, because although seeing a fresh system is gratifying, sometimes it doesn't work, and you've wasted your time.

Good Luck!

~Xomm

---

### Post by Ijtaba on 2009-11-02
Really dont want to sound rude, sorry if I do but no dice, 
I've tried the boot option about a 100 times, it stops after the splash screen to give a flashing underscore with no response, no magic (SYSREQ) keys or numlock keys....(i did not get to partitioning...no ext3)
 
Yeah im not going to do a full system clean, Ill lose windows that way :D
 
Ive tried about 3 mobos including a P.3, my last solution is to buy a used laptop, only if its model number is on the compatibility list...
 
Woah, thanks lewrockwell, I think your solution just might work, (with the broadband limits and all)
 
To Billv6, really sorry to hear that, 
im sure I read an article from somewhere about Unix history which said some certain hardware may never run some certain OS's because of some small technical errors e.g. unsupported drivers or architechtures. If thats the case then I should stop trying Linux on my current system and try another. Maybe you should try different system if you have another at home, or maybe a friend's :)
 
Thank you guys, Im loving the feedback, will write back when I get a laptop

---

### Post by Xomm on 2009-11-02
Nah, that wasn't really rude.

What you said about architectures made me remember:

Ubuntu's X86 is i686, which still has holes in compatibility with older hardware (according to my linux god/friend.)

I'm also using a Pentium 4, although without a hitch, but I'm just putting this out there.

---

### Post by Ijtaba on 2009-11-18
I did a little research and linux comes in i386, i686, and _x64 architectures.
i386 programs can run on i686 but not the other way round.
same for _x64
The problem I realise now is that I downloaded the i686 and _x64 for my brother.
His copy worked fine because he had the right hardware, but mine obviously didnt as I had the wrong software :/.
I'll try an i386 soon as I get back to cardiff lol
Sorry if I held you up guys.

---

### Post by Ijtaba on 2009-11-27
Update:- 9.10 i386 -> did not work, hung like last time..

---

### Post by om26er on 2010-04-23
This problem still persists in Lucid with tplink wn353g inserted. OMG its been a long time and still its not fixed :(

---

