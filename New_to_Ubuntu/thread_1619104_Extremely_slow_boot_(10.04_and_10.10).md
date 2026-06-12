---
title: "Extremely slow boot (10.04 and 10.10)"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by momrocker on 2010-11-11
Hey guys, I have recently installed Ubuntu 10.04 on my computer using Wubi and I have had extremely slow boot times, like just now when I rebooted it took a total of **18 minutes** from the time I hit the button till I got to the login screen. I have no idea what could be causing this, so I will A) post exactly what happened this time it booted and B) post a compressed archive that has 3 of the outputs from dmesg that I have saved when my computer was running slowly.

[Here]("http://www.amazon.com/Toshiba-NB205-N210-NB200-10-1-Inch-Netbook/dp/B002BDUAEK") is a page with my computer specs. I have updated and upgraded all the software in my installation of 10.04 to no avail.

So heres about how it went. I installed wubi and installed 10.04 with wubi no problem. fast install, and when i restarted my computer the first time to install ubuntu and the second to open ubuntu after install I didnt have this problem, leading me to believe it might have been the kernel update. Anyways, now, every time I boot it happens alittle like this:

10:02 oclock - hit the button on my laptop

10:03 - selected ubuntu in the grub menu and selected the version I want to boot. Hit with black screen with flashing white dot, like its asking me for input, but nothing I type in does anything.

10:13 - flashing dot disappears and even darker black screen ensues. If I hit enter the dot comes back, but the dot always seems to disappear at this point anyways.

10:19 - ubuntu screen pops up with orange and white dots

10:20 - login screen

So, as you can see this can get a little.. irritating. lol.

Please also check the 3 files I have attached and compressed.

Thanks in advance guys!

EDIT: It might have something to do with my SATA drive? Some [other people]("http://www.google.com/url?sa=t&source=web&cd=3&sqi=2&ved=0CCkQFjAC&url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Flinux%2F%2Bbug%2F595448&ei=9zPcTIXmHJD4sAPwv7GPCA&usg=AFQjCNFAnQcrvdytpW2sgWTHM4B_pMCf5w") have been reporting bugs with SATA drive support causing slow boot times.

---

### Post by bioterror on 2010-11-11
Found something:

> The boot time is with the default settings horrendously slow. A simple change in the BIOS will speed up the boot time to less than 30 seconds.

Press F2 on machine boot to enter the BIOS
Select the 'Advanced' tab
Change SATA controller mode from AHCI to Compatibility

Read more about this from [here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205")

---

### Post by momrocker on 2010-11-11
Ok, I'll try that out. Will report back soon.

---

### Post by momrocker on 2010-11-11
OMG It worked! Ty ty ty ty! Now I can actually use Ubuntu again!!!!

:guitar::guitar:

---

### Post by bioterror on 2010-11-11
You're welcome ;)
[IMG]http://ricecows.org/stuff/mosh.gif[/IMG]

---

### Post by sarum on 2010-11-12
I'm hoping that there may be some one still following this thread because I have tried the above. Problem is, F2 or del at start up takes me to BIOS; then  'Advanced' but I can't find AHCI to change to 'compatability' There are 6 or 7 headings, and I've expanded each one. I must be missing something. New thread if no replies..............sarum

---

