---
title: "Best way to install on a new HD for an old laptop"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by frogo on 2011-05-31
Hello 

I have recently bought a new HD for my old Acer Aspire 1350 (from around 2003?). My hope was to seamlessly install from a USB stick. Alas, it seems the machine won't boot from USB. As I'm considering my options and before launching in a series of maddening attempts, I'm wondering if I could get a few words of wisdom as to which might be the best way to proceed. 

Options I'm considering are: 

1- make a bootable USB from an older stick (I don't know if I'll find one old enough or that's large enough, or if that's worth the bother)
 
2- make a bootable CD (I'm not too sure how to go about that) 

3- install ubuntu on my new HD using another computer (making the new HD external), then perhaps reinstall if it works once placed back into the ACER machine 

4- update the BIOS on the ACER machine (scares me)

Are there other, better options? and which should I try first? I have to say I'm rapidly becoming clueless when engaging configuration of any sort. 

Also, given all this, is there any particular version of Ubuntu I should be looking at (I'll go for 10.04 in the mainline edition blindly otherwise).

many thanks

---

### Post by Joe of loath on 2011-05-31
Burn a CD. It's the easiest solution, put the CD in the drive of your main PC and click on the .iso :D

Also, on a PC that age, Lubuntu will be what you're looking at.

---

### Post by jerrrys on 2011-05-31
burning a cd is the the easiest solution.  have you snooped around in BIOS to make sure there is no boot option for a usb?

---

### Post by Mark Phelps on 2011-06-01
> **frogo said:**
> 1- make a bootable USB from an older stick (I don't know if I'll find one old enough or that's large enough, or if that's worth the bother)
A BIOS that old is almost certainly NOT going to support booting from USB.  So, doesn't matter what you make, it's not going to boot.
 
> 2- make a bootable CD (I'm not too sure how to go about that) 
The Ubuntu Desktop CD is a bootable disk -- you don't have to do anything special to it.

> 3- install ubuntu on my new HD using another computer (making the new HD external), then perhaps reinstall if it works once placed back into the ACER machine 
Bad idea -- because it will install the drivers for THAT machine, not for your machine.

> 4- update the BIOS on the ACER machine (scares me)
SHOULD scare you -- BIOS updating can NOT be done from another machine, and should only be done when necessary.  IF you make a mistake, you turn your machine into an electric "brick".

> Are there other, better options? and which should I try first? I have to say I'm rapidly becoming clueless when engaging configuration of any sort.
Boot from an Ubuntu in LiveCD mode and TRY it out, first.  That will show you how well it detects your hardware and loads the proper drivers. 

> Also, given all this, is there any particular version of Ubuntu I should be looking at (I'll go for 10.04 in the mainline edition blindly otherwise).many thanks

Would choose 10.10, myself.  NOT a fan of Unity.  And, while 11.04 DOES provide you a way of going back to the Gnome desktop, 11.10 will not.  Also, still getting LOTS of error reports on 11.04.

---

### Post by coffeecat on 2011-06-01
> **frogo said:**
> 
3- install ubuntu on my new HD using another computer (making the new HD external), then perhaps reinstall if it works once placed back into the ACER machine 

This is a good and valid option which many people have used. Hardware drivers are **not** an issue since Ubuntu autodetects hardware on bootup and loads the appropriate kernel modules (drivers) as necessary. Actually, there is one important exception to this rule. Don't install any proprietary video drivers until you have put the HD back into the machine in which it is going to work. If you install a nvidia proprietary driver (say) and then move the HD to a machine with ATI graphics, the xserver will fail. Ditto, vice versa. But video drivers are a special case.

However, one important caveat if you decide to do this. You need to install grub to the mbr of the HD you are going to transplant back into the Acer. It will be sda once it's in the Acer but will appear as sdb or sdc (or something) if it is atttached as an external to the machine you use for installing. If you know your way around grub and use the advanced/manual ("something else" in Natty) option in the installer so that you can designate where grub goes, you'll be OK. If you don't, you'll have grub installed to sda of the host machine and you won't be able to boot up when you remove the external HD - not until you repair the bootloader for that machine, that is.

---

### Post by mikechant on 2011-06-01
> Also, given all this, is there any particular version of Ubuntu I should be looking at (I'll go for 10.04 in the mainline edition blindly otherwise).many thanks 

and the reply says

> Would choose 10.10, myself. NOT a fan of Unity.

I'd go for 10.04 LTS (long Term support) as it is supported until April 2013. 10.10 is only supported until April 2012 (only 10 months away!).

---

### Post by Allavona on 2011-06-01
Most older machines that don't boot from a USB drive automatically can be "convinced" that the USB drive is a standard HDD.

Try powering down completely and stick in the USB drive. turn on the computer and go into bios. 

Once in bios see about editing your boot order. You should see your main HDD and the CD/DVD drive, along with the USB stick. You may have to use the arrow keys to highlight your main HDD and press enter to see the options for boot. 

On most systems this works once, as bios reverts back to the default boot order, forcing you to do these steps over again when needing to boot from USB again.

---

### Post by walt.smith1960 on 2011-06-01
> **Joe of loath said:**
> Burn a CD. It's the easiest solution, put the CD in the drive of your main PC and click on the .iso :D

Also, on a PC that age, Lubuntu will be what you're looking at.

This is what I did with a 2002 vintage laptop. Lubuntu installed and works perfectly. How much RAM do you have?   Lubuntu.org says 128 meg. minimum. I'd want more....256 minimum.  I added a 256 meg. chip to my machine to bring it to 512.  The DIMM cost < $10 off Ebay.  It works very well for everyday stuff except flash videos.

---

### Post by marcoftheknight on 2011-06-01
The Best answer to your question trust me:

Make a bootable CD and follow these instructions:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

use infraredRecorder free opensource burning program.

to boot from cd you will have to go to boot menu and select it when your ocmptuer is starting up.

Thanks

---

### Post by JohnBN on 2011-06-01
Just did something similar...
 
Best option is to boot from the Install CD made from the ISO download.  Wham, bam, done deal.  No heartbreak.
 
If all (and I do mean ALL) else fails, this is what I had to do:
 
[http://ubuntuforums.org/showthread.php?t=1772925](http://ubuntuforums.org/showthread.php?t=1772925)

---

### Post by sbraz on 2011-06-01
> **frogo said:**
> it seems the machine won't boot from USB.

yes you can, with "plop".

[COLOR="Red"]homesite[/COLOR] [http://www.plop.at/](http://www.plop.at/)
[COLOR="red"]download[/COLOR] [http://www.plop.at/en/bootmanager.html#download](http://www.plop.at/en/bootmanager.html#download) (current version is "Plop Boot Manager 5.0.12 (stable)")

download an image, burn a cd, boot from cd, the cd should redirect the process to usb drive.
should it fail you can force usb 1.1 mode or disable ohci (i don't remember atm).

it works with my pentium 233mmx too. ;)

---

### Post by Sylslay on 2011-06-01
Have a look if in boot option in BIOS is "HDD-USB".

If none, than:



1. Try use Ubuntu 10.04 (I have 2 lapotps from 2004 and they perform very well with 756 and 1GB ram on Ubuntu 10.04. Used 10.10 on seconf laptop, but than back again to 10.04, is better and more easy to configure on this laptop.

2. Plop is great work around if Yours laptop booting only form Cd and Cd-ROM is [COLOR="Black"]_[COLOR="Black"][COLOR="Red"]almost [/COLOR][/COLOR]_[/COLOR]Dead.

---

### Post by frogo on 2011-06-01
Hi,

thanks all for the input so far. Here's where I am at the moment, it's not far... and the CD install meets problems for now.

1. USB:

I gave up on finding an old USB, the machine just can't boot like that at the moment. (It's not only the boot order, it's possible to boot from 'removable' something --- can't recall the term --- but that doesn't seem to include flash drives, or not those I have).

I thought the only way to change that might be to update the BIOS, which I'm still not desperate enough to try. But the PLOP thing sounds very interesting.  I might go there next.

2. DVD

Downloaded a few ISOs (10.04, 11.04 and the latest Lubuntu). I'm trying to install 10.04 from a disc. The internal drive, however, is past its time (no surprise for an ACER machine in my experience). So I'm using an external CD/DVD drive and fortunately that seems to work, well to a point...

Problem:
Now the problem is that if I try to run Ubuntu from the CD (without installing), the machine turns off after a while (about 30 secs), while the DVD-drive is still spinning.
Between the moment it leaves the initial Ubuntu screen (keyboard = little man) and the moment when the computer turns off, all I see on screen is a couple of central groups of zigzaging lines (white and red..). It's the Ubuntu logo, but it looks like it's been drawn by a 3 year old in Paint. 
For all I recall, the machine doesn't beep or send any signal, it just turns off.

I'm trying the other items in the initial menu (so I enter the menu list in the first stage). At the moment, it's testing the memory, which seems fine (about 512Mb).
I assumed that the problem with this machine concerned the hard drive but I start wondering whether something else is not amiss. Bear with me, I *might* actually try and see whether I can install my old Windows 98 just to see whether the machine works...

3. HD

I don't think I'll have the patience to try too many things and eventually I'll probably try to install on the HD with another machine. Still have to do some reading about that, and the tips mentioned in some of the replies are quite useful already. If I can't salvage the machine this time, at least I'll have a portable bootable drive :)

Hope to be able to report some progress eventually, many thanks again and keep'em coming 

(sorry, I can see I'm a bit verbose...)

---

### Post by jerrrys on 2011-06-01
on your dvd install. a black screen does not necessary mean that your computer has turned off.  give it a few minutes

---

### Post by frogo on 2011-06-01
> **jerrrys said:**
> on your dvd install. a black screen does not necessary mean that your computer has turned off.  give it a few minutes

I'm giving it a try. But it's not just a black screen, it really does look, sound and feels like it's powered down.

Actually, now it won't even go into the boot sequence, just turns off (or seems to) where the sequence should start. I'll leave it alone for a while.

---

### Post by frogo on 2011-06-02
> **frogo said:**
> I'm giving it a try. But it's not just a black screen, it really does look, sound and feels like it's powered down.

Actually, now it won't even go into the boot sequence, just turns off (or seems to) where the sequence should start. I'll leave it alone for a while.

Now this is sad, in ways... 

I could install Windows 98, confirming the machine is OK (i had forgotten how all about 98 was so pathetic). Against all odds, the internal CD drive is still good. 

Installation problem persists: 
I've tried installing Ubuntu over Win98 from the CD but the same weird graphic problem persists (scrambled gross lines and shutdown). 

I guess now I'll first try WUBI... then another version of ubuntu (apparently, I can't manage burning a good CD for lubuntu so I'm considering Xubuntu). 

Taking away the HD on the side is still back up plan. But even if that worked I'm not sure I'll not have the same problem that seems to be graphics related(?) It's all I can do to not feel I'm entirely wasting my time now...

---

### Post by frogo on 2011-06-03
> **coffeecat said:**
> This is a good and valid option which many people have used. Hardware drivers are **not** an issue since Ubuntu autodetects hardware on boot up and loads the appropriate kernel modules (drivers) as necessary. Actually, there is one important exception to this rule. Don't install any proprietary video drivers until you have put the HD back into the machine in which it is going to work. If you install a nvidia proprietary driver (say) and then move the HD to a machine with ATI graphics, the xserver will fail. Ditto, vice versa. But video drivers are a special case.

However, one important caveat if you decide to do this. You need to install grub to the mbr of the HD you are going to transplant back into the Acer. It will be sda once it's in the Acer but will appear as sdb or sdc (or something) if it is atttached as an external to the machine you use for installing. If you know your way around grub and use the advanced/manual ("something else" in Natty) option in the installer so that you can designate where grub goes, you'll be OK. If you don't, you'll have grub installed to sda of the host machine and you won't be able to boot up when you remove the external HD - not until you repair the bootloader for that machine, that is.

I finally gave up on installing directly on the ACER. 

I took the hard drive and installed Lubuntu on it using another machine. Your warnings were useful. I didn't want to take a chance so I took away the hard drive of the machine used to perform the installation. So the HD I was installing on was the only one available and Grub went to the right mbr. The HD was hooked through USB external casing (because it's an IDE) but that didn't seem to be relevant. 

The install went through. I have Lubuntu on the HD of the ACER. I can even get to the login screen...

But so far, I haven't been fast enough to even log in once before the machine shuts down. 

I have now to figure out why the ACER shuts down systematically.

Many thanks for all the replies! Although I'm probably not done with the ACER, I'll mark the thread as solved; since unless something magical happens, I'll go for the same method if I have to reinstall. It took a little over an hour and I had been at it for 4 days with other attempts.

I meant to say: some of the suggestions I didn't use seem very interesting and it's very useful to have learnt about them (thanks for various links!), even if I couldn't apply some of the suggestion in this case.

---

### Post by Joe of loath on 2011-06-04
Is it overheating? Also, my P4 Asus occasionally locks up/shuts down as the processor socket is dodgy, and some of the pins lose connection.

---

### Post by frogo on 2011-06-04
> **Joe of loath said:**
> Is it overheating? Also, my P4 Asus occasionally locks up/shuts down as the processor socket is dodgy, and some of the pins lose connection.

i can't be sure, the fan works well, it's not perceptibly hot... 

The fan is active when shutting down, but for all I remember (this machine sat on a shelf for 3 years) that's always been part of the shut down sequence with this machine: tell to shut down + fan gets a boost + click = it's off. It really feels like something at start up just sends the shut down command. 

I've read (old) reports of overheating. I've seen mention of special drivers (ePower something?) I've seen allusions to boot options.. 

But the overheating reports were not only under Linux, also under windows. I had to install Windows 98 earlier this week and there was no such problem. Although the graphic rendering was really bad, if that tells anything 

That's all beyond my depth really


EDIT: 

well after much pain and shooting in the dark, I've finally managed finding a boot option that seemed to work. I just removed 'quiet splash' (and didn't replace it with anything) and I could get to the login screen... it stayed around 15 minutes without turning off and I ended up shutting down myself. Err... now, well... I can't remember the login password... teaches me well to install ubuntu at 1am in a hopeful way so that 2 days of struggles with boot will have wiped out the password from my memory

---

### Post by sbraz on 2011-06-05
> **frogo said:**
> I just removed 'quiet splash' (and didn't replace it with anything) and I could get to the login screen.
:shock:

---

### Post by frogo on 2011-07-05
> **frogo said:**
> Hello 

I have recently bought a new HD for my old Acer Aspire 1350 (from around 2003?). My hope was to seamlessly install from a USB stick. Alas, it seems the machine won't boot from USB. As I'm considering my options and before launching in a series of maddening attempts, I'm wondering if I could get a few words of wisdom as to which might be the best way to proceed. 

Options I'm considering are: 

1- make a bootable USB from an older stick (I don't know if I'll find one old enough or that's large enough, or if that's worth the bother)
 
2- make a bootable CD (I'm not too sure how to go about that) 

3- install ubuntu on my new HD using another computer (making the new HD external), then perhaps reinstall if it works once placed back into the ACER machine 

4- update the BIOS on the ACER machine (scares me)

Are there other, better options? and which should I try first? I have to say I'm rapidly becoming clueless when engaging configuration of any sort. 


Also, given all this, is there any particular version of Ubuntu I should be looking at (I'll go for 10.04 in the mainline edition blindly otherwise).

many thanks

Hi... finally!

replying from the ACER machine running Lubuntu 10.10. This is the first boot, so far so good...

Option 3 worked with Lubuntu

1. burn Lubuntu ISO

2. Remove HD from other machine (so I wouldn't have to worry about where Grub goes with more than one HD)

3. Plug me brand new old school ATA drive in an external case via USB (fortunately the machine for the install was new enough to be capable of booting from USB without intermediate steps)

4. Boot

5. Install Lubuntu (went smoothly, I had to have a live internet connection for the network config; I didn't bother trying to be smarter than I am with partitions and there's just one ext4 and one swap -- I guess I can still come back to this in time; GRUB was placed on master)

6. Reboot (failed somehow on the host machine, I think because of its Intel Integrate Graphics; a couple of libraries said to be not found too, I don't know if it matters and if it's peculiar to the distro install)

7. turn off, take away ATA HD from case, place it into ACER machine, boot and voilà!

Many thanks for all the input, this has been quite eventful and long winded as I didn't have much time to spare, just hope it will be stable enough now.

---

