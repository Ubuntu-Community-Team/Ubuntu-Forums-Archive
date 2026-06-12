---
title: "&quot;generic-pae&quot; kernel - what is it?"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-16
I was trying to download some programs into a v10.04 LTS installation yesterday, and ran into a problem. (Actually, I've forgotten the details, and I'm not on a Linux system right now so I can't check.) I was downloading extra ALSA accessories & libraries in the hopes I could get the sound to work through my M-Audio sound card. I'd selected to download a file (library? headers?) that I think was marked as a "dummy" file, for making OSS utils use "pae" wrappers. It was the 2nd such file I'd come across in the list (my search term in the Ubuntu Software Center had been "ALSA"), and this had the term "pae" in the title. I wasn't sure what it was, but I clicked to download it anyway. I figured the system would reject it if it was an improper fit. So, I clicked on it, and it starting installing.

There came a point where the screen went black. The hard drive indicator light was blinking; almost lit continuously. That lasted quite a while. Then, the drive activity ceased, and it just sat there. I also sat there, looking at that black screen for about 3 minutes. I was hoping it was just doing some calculations and would put the desktop back up - or, at least do *something*. But, it didnt. Eventually I got tired of waiting, and used Ctrl/Alt/Del to reboot.

That worked, but it didn't get to the login screen. It got stuck on the "Ubuntu" logo screen.

Before I quit, I also tried using a "recovery" mode. Then, normal booting. Nothing worked. Unless somebody comes up with some kind of brilliant suggestion, I'll had have to re-install the OS.

The reason I'm posting this, is that in the Grub list after my initial rebooting, there are now 2 new entries. A regular, and a recovery mode entry. They're for a kernel ending w/ "33-generic-pae". (NOTE: During the "recovery" attempt it ran dkpg, and I saw both the pae kernel items and stuff for kernels ending in "33.71" & "33.72". Anybody know what that pae thing is?

---

### Post by alphacrucis2 on 2011-08-16
> **scruffyeagle said:**
> I was trying to download some programs into a v10.04 LTS installation yesterday, and ran into a problem. (Actually, I've forgotten the details, and I'm not on a Linux system right now so I can't check.) I was downloading extra ALSA accessories & libraries in the hopes I could get the sound to work through my M-Audio sound card. I'd selected to download a file (library? headers?) that I think was marked as a "dummy" file, for making OSS utils use "pae" wrappers. It was the 2nd such file I'd come across in the list (my search term in the Ubuntu Software Center had been "ALSA"), and this had the term "pae" in the title. I wasn't sure what it was, but I clicked to download it anyway. I figured the system would reject it if it was an improper fit. So, I clicked on it, and it starting installing.

There came a point where the screen went black. The hard drive indicator light was blinking; almost lit continuously. That lasted quite a while. Then, the drive activity ceased, and it just sat there. I also sat there, looking at that black screen for about 3 minutes. I was hoping it was just doing some calculations and would put the desktop back up - or, at least do *something*. But, it didnt. Eventually I got tired of waiting, and used Ctrl/Alt/Del to reboot.

That worked, but it didn't get to the login screen. It got stuck on the "Ubuntu" logo screen.

Before I quit, I also tried using a "recovery" mode. Then, normal booting. Nothing worked. Unless somebody comes up with some kind of brilliant suggestion, I'll had have to re-install the OS.

The reason I'm posting this, is that in the Grub list after my initial rebooting, there are now 2 new entries. A regular, and a recovery mode entry. They're for a kernel ending w/ "33-generic-pae". (NOTE: During the "recovery" attempt it ran dkpg, and I saw both the pae kernel items and stuff for kernels ending in "33.71" & "33.72". Anybody know what that pae thing is?

[PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

---

### Post by scruffyeagle on 2011-08-16
> **alphacrucis2 said:**
> [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

Ah,... I see. Thank you! "Physical Address Extension", for surpassing the 4 GB limit on usable memory in a 32-bit system.

Given that the machine I was loading it into only has 500 MB, I can see that this wasn't really useful for my situation.

Now the remaining question in my mind, is whether or not I can recover that particular installation from this fiasco, or is the only available option re-installation?

---

### Post by seawolf167 on 2011-08-17
Can you boot at all into either the "normal" mode or recovery kernel? If you can't, are you able to enter tty1 after you select either entry by hitting [CTRL][ALT][F1]? Do you get a login prompt?

---

### Post by scruffyeagle on 2011-08-18
> **seawolf167 said:**
> Can you boot at all into either the "normal" mode or recovery kernel? If you can't, are you able to enter tty1 after you select either entry by hitting [CTRL][ALT][F1]? Do you get a login prompt?

I'll have to go toy with it again, to find out the answers. Then, I'll come back and post here.

There wasn't anything I couldn't afford to discard in that installation. I just held off wiping it out because I figured I might learn some useful stuff in the process of making it functional again (IF that's possible).

---

### Post by Paqman on 2011-08-18
> **scruffyeagle said:**
> 
Now the remaining question in my mind, is whether or not I can recover that particular installation from this fiasco, or is the only available option re-installation?

Depends what you've done. As far as the PAE kernel, just boot into one of the others and uninstall it. The system will update Grub and it'll be gone.

---

### Post by scruffyeagle on 2011-08-18
> **Paqman said:**
> Depends what you've done. As far as the PAE kernel, just boot into one of the others and uninstall it. The system will update Grub and it'll be gone.

I tried to do that by selecting recovery mode of the 33-generic option, but that didn't work. I didn't install the pae kernel on purpose, so I'm not sure how to name it in a command. Can you tell me what the correct command would be?

---

### Post by Paqman on 2011-08-18
> **scruffyeagle said:**
> I tried to do that by selecting recovery mode of the 33-generic option, but that didn't work. I didn't install the pae kernel on purpose, so I'm not sure how to name it in a command. Can you tell me what the correct command would be?

If you can't boot, you can't execute any commands. If none of your available kernels will boot then you're probably looking at a reinstall. You can salvage your data by booting up into a LiveCD and mounting your Ubuntu partition(s).

---

### Post by scruffyeagle on 2011-08-18
> **seawolf167 said:**
> Can you boot at all into either the "normal" mode or recovery kernel? If you can't, are you able to enter tty1 after you select either entry by hitting [CTRL][ALT][F1]? Do you get a login prompt?

This is going to be a lengthy reply... What follows is a terse description of my session toying w/ this installation, exploring its condition, and hoping I might accidentally fix it. (They say it's statistically guaranteed that given a thousand monkeys typing at a thousand typewriters for a thousand years, one of them would accidentally produce the complete works of William Shakespeare - so, why not me?)

My Grub list is as follows:
2.6.32-33-generic-pae
2.6.32-33-generic-pae (recovery mode)
2.6.32-33-generic
2.6.32-33-generic (recovery mode)
2.6.32-21-generic
2.6.32-21-generic (recovery mode)
(memtest 86+)
(memtest 86+, serial console 115200)
Microsoft Windows XP

*) I chose 2.6.32-33-generic (recovery mode).
*) I saw a long list in large print flash by
*) I saw a long list in tiny print flash by
*) I got the Recovery menu screen

*) I chose to repair the packages
*) In the midst of the output there was a long list of files that had been automatically installed, but were no longer required. There was also a command to use.

*) I got back to the recovery menu screen, and chose the netroot option.
*) I typed in the recommended command,
apt-get autoremove
*) In the midst of the long list that flashed by, I saw many items w/ "pae" & "21" in their names.
*) Exit took me back to the Recovery menu

*) I chose the "Resume normal boot" option.
*) It went to a tty1 login.

When I logged in (yes, it worked), there was a warning message displayed on the screen saying that the BIOS was lacking security protections that the CPU was capable of. I used the command it provided,
/usr/bin/check-bios-nx --verbose

I learned the CPU is family 15, model 3, w/ NX capabilities. But, the system can't use them because the BIOS is configured to disable them. It told me to please enable them, and that I could get further details at
[https://wiki.ubuntu.com/Security/CPUfeatures](https://wiki.ubuntu.com/Security/CPUfeatures)

*) I tried to use
sudo shutdown -r now
but it wouldn't work. I couldn't log in as root.

*) Ctrl/Alt/Del worked, rebooting the computer.

*) The Grub list was unchanged.
*) I chose the 33 normal option
*) There was a black screen, then the Ubuntu logo screen. Then, it hung there, not proceeding.

*) Left arrow shifted to a text screen. The last log entry displayed was the line about checking the battery. I don't know if it's significant, but the asterisk preceding "Speech dispatcher configured for user sessions" was red instead of white like the other asterisks.

There was also a message that said "Skipping profile in /etc/apparmor.d/disable: usr/bin/firefox.

*) I tried Ctrl/Alt/F1, as a way of seeing something other than this set of messages or the Ubuntu logo screen. It worked.
*) I logged in.
sudo shutdown now
returned me to the Recovery menu.

*) Tabbing to "Cancel" & hitting Enter took me to login command prompt line.
*) Logged in & tried to shut down.
*) That took me back to the Recovery menu.

*) Ctrl/Alt/Del rebooted the system.

---

