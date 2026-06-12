---
title: "Restart Problem on Dell B110 after hibernation"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by deaner51 on 2009-09-16
My Dell B110 will not restart from the HD after going to hibernation mode. This has happened twice. It seems that the only way to start up again from the HD is to do a complete reinstallation of 9.04.  The BIOS appears to load up normally--and I can, for example, change the start up disk--but after the BIOS runs the screen just goes blank.  I have run Ubuntu for several weeks now with no problems except for the two times I tried to shut down to hibernation mode--then it wouldn't restart.  Any solutions (other than the obvious one of not hibernating again)?

---

### Post by QIII on 2009-09-16
How much memory do you have and what is the size of your swap?

When you hibernate, your memory state is saved to swap (hibernation is sometimes called "suspend-to-disk").

If you have, for instance, 4GB of RAM but only 2GB of swap, the entire contents of the RAM cannot be saved, and you will get garbage back to your RAM from the swap when you try to come out of hibernation.

The "other" OS (hack, cough) allots space dynamically.  I have to give them that one.

---

### Post by deaner51 on 2009-09-17
I have 2 GB of RAM.  You are on to something...I have 0 memory allocated to swap.  Would you recommend that i set it to about 1 GB of swap memory?  Thanks for your response!

---

### Post by Cheezespread on 2009-09-17
If you have enough disc space , allot 1.5-2 times your RAM memory size to the swap size. Around 3GB-4GB.

Hope this [link]("https://help.ubuntu.com/community/SwapFaq") helps !! . Especially the part of creating a swap file rather than going to reintsall it from scratch.

---

### Post by deaner51 on 2009-10-03
I still have the restart problem after hibernation.  I added the swap memory and my computer still is dead in the water after hibernation.  I also double-checked the swaptotal and apparently have--with the default installation of Ubuntu 9.04--3,229,025 KB of swap memory available. I have an 80 Gb hard drive and 2 Gb of RAM.  

I have reinstalled Unbuntu on my desktop.  I appreciate your feedback and am looking for additional suggestions!

---

