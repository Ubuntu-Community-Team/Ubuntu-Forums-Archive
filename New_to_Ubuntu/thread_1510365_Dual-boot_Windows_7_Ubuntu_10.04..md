---
title: "Dual-boot Windows 7 Ubuntu 10.04."
date: 2010-06-15
forum: New to Ubuntu
---

### Post by kenny-an on 2010-06-15
[SIZE=1]Hi!
I bought a new computer a few months ago. I installed Windows 7 and then Ubuntu 10.04(64x) on another[/SIZE][SIZE=1][COLOR=black] partition[/COLOR]. It all e computer worked out fine until a few days ago when all of a sudden Ubuntu freezed. I rebooted and everything seemed fine for a while when it freezed again. When I start Windows after a while I get the blue screen and the computer reboots. Do anyone know that the problem could be? I think there could be some problem with my harddrive, how do i check this? If more info is needed, please ask...

This is my computer setup:[/SIZE]
       Intel Core# i5 Quad Processor i5-750
       Quad Core, 2.66Ghz, Socket 1156, 8MB, 95W, Boxed
       w/fan.
                                                     
       MSI P55-CD53, P55, Socket-1156, DDR3
       DDRIII, ATX, 1xPCI-Ex(2.0)x16, GbLan(Winki), OC Genie,
       DrMOS.

       Corsair XMS3 DDR3 1600MHz 4GB CL9
       Kit w/2x 2GB XMS3 modules, CL9-9-9-24, for Core i5
       and i7, 1.65V, Intel XMP.

       Western Digital Caviar SE16 500GB SATA2
       16MB 7200RPM.

       Sony NEC Optiarc DVD±RW burner AD-7240S
       DVDRW 24x, DL, RAM, SATA, Bulk, Black.

       MSI GeForce GTX 260 896MB PhysX CUDA
       PCI-Express 2.0, "Twin Frozr OC", GDDR3, 2xDVI,
       HDCP.







[SIZE=1]
[/SIZE]

---

### Post by spotted zebra on 2010-06-15
go into windows and get the error code from the crash. google the code or bring it here and ill help you with it. once you figure out what the error code is we test that specific element.

it defiantly sounds like a hardware problem but i am not sure what i could be with out a little further investigation. 

the code can be found in control panel>admin tools>computer management>event viewer

ps nice rig :)

---

### Post by kenny-an on 2010-06-16
Thanks for the reply and yes it is nice if it would work :D
 I've tried to get the error code but now I can't even get into windows and ubuntu won't boot either. A new disturbing thing has also showed up, when I start the computer and the starup screen shows up it is all green and you can barely see the text. My computer is """"ed up.

---

### Post by cotcot on 2010-06-16
Try to boot ubuntu from the install CD. If this works than check if you can see your files on the hard drive(s). 

Maybe the supergrub repair CD could help. [URL="http://beginlinux.com/server_training/server-managment-topics/1069-supergrub"][COLOR="Red"]Super grub CD[/COLOR]
[/URL]

---

### Post by Mark Phelps on 2010-06-17
> **kenny-an said:**
> T... A new disturbing thing has also showed up, when I start the computer and the starup screen shows up it is all green and you can barely see the text. My computer is """"ed up.

Suggest you boot two times, first, from the Win7 DVD, and second, from an Ubuntu CD.  If you get the same color problems both times, we can rule out video drivers and presume that your video hardware has gone bad.  

Plus, when you boot from the Win7 DVD, it doesn't actually boot into Win7 -- so it's not using the video drivers you installed.

---

### Post by mastablasta on 2010-06-17
Had a crash in WinXP that borked the system. Turns out the new cable leading from Hard disk to motherboard was faulty. replaced it and no problems since...
 
So if you can go into motherboard and you do not hear any strange beeps then it can be GPU, Hard disk or cables. If you can boot form CD then GPU is ok, so you are left with Hard disk or cable. turn off the computer, change the cable,  boot it with CD and try to access the hard disk.
 
Note most motherboards do a basic RAM check when you start. if it's not enabled you can enable it in BIOS. Check the manual on how to do it. Also check the motherbaord manual if you have any strange beeps to see what they mean.

---

