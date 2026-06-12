---
title: "Question on IDE devices"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by anewguy on 2010-04-20
I seem to remember from way back when (it's been a LONG time) that I was taught that an IDE channel is only as fast as its slowest device.  With that in mind, I have a small question I hope someone can answer.  Since I think it's just an IDE question, but for all I know anymore maybe it did have something to do with the OS, I'll ask here and if the thread needs to be moved that fine.

I have a second IDE drive I've been trying to set up.  Since the larger drive bays up where my DVD/RW are require rails, and of course rails for this case seem to be impossible to find, I have needed to mount the new drive right above my main drive and connect it to the same cable.  The problem is that my main drive is ATA 133, and the second drive is ATA 100, and I really don't want to run my main drive at 3/4 speed transfer rate, but the IDE ribbon cable for the second IDE channel, that my DVD/RW is on, doesn't have enough space between the drive connectors to allow it to reach both my DVD/RW drive and my second hard drive.

So the question is does anyone make IDE cables that either have two completely seperate leads to the drives or at least have more space between the two connectors?  I'm guessing, without taking the cover of the case again right now, that it would need about a foot or so of space between the two drive connectors.

I've been away for going in to computer parts stores for quite a while because with my spending habits every trip for something small was getting very expensive with the Steve Martin/The Jerk movie line "and I need this....". :)

Thanks in advance from an old guy!

Dave ;)

---

### Post by shazbut on 2010-04-20
I wouldn't worry too much about running both through the same cable.  Even with both drives working at the same, they're unlikely to saturate the ATA bus.

Having said that, custom IDE cables are possible.  Where I used to work we had a special press for making them.  Just remember that the max rated length is 45cm (18in) for the entire cable, and an out-of-spec cable with errors is likely to be worse than mixed ATA100/133 drives in master/slave config.

---

### Post by Drenriza on 2010-04-20
IDE can be both IDE-PATA or IDE-SATA. In this situation i believe your having pata drives. To keep performance loss to a minimum, connect your fastest drive to the first avaliable connector on your cable. And your slower drive on the second avaliable connector.
 
This first avaliable connector on ur cable, is also the closest to the MB. After it is connected to the MB.
 
You can either get cables with 40 wires or 80 wires. The one with 80 wires is the one with the most performance possibilityes. With speeds from 16mb/s to 33, 66, 100 and 133

---

### Post by anewguy on 2010-04-20
Yep, got the 80-pin cable already (kinda required at ATA-100 and up).  I wasn't aware there was a IDE-SATA drive - I thought IDE was actually the old standard parallel ata, and sata is for serial at attachment.  Maybe I didn't know that SATA is actually IDE-SATA (considering the actual meaning of IDE from way back when, I suppose that's quite possible - I just haven't kept up with the technology since I haven't been working since 1996).  As for length, I *thought* (again, this is from a long time ago) that reason for the limitation on the cable length was 2-fold - cross talk and signal strength.  I assumed the with the 80-pin cables (hence a ground on each signal/address/data line) would increase the length, but I guess signal strength must still be a limiting factor.

Also, have the "fast" drive first on the cable.

But....the only thing is there is a very noticable difference in performance when both drives are on the same IDE channel.

I did see a cable on the Micro Center web site just now that is supposedly parallel ata and has 2 seperate cables (1 for each drive) coming off the channel connector at the motherboard.  I may try picking one of those up and connecting the second drive and the optical drive on that channel.

Thanks for the input!

Dave ;)

---

