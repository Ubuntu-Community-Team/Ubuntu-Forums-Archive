---
title: "Problems installing 10.10 from usb - Invalid RT chipset detected"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by cheekybuddha on 2010-11-17
Hello everyone,

I seek some assistance in installing Ubuntu Desktop 10.10 on a laptop (core 2 duo, 1gb ram) with a broken DVD drive.

I am trying the usb install as I can't use cd/dvd. I have tried various flavours but all attempts seem to hang just before login.

1st attempt: 
Use Startup Disk Creator from my other laptop with Ubuntu Desktop on a freshly formatted (FAT32) 4GB stick with 10.10 Desktop iso.
This hung at screen saying "Try" or "Install"

2nd attempt:
Use Unetbootin-linux-494 to create Ubuntu 10.10_NetInstall on another freshly formatted 4GB stick (version provided by Unetbootin)
This went throught the familiar text-based setup install. I chose to use the whole 140GB hard drive and install Ubuntu Desktop.
Everything completed and reboot requested.

I removed the stick and rebooted: result was a blinking cursor in top left of black screen.

So I thought I needed to reboot from the stick again to try an finish off installation(?). This got me as far as the splash screen with the red dots. There it hung again.

Tried again with stick in - got as far as splash screen with red dots, this time a mouse cursor appears! Still, not going any further.

Tried several more times, and even removed the dvd drive in case it was getting stuck trying to detect it. Result is always sticking around screen with red dots before login.

After leaving for a while the laptop switches off by itself completely!

I found this thread [http://ubuntuforums.org/showthread.php?t=1560792](http://ubuntuforums.org/showthread.php?t=1560792) which sounded very similar, but the solution there was finally to boot from cd, which I can't do.

On hitting escape at the splash screen I see this output:
```
[   20.733879] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   20.733912] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 132501/9576448 files, 1178469/38304768 blocks
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                               [ OK ]
                                                                                                               [ OK ]
```I haven't tried boot switches because I'm not sure where I need to add them. :P

Any suggestions would be appreciated.

TIA,

d

---

### Post by sikander3786 on 2010-11-17
Did you check the integrity of the downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you tried the mentioned boot parameters on that other thread like acpi=off, nomodeset, xforcevesa etc?

Did you try with some other USB drive?

---

### Post by cheekybuddha on 2010-11-17
Hi,

Thanks for your response.

Did you check the integrity of the downloaded image?
Yes, I checked:
```
dm@dm01:~/Downloads$ md5sum ubuntu-10.10-desktop-i386.iso 
59d15a16ce90c8ee97fa7c211b7673a8  ubuntu-10.10-desktop-i386.iso
```This matches the hash on this page: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
The unetbootin iso is downloaded by unetbootin, and I guess it verifies its own iso (?)

Did you tried the mentioned boot parameters on that other thread like acpi=off, nomodeset, xforcevesa etc?
No - I mentioned I wasn't sure how to go about it. Assistance, or pointers to directions would be aprreciated. There were no instructions in the thread I read/

Did you try with some other USB drive?     
I used 2 different usb drives - both ultimately failed, however, I used one with the ubuntu-created disk, and the other with the unetbootin-created disk.

Please let me know if there is any more info I can provide.

Thanks,

d

---

### Post by sikander3786 on 2010-11-17
Boot options for Live CD can be seen by pressing any key as soon as the Bios screen disappears. (Keep on pressing until you see the menu with Install and Try options).

Don't know where they should be for the USB drives.

I think for Unetbootin, you get a blue startup screen with some options with Default on the top of the list. There might be an option for Custom entry or Edit, or something similar. Select that and put acpi=off at the end and continue boot.

You might need to try all those options one be one until you succeed.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by cottfcfan on 2010-11-17
Hi Cheekybuddha,
I had exactly the same problem.
Edit the file etc/modprobe.d/blacklist.conf
at the end of the file add the line:
blacklist rt2500usb
Save & Reboot.
Problem should be gone.

ps this can only be done after installation.

---

### Post by cheekybuddha on 2010-11-17
OK, thanks for your responses.

So, I can't get to the grub loader without booting from the usb still - straight to blinking cursor at top left of screen.

Booting from usb, I got to grub loader and to the boot options. I removed "quiet splash" and replaced with "nomodeset acpi=off xforcevesa"

It booted in fine(ish!). I logged in to the desktop - all looked good but the screen was slightly stretched vertically.

Ubuntu invited me to add drivers for NVIDIA which I did.

I then added "blacklist rt2500usb" to etc/modprobe.d/blacklist.conf as per cottfcfan's suggestion.

Rebooted for driver update to take effect.

Reboot without stick - back to blinking cursor, unable to access grub menu

Reboot with stick, into grub options. This time I replaced "quiet splash" one at a time:
nomodeset: booted to weird screen - half white, half black
acpi=off: booted to shell login
xforcevesa: booted to weird half white, half black screen

Then, again with stick, booted with all three. This time again to shell login. I logged in and issued:
startx

Basically the NVIDIA drivers seem to have mucked things up.

Here's some of the last output:
```
NVIDIA: IRQ 10, assigend to device PCI:0000:02:00.0, is edge-triggered!
(EE) NVIDIA(0): The interrupt for NVIDIA graphics device PCI:2:0:0 appears to
(EE) NVIDIA(0):     be edge-triggered. Please see Chapter 8: Common Problems
(EE) NVIDIA(0):     in the README for additional information.
(EE) NVIDIA(0):  Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

 ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2):  unable to connect to X server
xinit: No such process (errno 3): Server error.
```Aaargh!

Any further ideas?

Thanks,

d

---

### Post by cottfcfan on 2010-11-17
Are you running all this from a Live USB stick, or have you installed?

---

### Post by cheekybuddha on 2010-11-17
Not entirely sure!!!

I thought I had installed - it was a net install.

However, I can only get back into the grub loader from the live stick. When booting from the hdd, I can only get to the blinking cursor no matter how much I hold down shift.

d

---

### Post by cottfcfan on 2010-11-17
Not sure what you've done.
It could be the Nvidia driver thats causing you the problem.
When booting from the usb stick and you get the grub prompt, type "help" and it should give you a list of options. One is just enter to carry on boot, see if you can get in that way and post back.

---

