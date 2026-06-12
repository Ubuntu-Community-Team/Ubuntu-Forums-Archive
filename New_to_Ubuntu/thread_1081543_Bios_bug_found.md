---
title: "Bios bug found"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by humbug01 on 2009-02-26
Hi all,

I'm running Ubuntu 8.10 with no real problems, but I get a bug message whenever I boot into Ubuntu. The message goes by too fast on the screen for me to read except "bios bug found" (it appears before the "Ubuntu" screen with progress bar).

I routed the output of "dmesg" to a file and found what I believe is the message:

[    0.384228] PCI: BIOS BUG #0[00000031] found

This is a custom built new desktop with: ASUS P5Q Pro motherboard and Intel E8400 CPU. The bios was updated in December when I put the system together.

This is not urgent, since Ubuntu does work fine but a bug message, well, bugs me! :)

Any ideas on the cause or fix? Thanks in advance,

Steve

---

### Post by LowSky on 2009-02-26
Bios bugs ar enot kernel bugs, something from BIOS is either corrupted or not working correctly, there is a way to turn off the notification, but maybe upgrading/downgrading your BIOS would be best

---

### Post by humbug01 on 2009-02-26
Thanks. Maybe I'll post this in the ASUS forum and see what they say...

Best,

S

---

### Post by blueridgedog on 2009-02-26
Typically you will see those messages when the kernel is noticing a given bug and adopting a given work around.

---

### Post by humbug01 on 2009-02-27
Thanks. My BIOS is the latest version (1611) and you'd think they would get it right by this stage of the game. If you go to the ASUS site you notice that they make what looks like hundreds of motherboards. Maybe they just don't put the effort into perfecting each one and their BIOS programs....

It seems that Ubuntu does indeed cope with the bug since I can boot and wake from suspend just fine. Impressive!

Steve

---

### Post by Sierra 99 on 2009-05-14
When trying to install ubuntu, I'm receiving the following message and then the system hangs. [COLOR=Red]0.0556244 Pci: Bios bug #0 (00000031) Found[/COLOR]
I've tried upgrading/downgrading my bios without success. The cd works fine in other computers and installs fine as well. 

i have an Asus P5QL - Pro motherboard with the latest bios update. 

Any suggestions?

---

### Post by LarryMi on 2009-05-23
Sierra99,

[Try this link]("http://ubuntuforums.org/showthread.php?t=1021549&page=2").  Notice the last comment from Sesshomaru dated 12/29/008.   I have this problem too, but not sure how to move to connector.

Good luck,
Larry

---

### Post by rob2uk on 2009-05-23
Asus mobos are one of my pet hates - the only thing I hate working on more are Dells

Was fitting an Asus board for a customer last week - the header for the rear case fan was right at the front of the board, and the header for the front panel (power/HDD LEDs, power button, reset switch) was at the back, blocking a PCI slot.

Basically, the customer had a choice of being able to turn his PC on OR use the slot...

Slightly off topic, maybe, but it gives you some idea of the company's design and test procedures...

---

### Post by LarryMi on 2009-05-24
I can't figure this one out, but I installed the 64 bit version, and now this message disappeared.  I now boot with absolutely no errors.  This version also plays my HD audio, when the 32 bit version required manually modifying the file alsa-base.conf.

---

### Post by humbug01 on 2009-05-31
I'm running 64 bit Jaunty now and don't get the message about the bug either.

Steve

---

### Post by Sierra 99 on 2009-05-31
I tried installing the 64bit as well. I never received the bug message but it would load to the desktop screen but that was it, I had no mouse cursor, icons, etc. The disk worked fine in another computer. Any ideas?

---

### Post by nandemonai on 2009-05-31
I like Asus boards. Never had a problem with them myself. /shrug

On topic though, I've seen these BIOS issues before. Asus leave a lot to be desired in the BIOS department I'll admit that.

---

### Post by humbug01 on 2009-06-01
Hi Sierra,

I'm just going to throw out ideas but too much a newbie to be reliable here....

A CD that works on one machine might not work reliably on another. I've seen this several times with Ubuntu installation disks already. Try re-burning the .iso on a different machine at a slower setting.

I've installed Jaunty on about 5 (extended) family machines so far with no problems. In all cases but one, I've done a minimal install to the CLI then built up the desktop (Gnome on most, XFCE on an older laptop) and other software from that base. It requires a lot of reading and some tweaking but it's worked out great for me. The default desktop installs 900+ pieces of software while minimal is around 200. This may have nothing whatsoever to do with your problem, but I thought I'd mention it.

H.

---

### Post by bgiannes on 2009-06-03
i've been having this error for a time, but as of last night the machine goes from the error to a kernal panic, i can't boot the machine everytime.  Every 10th time it does start (/w the error message) but the system is unstable.

this HTPC build is 45days old 
Asus turbo
CORSAIR Dominator 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 
E8400

i have both 32bit and 64bit installed and have the same problem, even trying to boot a CD results in a kernal panic.

a memory test reported lots of error....  is this bad memory or bad memory setup, MB the settings post on the ASUS site don't work?  

<update>
there is a new bios update (dated 5/22/2009)... i'll try it tonight...

:(

---

