---
title: "Merging two partions seperated by an extended partition"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by sajaskk43 on 2011-05-13
Hi,
I am new to ubuntu. I was trying to install ubuntu ultimate edition 2.9 to my computer. I have 4 partitions. One for the bootloader. Then a 29Gb which i used for windows 7 and a 7.4 Gb freespace and an extended partition. I want to merge the windows 7 partition to the 7.4 Gb free space. I have formatted every partition except the extended partition and tried to merge them but couldn't do it. Please help. I have seen a lot of discussion on partition in this forum but i couldn't make them to work..Please help........:sad:

---

### Post by jerrrys on 2011-05-13
need to go to the "paperclip" to post a pic

[ATTACH]191995[/ATTACH]

---

### Post by sajaskk43 on 2011-05-13
Thank you...Could you please help me with the partitioning problem.........

---

### Post by jerrrys on 2011-05-13
yes, just wanted to see the big picture first :D

---

### Post by sajaskk43 on 2011-05-13
> **jerrrys said:**
> yes, just wanted to see the big picture first :D

Ok ..What should i do now??????? [-o<

---

### Post by jerrrys on 2011-05-13
nice big pic :D  ok i see what your up to and i have not tried that before.  i got a test box, let me see if i can do it. ill post back

---

### Post by mcduck on 2011-05-13
You can only merge partitions that are next to each other, and unmounted at the time. And you can't merge a primary partition with a logical one.

If it's the free space at the end of the drive and you want to merge it with sda2, you'll have to first grow the extended partition to contain that space, then move all partitions inside the extended one to the end of the extended partition, and shrink it again from the other end to leave the free space between it and the sda2. After that you can grow the sda2 to use that space.

---

### Post by sajaskk43 on 2011-05-13
So, I  won't be able to merge my sda2 (26.87 Gb) and sda4 (6.67 Gb)...Thanks for the quick reply....

---

### Post by sajaskk43 on 2011-05-13
It seems like I don't have any way to get around this problem..Thanks jerry for your support..

---

### Post by mcduck on 2011-05-13
> **sajaskk43 said:**
> So, I  won't be able to merge my sda2 (26.87 Gb) and sda4 (6.67 Gb)...Thanks for the quick reply....

Not directly. What you *can* do is delete the sda4, shrink the extended partition accordingly to leave the free space in front of it, and then grow sda2 to use it.

---

### Post by sajaskk43 on 2011-05-13
> **mcduck said:**
> Not directly. What you *can* do is delete the sda4, shrink the extended partition accordingly to leave the free space in front of it, and then grow sda2 to use it.

Will that affect the data in the extended partition. If it won't, could you please tell me how to do it explicitly. I don't want to lose the data.

---

### Post by mcduck on 2011-05-13
> **sajaskk43 said:**
> Will that affect the data in the extended partition. If it won't, could you please tell me how to do it explicitly. I don't want to lose the data.

It shouldn't, but when editing partitions there's of course always the risk of something going wrong. Make a backup before making any partition changes, one should always have a backup anyway.

...and sorry, but you'll have to wait for somebody else with the exact instructions, I don't have an Ubuntu system at hand now so giving detailed instructions for gparted would be pretty hard. :/

---

### Post by jerrrys on 2011-05-13
i just did it

had to recreate your conditions by adding a 100MB free space in front of everything then turn off swap and resize the extended partition down 100MB.

end result i now have an extra 100MB in my primary partition

---

### Post by sajaskk43 on 2011-05-13
> **jerrrys said:**
> i just did it

had to recreate your conditions by adding a 100MB free space in front of everything then turn off swap and resize the extended partition down 100MB.

end result i now have an extra 100MB in my primary partition

What should i do ???? Is there any risk of loosing my data in extended partition??

---

### Post by jerrrys on 2011-05-13
when working with partitions there is always a risk...

---

### Post by sajaskk43 on 2011-05-13
I think I will have to take that risk....... go on.....

---

### Post by jerrrys on 2011-05-13
you have to unmount your hdd.  i have done resizing in the past while mounted, but it won't work here. so if you have to, use your live cd.

---

### Post by jerrrys on 2011-05-13
> **jerrrys said:**
> i just did it

had to recreate your conditions by adding a 100MB free space in front of everything then turn off swap and resize the extended partition down 100MB.

end result i now have an extra 100MB in my primary partition

i said in front of everything.  what i should of said is your free space has to be at the beginning of the extended partition.  its a slow process, good luck

---

