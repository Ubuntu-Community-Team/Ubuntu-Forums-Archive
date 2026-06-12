---
title: "Need help updating Bios"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by deanom on 2010-11-30
Hi All
I have been having problems ever since trying to install Ubuntu, and still do not have a functioning system. Everything seems to be pointing towards the Hard drive, and/or the drivers for the SATA controller.
Checking the Abit site, it seems that the latest bios update may solve my problems.
However, searching for information about how to go about it in Ubuntu are confusing me.
Can anyone give me a really **simple** explanation of what I need to do.
It may be easier doing this through my laptop, which is running Vista.

Looking forward to finally getting up and running, but need your help.
Thanks

Deano

---

### Post by eriktheblu on 2010-11-30
It's going to depend on your motherboard. Each model can potentially have different methods needed to do the update.

Many manufacturers will only have Windows or DOS compatible update applications. Abit seems to employ a Windows bootable floppy. If you can create a boot disk from your Vista laptop and add the BIOS files to it, that may work. If not, I've heard of people using FreeDOS to update BIOS.

---

### Post by deanom on 2010-11-30
Hi Eriktheblue
Thanks for your quick reply.
I've been looking at the freedos solution, but if I'm honest, I don't understand how.
Similar for the Vista option. How do I go about making the boot disk, and then how do I add the files?
It's the detail that I need.
Deano

---

### Post by eriktheblu on 2010-11-30
I can't help with that a whole bunch, but here's what to look for:

If you have a spare USB thumb drive, look for a guide by searching "freedos thumbdrive". From there, simply add your BIOS file and ROM flashing software to it.

If not, you could try burning a CD with the FreeDOS ISO, then edit the ISO to add the BIOS files. 

Ugliest method: install FreeDOS on your HDD, then copy the files over and run.

I'm an experienced DOS user, but I've never installed nor configured it. FreeDOS looks pretty easy though.

Now to run the BIOS flash program, follow the [guide on Abit site]("http://www.abit.com.tw/page/en/download/guide.php").

---

### Post by pricetech on 2010-11-30
That link should give you all the information you need.  Just make sure you have the right BIOS for your board.  You can quickly turn it into a paperweight with the wrong firmware.

---

### Post by Mark Phelps on 2010-12-01
I don't mean to be critical, but your questions about using Ubuntu and/or Vista to do a BIOS upgrade lead me to believe that you've NOT actually done a BIOS upgrade before.

This is the most risky thing you can do to a PC!!

IF anything goes wrong, you will end up with an "electric brick" -- as, after that, NOTHING will work.

The very first thing you should do, after you have all the items needed, is back up your existing BIOS.  The BIOS update programs generally provide an option to do that.  At least that way, if the upgrade goes wrong, you will have a way to restore the current BIOS.

---

### Post by deanom on 2010-12-01
Hi Mark
Thanks for your warning.
You're right. I haven't done this before, but if the bios needs to be updated, how else is it going to get done?
Sadly, nobody has been able to give me a solution to my problem, which means that either I update the bios, or I have to go back to Windows. If I get it wrong, then I will have change the motherboard, which isn't quite the same thing as needing a new computer. I built this one, so have no fear of the job.
Once again, thanks for the advice.
Deano

---

### Post by QLee on 2010-12-01
[QUOTE=deanom]Hi Mark
Thanks for your warning.
You're right. I haven't done this before, but if the bios needs to be updated, how else is it going to get done?
Sadly, nobody has been able to give me a solution to my problem, which means that either I update the bios, or I have to go back to Windows. If I get it wrong, then I will have change the motherboard, which isn't quite the same thing as needing a new computer. I built this one, so have no fear of the job.
Once again, thanks for the advice.
Deano[/QUOTE]

Most of the time, all you need to flash a BIOS is an old DOS boot disk, often the MB manufacturer will even be able to supply that or something equivalent.

Even if you fail badly, sometimes you can obtain a new EPROM chip and not have to get a new MB, if it's on a socket on the MB, but as Mark mentioned, the flashing program usually has a method to write a backup before you try the flash.

Mark's advice was excellent.

---

### Post by deanom on 2010-12-02
Hi QLee
Thanks for your advice.I'm trying to get hold of a DOS disk now, and will proceed with caution.
Deano

---

### Post by QLee on 2010-12-03
[QUOTE=deanom]...
Thanks for your advice.I'm trying to get hold of a DOS disk now, and will proceed with caution.
...[/QUOTE]
I've not used Vista but older MS operating systems had a method of creating one. 

If I remember correctly, some BIOS have an option that allows a flash and a setting that disables it for safety, that might have to be optioned. I don't have any experience with Abit MB's. 

I think if you proceed with caution (and of course you will after we have all recommended it) you can be successful. Good luck.

---

### Post by Mark Phelps on 2010-12-03
You should check the Abit site for info on your make and model motherboard.  I don't know about Abit, but ASUS provides a key-sequence that allows you to flash the bios without requiring a bootable DOS diskette or CD.  All you need is the new BIOS binary image (usually a .bin file). Abit may have a similar feature.

Also, some motherboards have dual-BIOS, meaning, they have two BIOS chips -- which will allow you to flash one, and if anything goes wrong, reboot but using the other BIOS chip.

---

### Post by CharlesA on 2010-12-03
I've flashed the BIOS on an Abit mobo and it was a royal pain in the butt. I think I had to find a 3.5" floppy drive (and disk!) in order to boot off a dos boot disk to flash the BIOS.

I'm glad that the other mobos that I have allow me to just throw the updated BIOS file on a thumb drive and flash it directly from the BIOS setup program.

---

