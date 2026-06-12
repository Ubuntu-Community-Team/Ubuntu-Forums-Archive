---
title: "Connecting my other Partition."
date: 2010-04-23
forum: New to Ubuntu
---

### Post by DarkDavil on 2010-04-23
Is it possible to open files that are on my Windows, C:, partition? Because the main reason I got Ubuntu this time was just so i could watch movies on a less CPU/Graphics using OS.
I have Ubuntu ver 9.10 x64. My windows is Winows 7 Ultimate x64.

My system(laptop)
CPU: Core 2 Duo @ 2.4 Ghz
RAM: 4 GB DDR2
Graphics: Nvidia Geforce 8400M GS

I would open my HD movie files(Blu-Ray rips usually) and watch them in VLC media player and add downloaded subtitles. I would then hook my laptop to my tv using an HDMI cable(already tested this on ubuntu, it works fine, and my stero cable to 2 channel sound splitteer cable works fine too.)

-Thanks Everyone

-DD
PS. Please include all steps, as i haven't used Ubuntu in ageees :D!

---

### Post by 2hot6ft2 on 2010-04-23
System > Administration > NTFS Configuration Tool
set that up then go to
Places > (Your windows partition)
and browse to them.
If you have any trouble there are only 3 programs to work with NTFS partitions that you might need ntfs-config is NTFS Configuration Tool
so if you don't have it just try installing them all like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ntfs-3g ntfsprogs ntfs-config
```
You will have to enter your password which wont be displayed just type it in and hit Enter
If it says one is already installed just remove it from the command and re run it.
Then try again in
Places > (Your windows partition)

---

### Post by DarkDavil on 2010-04-23
Okay - got all those things installed, but when i open up the NTFS Configuration Tool - it only gives me the option to:
"Enable Write Support for Internal Device"
 or
"Enable Write Support for External Device"

So i have the Enable the Internal Device check off - but when i try to go to my "Places", it doesn't show anything to do with my C: drive.

---

### Post by adam814 on 2010-04-23
Ubuntu won't recognize it as your Windows C: drive automatically.  You'll either see the partition label (might even just be a mixture of numbers and letters since Windows came pre-installed on it) or "200 GB Filesystem" for example.

Your C: drive should show up as something like that under the Places menu.

---

### Post by marshmallow1304 on 2010-04-23
> **DarkDavil said:**
> So i have the Enable the Internal Device check off - but when i try to go to my "Places", it doesn't show anything to do with my C: drive.

Does it show "XX GB Filesystem" where XX is the size of your Windows partition?

Edit: It could be labeled differently, like "OS" or "Windows".

---

### Post by DarkDavil on 2010-04-23
> **marshmallow1304 said:**
> Does it show "XX GB Filesystem" where XX is the size of your Windows partition?

Edit: It could be labeled differently, like "OS" or "Windows".
Nope - nothing new is shown. :(
Though i do have a system reserved, which doesn't contain anything but some odd files.

---

