---
title: "accidentally tried to format my ubuntu drives while in XP"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by kellym on 2011-03-09
I still can't believe I did this...
XPP/Ubuntu 10.10 Dell Dimension 4600 2GB RAM
Had the drive partitioned into XP(ntfs) , ubuntu/xp share(ntfs), ubuntu, and free space. 
Was working perfectly until I decided to format my ubuntu/xp share drive and my ubuntu partition instead of the free space while I was in XPP. 
I rebooted (should not have) and get:
error: no such partition 
grub rescue>

I don't have an XP Pro disc here only XP Home and I think I have a Ubuntu 10.10 LiveCD somewhere.
What do I need to do to fix this mess.  First priority is getting back into XPP then get data back from Ubuntu then fix Ubuntu install.

---

### Post by cap10Ibraim on 2011-03-09
*[SIZE="3"][COLOR="Red"]Did you format the Ubuntu partition ?! [/COLOR][/SIZE]*
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by kellym on 2011-03-09
Yes I think I formatted the ubuntu share and ubuntu partitions. 
I dont think the administrator password was set or I dont remember what it is.

---

### Post by Rubi1200 on 2011-03-09
If none was set you can just hit Enter to continue.

If you cannot remember it that is a different issue.

There would be another way to get Windows booting, but first try fixboot followed by fixmbr, then exit and reboot.

---

### Post by DogMatix on 2011-03-09
> **kellym said:**
> First priority is getting back into XPP then get data back from Ubuntu then fix Ubuntu install.

Have you got a back up of the ubuntu install? If you have formatted the Ubuntu install partition. I think that is your only hope of retrieving it.

---

