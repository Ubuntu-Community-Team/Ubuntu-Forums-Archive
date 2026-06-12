---
title: "Keyboard Mapping"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by JeffG01 on 2009-05-15
Hi, I'm new to Kubuntu and have just installed version 9.04. As soon as the installation finished the update manager alerted me to a number of updates which I promptly installed. Everything appears to work OK except for the keyboard mapping.
 
I've chosen generic keyboard and US English. It's a 104 key keyboard and while the graphic looks identical to my keyboard some keys do not respond at all and the number 2 key when shifted (uppercase) produces a " instead of the @. I've tried a couple of variations in setting up the keyboard preference (differennt keyboard names, English language, etc.) and can't seem to get this to work right.
 
I initialling burned an ISO CD and tried to install from it but the install failed at the very last stages yielding an "Invalid Argument" error message that I couldn't make sense of. I was using the WUBI installer and installing within Windows XP environment.
 
I then ultimately ran WUBI installer and downloaded the ISO directly to md HD, and this install has succeeded with the exeption of the keyboard mapping issue as described above.
 
Any assistance would be appreciated.
 
Thanks,
JG

---

### Post by radiocognition on 2009-05-16
From the Kickoff menu in KDE 4 open your System Settings program ( you can usually find it under the computer tab ).  Select Regional & Language.  Here you can select a different regional keyboard layout.

If this answers your question and resolves your issue, please mark this thread as SOLVED so that other users can know it worked for you.

---

### Post by JeffG01 on 2009-05-16
Turned on my computer and chose the boot into Unbuntu option so that I could try your suggestion.   This is a copy of the screen message that I received.
 
[FONT=Times New Roman][SIZE=3]Booting ‘Unbuntu 9.04, kernel 2.6.28-11-generic’[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Filesystem type is ntfs, partition type 0x07[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The current working directory(i.e., the relative path) is /unbuntu/disks[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][Linux-bzImage, setup=0x3000, size=0x353cd0][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][Linux-initrd @ 0x2e87d000, 0x76e41e bytes][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][   0.909016] ACPI: Aborted because bad gzip magic numbers.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][  2.706539]  IO APIC resources could be not be allocated.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][  3.814830]  Kernel panic – not syncing:  VFS: Unable to mount root fs on unknown-block(0,0)[/SIZE][/FONT]
 
 
My computer is now frozen.  Any suggestions?  Should I be posting this in the installation forum now? Thanks, JG

---

### Post by radiocognition on 2009-05-16
I have never worked with wubi, it looks like you had some sort of issue in you installation.  Apparently the kernel can't find the filesystem you used to set up your root directory.  Can you still boot into windows or are you forced to use the live cd?

It looks like you have a whole different ( and much more serious ) problem than what was stated in the thread.  I would start a new thread entirely - you can try posting it in "Installations" , but you might get better help faster if you post it in "Absolute Beginner Talk"

---

