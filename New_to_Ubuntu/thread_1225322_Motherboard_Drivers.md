---
title: "Motherboard Drivers"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by julian.irwin on 2009-07-28
I just put together a new computer. Do I need to install motherboard drivers before I install Ubuntu? Also, if the BIOS message recognizes the right processor name does that mean I probably put it in right? This is my first attempt at putting a system together.

---

### Post by halitech on 2009-07-28
Ubuntu (and linux) doesn't need a bunch of drivers like windows does so if the system is booting and seeing the CP and ram, chances are you have things set up correctly.

---

### Post by Maheriano on 2009-07-28
There's 2 ways to answer this.

1. If you're talking about the actual drivers to use the onboard sound and video, then no. Windows requires it but Linux builds it into the kernel and will just work. There are no drivers for Linux like there are for Windows. Just install and use.

2. If you're talking about the BIOS, which I doubt, then Linux doesn't have the ability to do this without lots of headaches. The easiest way is to install Windows, update the BIOS, format and install Ubuntu.

---

### Post by XCan on 2009-07-28
Although many mobo vendors provide flashing tools from within BIOS. All that is required is to load the image of the bios onto a flash drive or another storage medium.

---

### Post by julian.irwin on 2009-07-28
Cool. Shuttle sent me a DVD that said motherboard drivers on it. I have never done this and assumed everyone put that disc in after getting a new motherboard. Im installing ubuntu right now. Thanks Guys.

---

### Post by BDNiner on 2009-07-28
You would need to identify that hardware that is on your motherboard to determine if you need drivers in ubuntu. Most likely the drivers will be included in the kernel so you will have nothing to worry about. If the BIOS recognizes the processor then you did it right, the computer would not turn on if the processor was installed incorrectly. Try booting with the ubuntu live CD and if everything works on the live CD then it will work when you install the OS.

---

### Post by nhasian on 2009-07-28
hello julian.irwin,

if you get to the POST (Power On Self Test) screen then your cpu is installed properly hehe.  Just make sure that it also shows all the ram, hard disks, and dvd drives.  If this is your first time putting a computer together, i strongly caution you to check two things:

1) the metal standoffs you used to secure the motherboard to the case - make sure that you ONLY used the metal standoffs where it matched the holes in your motherboard.  they should _never_ touch the bottom of the motherboard.  Some cases come with these standoffs already screwed into the case and you may have to remove some of they dont line up with your motherboard.  else you can short out the motherboard.

I've even seen a customer screw the motherboard directly to the case without using the metal standoffs.  needless to say the computer didnt boot at all.

2) make sure that the CPU fan is secured properly to the CPU, and hopefully you used some thermal paste.  otherwise your computer will boot, but it will overheat and lockup.

probably in your bios it will show the temperature of the cpu.  you can make sure that it is within normal parameters.  Also i recommend running some kind of burn in tool where it tests the hard disk, memory, video memory, etc.  you can run the burn in tool overnight and check for any errors in the morning.

Congratulations on your new computer!  I'll be building my new computer when the hex i7 cores come out later this year. 

> **julian.irwin said:**
> I just put together a new computer. Do I need to install motherboard drivers before I install Ubuntu? Also, if the BIOS message recognizes the right processor name does that mean I probably put it in right? This is my first attempt at putting a system together.

---

