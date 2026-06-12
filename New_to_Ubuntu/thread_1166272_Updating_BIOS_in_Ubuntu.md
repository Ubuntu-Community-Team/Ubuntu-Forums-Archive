---
title: "Updating BIOS in Ubuntu"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by rob2uk on 2009-05-21
I have a Gigabyte 965P-DS3 mobo, and don't run a Windows partition.

Is there any way fr me to update my BIOS?

The Gigabyte website only supplies Win32 exe files :(

---

### Post by o0Loco0o on 2009-05-21
There should be a utility that will run off bootable media regardless of what os you are running to flash the bios of your motherboard. Maybe check the manufacturer webpage again and see if you can find something, maybe that includes freedos?

---

### Post by logos34 on 2009-05-21
you have to unzip the files in the .exe and copy them to floppy or cd:

[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

Never done it this way personally, though (luckily mine come as floppy-ready .bin files)

---

### Post by rob2uk on 2009-05-21
> **o0Loco0o said:**
> There should be a utility that will run off bootable media regardless of what os you are running to flash the bios of your motherboard. Maybe check the manufacturer webpage again and see if you can find something, maybe that includes freedos?

You'd think... here's the product page:

[http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2456]("http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2456")

---

### Post by rob2uk on 2009-05-21
> **logos34 said:**
> you have to unzip the files in the .exe and copy them to floppy or cd:

[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

Never done it this way personally, though (luckily mine come as floppy-ready .bin files)

Damn... I'll wait til a 20GB HDD shows up at work, install Windoze on it, and do it that way...

I'll give anything a go, but losing my mobo is too big a risk

---

### Post by logos34 on 2009-05-21
> **o0Loco0o said:**
> There should be a utility that will run off bootable media regardless of what os you are running to flash the bios of your motherboard.

Not always...A lot of mobo manufacturers only offer the WinFash .exe desktop Bios update.  Gigabyte only offers the .exe

It should be against the law not to offer the .bin/dos format

---

### Post by Didius Falco on 2009-05-21
> **rob2uk said:**
> I have a Gigabyte 965P-DS3 mobo, and don't run a Windows partition.

Is there any way fr me to update my BIOS?

The Gigabyte website only supplies Win32 exe files :(

I run a Gigabyte MA790GP-DS4H, and I just recently flashed my BIOS.

1. Downloaded BIOS exe to Ubuntu Desktop.

2. Cut/Pasted onto Flash drive.

3. Double-clicked EXE and extracted contents onto Flash Drive.

4. Rebooted with Flash drive still inserted and used the BIOS Flash utility by pressing the End key during boot-up. I can also get to it by pressing Delete to enter BIOS setup and pressing F8 on the BIOS screen.

5. Flashed BIOS, rebooted and set up BIOS settings again.

I do wish I'd written down my BIOS settings before flashing it, though. I have mine tweaked a bit and it took me a bit to get it set back up the way I like it. 

I prefer flashing the BIOS that way - before I'm in any o/s at all.

Regards,

Didius

---

### Post by rob2uk on 2009-05-23
Thanks Didius Falco, that did the trick (with a slight modification).

I used 7zip to unzip the .exe, which gave me two files - another .exe and an autoexec.bat.

Copied these to a floppy and rebooted and...


> ***CANNOT LOAD BIOS FILE***

Figured I'd see what the output was if I ran the originally downloaded .exe in a Windows VM and voila! It output THREE files - the same two I'd already seen and a ROM file.

Copied these to a floppy, rebooted and flashed quite happily :D

---

