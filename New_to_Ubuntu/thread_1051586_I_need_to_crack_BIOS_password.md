---
title: "I need to crack BIOS password"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by cnico88 on 2009-01-26
I have recently added 2GB of Corsair DDR3 Memory (PC 12800) 1600 MHz and I noticed in all the software that the RAM is under clocked at 1066MHz. I need to go back into the BIOS and change it but I am asked for a password as soon as I try to get into the BIOS. If I don't provide the password I can still get in and see the BIOS, I just can't save the changes. I read online and I see methods of either typing something into the command prompt or removing some kind of jumper on the board. I already tried popping out the battery for a few minutes but the password is still there. I run on an Intel DX48BT2.

---

### Post by LowSky on 2009-01-26
Pop out the battery and then you need to pull the jumper, to do so you will need to know which one it is, hopefully you have the manual

---

### Post by LostMagix on 2009-01-26
Google your motherboard to see if there is a reset button on it, if not then remove the battery on your motherboard after unplugging the power cable., then simple put the battery back in.

This will reset your BIOS


edit:sorry, i didnt see that you removed the battery..

Did you unplug the board when you took the battery out?

---

### Post by niteshifter on 2009-01-26
Hi,

Popping the battery out for a few minutes won't get it. It can take much longer than that. That board sports a CMOS jumper and the manual for it is [here]("http://support.intel.com/support/motherboards/desktop/dx48bt2/sb/CS-028496.htm").

---

### Post by sandyd on 2009-01-26
sigh... well b/c/ you asked for it.....

use killcmos.

i hope your motherboard contans a working copy of the bios so that it can restore it after you blow it into a million bits using killcmos.

---

### Post by cnico88 on 2009-01-26
I will try to remove the battery and the power cable and see what happens.

---

### Post by jerome1232 on 2009-01-26
> **niteshifter said:**
> Hi,

Popping the battery out for a few minutes won't get it. It can take much longer than that. That board sports a CMOS jumper and the manual for it is [here]("http://support.intel.com/support/motherboards/desktop/dx48bt2/sb/CS-028496.htm").

Why not just use the cmos jumper as per this post? You simply move the jumper that the manual indicates over a pin for a few seconds and then move it back.

---

### Post by cnico88 on 2009-01-27
Do I move the jumper while the computer is turned off and do I boot without it or how? Please explain in a little more detail. 

I tried to remove the CMOS battery and left the computer like that unplugged overnight and it looks like the date was reset but the password is still there.

---

### Post by jerome1232 on 2009-01-27
while it's off, just move it over, wait like 4 seconds, then move it back.

I wonder does this motherboard have some sort of factory default password, dose it say anything about that in the manual?

---

### Post by cnico88 on 2009-01-27
I fully removed the BIOS with the jumper method and now my settings have been reset to factory settings. I need to reset them to regular settings. Here are the screen shots that I got. I need to run CPU @ 2.5GHz and RAM @1600MHz. Please let me know how to do this since I have never done it myself and I don't want to overclock either.

[IMG]http://i37.photobucket.com/albums/e67/cnico88/1-9.jpg[/IMG]

[IMG]http://i37.photobucket.com/albums/e67/cnico88/2-2.jpg[/IMG]

[IMG]http://i37.photobucket.com/albums/e67/cnico88/3.jpg[/IMG]

[IMG]http://i37.photobucket.com/albums/e67/cnico88/3.jpg[/IMG]

PC SPECS:

CPU: Intel Core 2 Quad Q9300
Motherboard: Intel DX48BT2
Video Card: Visiontek ATI HD3870 X2
Hardrive: WD Velociraptor 300 GB
RAM: 4GB (4x1GB) CORSAIR XMS3 1600 MHz DDR3 PC 12800
Power Supply: Corsair 1000 Watt

---

### Post by LowSky on 2009-01-27
wher it says memory frequency, that needs to change to 1600 MHz

EDIT, you might not be able to run the Memory that fast as the FSB for the Processor is 1333MHz

If the PC doesnt boot after the change, no worries just pull the CMOS battery again

---

### Post by cnico88 on 2009-01-27
> **LowSky said:**
> wher it says memory frequency, that needs to change to 1600 MHz

EDIT, you might not be able to run the Memory that fast as the FSB for the Processor is 1333MHz

If the PC doesnt boot after the change, no worries just pull the CMOS battery again

[IMG]http://i37.photobucket.com/albums/e67/cnico88/Capture-1.jpg[/IMG]

Are you sure? Because it is advertised otherwise. Also how do I clock the CPU to its normal frequency?

---

### Post by LowSky on 2009-01-27
> Are you sure? Because it is advertised otherwise. Also how do I clock the CPU to its normal frequency?

Dude use smaller pictures....lol
and im sure
[http://www.intel.com/products/processor/core2quad/specifications.htm](http://www.intel.com/products/processor/core2quad/specifications.htm)

says it here too
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115043](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115043)


Like I said before go to  memory frequency and change it to 1600
And read your Motherboard Manual, it tells you how to change settings and other cool stuff.

---

### Post by cnico88 on 2009-01-27
> **LowSky said:**
> Dude use smaller pictures....lol
and im sure
[http://www.intel.com/products/processor/core2quad/specifications.htm](http://www.intel.com/products/processor/core2quad/specifications.htm)

says it here too
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115043](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115043)

So how do I set it to 1333MHz and CPU to 2.5GHz? Do I increase the voltage or just the multiplier?

---

