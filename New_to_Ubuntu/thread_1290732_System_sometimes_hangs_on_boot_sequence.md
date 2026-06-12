---
title: "System sometimes hangs on boot sequence?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by glenduncanscott on 2009-10-13
I recently installed Ubuntu 9.04 64bit Desktop Version without a problem. I boot the machine and sometimes it loads into Ubuntu and other times it does not. Normally what happens when it does not load properly is after the Ubuntu loading bar graphic has finished the screen goes black and the white cursor appears, then nothing. You can move the cursor around but you eventually have to switch the computer off and restart again. It just happens before the music jingle sounds. If anyone has experienced this problem or knows how I could fault find what is happening I would be extremely grateful. 

Further details of system can be found here:
[https://wiki.ubuntu.com/LaptopTestingTeam/MedionMD96442](https://wiki.ubuntu.com/LaptopTestingTeam/MedionMD96442)

---

### Post by 123456789123456789123456 on 2009-10-13
> **glenduncanscott said:**
> I recently installed Ubuntu 9.04 64bit Desktop Version without a problem. I boot the machine and sometimes it loads into Ubuntu and other times it does not. Normally what happens when it does not load properly is after the Ubuntu loading bar graphic has finished the screen goes black and the white cursor appears, then nothing. You can move the cursor around but you eventually have to switch the computer off and restart again. It just happens before the music jingle sounds. If anyone has experienced this problem or knows how I could fault find what is happening I would be extremely grateful. 

Further details of system can be found here:
[https://wiki.ubuntu.com/LaptopTestingTeam/MedionMD96442](https://wiki.ubuntu.com/LaptopTestingTeam/MedionMD96442)

there is a log file called crash report.  it is located under /etc/logs, I believe.  Find it, after the next suscessful boot.  List the contents of the file of the date of the failed boot.  That could help identify the problem.  I had a simuler problem, it turned out to be a bad install, there was some damage to the install disk, not enough to completely cause a failure on installation, but some of the files got corrupted as a result.  That could be the problem, or it could also result from a video driver issue, the video driver being used by the system may not be fully compatable with your video card, Bad Ram, could also cause lock ups.  Another useful tool is to have the system report in text mode everything that happens at startup.  I have to do some research, but you can inform GRUB and Ubuntu to forgo graphical boot, and list all components.  That could help identify if there are hardware issues, or software issues in play.

---

### Post by glenduncanscott on 2009-10-14
Thank you for your helpful input...

The last messages that appear in the log before the system hangs is...

/var/log/kern.log

Oct 14 22:16:11 kernel: [   29.226109] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 14 22:16:11 kernel: [   29.226112] Bluetooth: BNEP filters: protocol multicast
Oct 14 22:16:11 kernel: [   29.245859] Bridge firewalling registered
Oct 14 22:16:12 kernel: [   30.424070] ppdev: user-space parallel port driver

No problems occur when using the Live CD, so there is either something wrong with the installed software or the hardware.

I tried removing the 'NVIDIA accelerated graphics driver (version 180) [Recommended]' but system still hangs

Is there any way to test the RAM on 64 bit systems? 

In addition the system has also overheated a couple of times resulting in an automatic shutdown. This is normally occurs when the system (not under excessive load) is used for four hours or more.
  
Oct 14 02:15:11 kernel: [   94.500065] Clocksource tsc unstable (delta = -154009497 ns)
Oct 14 02:38:44 kernel: [ 1507.133032] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 14 03:13:26 kernel: [ 3588.850050] ACPI: Critical trip point
Oct 14 03:13:26 kernel: [ 3588.850067] Critical temperature reached (99 C), shutting down.
Oct 14 03:13:27 kernel: [ 3589.984169] wlan0: disassociating by local choice (reason=3)

---

### Post by 123456789123456789123456 on 2009-10-17
There is a way to test ram, under the live cd, is an option to check memory, it runs mem86.  This checks the ram.  One thing that is woring me though is the processor over heat.  Over heating of processors can be caused by the heat synk, or fans, not working correctly, like the fans not coming on, or sudenly stop spinning, causing the processor to over heat, causing protection mode to enable, and shut the computer off.  Sometimes the CPU itself could be damaged, or even if the computer is not in a open area, not allowing the heat from the cpu to be vented could also cause over heating.

Over heating of the CPU can cause freez ups.
Boot the computer, go to BIOS, and look at the PC health section, this gives a temp range for the CPU.  The temp should stay very close to the original temp that you note when booting into this menu.  If there are any dramatic increases in heat temp, for instance it starts at 50c, then jumps to 70c, then continues to rise, in such jumps, and never cools down.  This indicates a problem somewhere.

Make sure you hear the sound of the fans.

From what you posted, it sounds like a processor overheat may be the culprit.  I would note that the BIOS safe temp was not reached, it was Ubuntu that trigered the shutdown, from the cpu temp.  I don't know how to change that temp safety in Ubuntu, but 99 degrees c is a bit hot to say the least.
you are looking at 131 degrees F.  most BIOS safe range is at 100 to 110c

If the CPU at unsupported times is getting very hot, it more than likely will cause freez ups.  expecially if it freezes up on a restart from the system shutting down.

If so we just need to figure out what is causing the over heat and fix it.

---

### Post by glenduncanscott on 2009-10-18
I used the Live CD as you suggested to test the RAM, unfortunately after only an hour the system overheated and shut down twice. This particular test appears to overheat the system faster than any other software application I have used.

I checked the BIOS but there was no option to check the PC Health to monitor temps. Although I followed the guide below which gave me some capability...

[http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/](http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/)

The fan sounds like it is on. 

I think it's time to open up the system and carry out a clean/visual inspection...

[http://ubuntuforums.org/showthread.php?t=452475](http://ubuntuforums.org/showthread.php?t=452475)

---

### Post by 123456789123456789123456 on 2009-10-18
ok, It deffinatly sounds like the processor(CPU) is going bad.  Thing to do to test this.  Open up the case, use one of those compressed air cans to clean out all the dust inside the computer, turn on the computer, guage visually to see if the CPU and case fans are operating, and see that none of them all of a sudden stop working.  Just for kicks, run the ram test again, if the computer does turn off.  Then the CPU is physically unable to handle the load being pressed upon it.  You can try reducing the overclock spead/rate/number, if your BIOS allows that.

Explanation
Overclock, On most computers the processor is set at lets say normal rate being overclock 1, which would be normal cpu speed, lets say 1ghz for an old model, however they set the overclock to 2 or 3, which is 2x or 3x normal speed, so if overclock is 3, then the processor is running at 3ghz, unfortiantly, this also even though it increases performance, and speed, decreases the life of the CPU, it is no longer able to cope with normal processes.  If you can change the over clock speed, set it to 1, or even -1.  This will slow the computer down alot from what you are used to.  But it should also allow the computer to perform longer before the CPU overheats.  This will also allow you to confirm my diagnoses, If the CPU is bad, or going bad, you will need to replace the cpu.

---

