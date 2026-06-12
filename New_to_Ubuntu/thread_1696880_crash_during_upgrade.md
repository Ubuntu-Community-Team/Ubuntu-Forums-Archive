---
title: "crash during upgrade"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Velenjak on 2011-02-28
ubuntu 9.10 upgrading to 10.04

ive been having odd computer problems, i thought upgrading my OS version would be a good idea, i was wrong.     most of my information is already backed up - i was basically experimenting with my spare computer.


operating system wont start, gives the error of cannot mount dev: no such device

and it also says unable to access pci1000 usb 5/5.2


i used the installation usb and checked file integrity, it said everything was fine - then i tried memtest and every single test showed as an error - i actually laughed, it was pretty funny to see. my question is, is this an error relating to the broke OS? or is it referring to the actual hardware of my computer. 


the computer never had any problems until my power source broke 3 months ago and more recently my cd drive broke 2 weeks ago. ive had it for awhile now - it has 'alot of miles' on it. i wont mind replacing more parts...

thanks in advance

---

### Post by sikander3786 on 2011-02-28
What do you mean by odd computer problems?

If memtest is reporting errors, your RAM is actually defected.

---

### Post by Velenjak on 2011-02-28
> **sikander3786 said:**
> What do you mean by odd computer problems?

If memtest is reporting errors, your RAM is actually defected.

whenever i would transfer lots of files, like a torrent or moving files to a usb, the computer would lock up and crash.

it was a bad idea to decide to try an upgrade... 

how would all my ram become defected? can you elaborate on that im not the best with computers...

---

### Post by sikander3786 on 2011-02-28
There is no apparent reason behind RAM or any other Electronic item getting defected. It happens. And might happen due to power fluctuations, power failures etc.

If you can get your hands on some other RAM modules, I would recommend to put them in your PC and run a memtest again. You can also run a memtest on your current modules by placing them in another PC.

---

### Post by Velenjak on 2011-02-28
> **sikander3786 said:**
> There is no apparent reason behind RAM or any other Electronic item getting defected. It happens. And might happen due to power fluctuations, power failures etc.

If you can get your hands on some other RAM modules, I would recommend to put them in your PC and run a memtest again. You can also run a memtest on your current modules by placing them in another PC.

thanks for advice. ive got some extra ram somewhere...

is the ram the reason for the failure to mount dev as well?

---

### Post by sikander3786 on 2011-02-28
Perhaps faulty RAM is the cause all those errors on your PC.

Let us know about your experience with the new modules please.

---

### Post by Velenjak on 2011-02-28
> **sikander3786 said:**
> Perhaps faulty RAM is the cause all those errors on your PC.

Let us know about your experience with the new modules please.

mem test no longer loops with constant errors, ill experiment more with that - maybe some of the sticks will work...


still cannot not boot into OS though, still receiving original unable to mount dev error...

---

### Post by sikander3786 on 2011-02-28
You might need to re-install the OS as the upgrade was proceessed on faulty RAM.

---

### Post by Velenjak on 2011-02-28
> **sikander3786 said:**
> You might need to re-install the OS as the upgrade was proceessed on faulty RAM.


i have some files that i need but havent backed up yet... ill look into finding a way to do that - thanks for your help!!

---

### Post by Velenjak on 2011-02-28
found the culprit to be a 1gb samsung stick

makes sense why my computer would operate doing mundane things - and lock up when i made it move lots of files

---

### Post by sikander3786 on 2011-02-28
You can recover your files simply by booting an Ubuntu Live CD/USB and mounting your intended partitions. Then, you can copy over your data to a safe location.

Happy Ubuntu-ing!

---

### Post by Velenjak on 2011-02-28
> **sikander3786 said:**
> You can recover your files simply by booting an Ubuntu Live CD/USB and mounting your intended partitions. Then, you can copy over your data to a safe location.

Happy Ubuntu-ing!

how would i mount my main partition and transfer the data? i dont know the command prompt very well...

---

### Post by sikander3786 on 2011-02-28
You dont need to use the command prompt. Boot an Ubuntu CD and under Places, simply click your drive. It should mount automatically. Same for the other one to which you will be saving the data.

---

### Post by Velenjak on 2011-02-28
> **sikander3786 said:**
> You dont need to use the command prompt. Boot an Ubuntu CD and under Places, simply click your drive. It should mount automatically. Same for the other one to which you will be saving the data.


ok cool ive backed up the important files - do you know where the tomboy note files are stored on the home folder? ive been using the search function but i cant find it...

---

### Post by sikander3786 on 2011-03-01
/home > .local > share > tomboy.

Press Ctrl + H in home directory to see hidden files.

---

### Post by Velenjak on 2011-03-01
> **sikander3786 said:**
> /home > .local > share > tomboy.

Press Ctrl + H in home directory to see hidden files.

it says i dont have permission to access .local ?

what do i do from here? 

thanks again for the help

---

### Post by sikander3786 on 2011-03-01
Permission shouldn't be an issue here. From Terminal, run this command.

```
gksudo nautilus
```

Navigate to /home and try again.

---

### Post by Velenjak on 2011-03-01
thank you very much!! all finished here....

---

### Post by sikander3786 on 2011-03-01
> **Velenjak said:**
> thank you very much!! all finished here....
You are Welcome :-)

---

