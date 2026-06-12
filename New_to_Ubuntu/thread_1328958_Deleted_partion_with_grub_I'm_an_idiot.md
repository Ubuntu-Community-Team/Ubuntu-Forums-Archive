---
title: "Deleted partion with grub *I'm an idiot*"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by pearldrums on 2009-11-16
Ok, So I was testing out the netbook remix and made a small partition for it. I then had 2 different partitions with ubuntu installed. I decided I didn't like it. So I had the braniac idea to delete the UNR partition. BAD IDEA. Grub wants to load off of the no longer existant partition. Now when I boot it brings me to a grub rescue menu. It looks like it should be easy enough to change where it looks for its config files though... I hope... Other wise if I know how big my partition was can I re-create it with a live CD gparted?

---

### Post by Miljet on 2009-11-16
You are going to have to reinstall GRUB. Not a major problem, but before anyone can help, they will have to know what Ubuntu version you have. 9.10 uses GRUB2 and reinstall procedures are different.

---

### Post by pearldrums on 2009-11-16
oh yes I suppose I should have mentioned that, I'm running 9.10 with grub2.

Do I really need to re-install grub though? Shouldn't I have the data in my other ubuntu distro?

---

### Post by Sealbhach on 2009-11-16
> **pearldrums said:**
> Ok, So I was testing out the netbook remix and made a small partition for it. I then had 2 different partitions with ubuntu installed. I decided I didn't like it. So I had the braniac idea to delete the UNR partition. BAD IDEA. Grub wants to load off of the no longer existant partition. Now when I boot it brings me to a grub rescue menu. It looks like it should be easy enough to change where it looks for its config files though... I hope... Other wise if I know how big my partition was can I re-create it with a live CD gparted?

Which version of Ubuntu are you using? You will need to re-install grub with a Live CD.  If you're using a Live CD, the procedure can be found here (item number 13): [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It's not too difficult to do.

.

---

### Post by pearldrums on 2009-11-16
> **Sealbhach said:**
> Which version of Ubuntu are you using? You will need to re-install grub with a Live CD.  If you're using a Live CD, the procedure can be found here (item number 13): [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It's not too difficult to do.

.


Thanks for pointing me in the right direction, but item 13 is under construction FYI... I'll get a live CD ready in the mean time though (seen as I have to do it usb this will take a few min)

---

### Post by Sealbhach on 2009-11-16
> **pearldrums said:**
> Thanks for pointing me in the right direction, but item 13 is under construction FYI... I'll get a live CD ready in the mean time though (seen as I have to do it usb this will take a few min)

Sorry, it''s item 12, the headings were incorrect there.

Also, if you look, item 14 gives instructions on what to do from the rescue mode....

.

---

### Post by pearldrums on 2009-11-16
thanks for the info, as I'm trying to make this work can anyone tell me if I might run into any oddities because I'm using an extended partition for my linux partitions?

---

### Post by pearldrums on 2009-11-17
EDIT: I must have made a mistake, this is now working for me.


alright, i tried using the rescue option and have troubles doing "ls /boot" so I'm not sure why. But I decided to try the live CD re-install... this is also proving to be a challenge. Before I start let me say that the correct partition is sda5 or hd0,5.

Step 1: mount device.... I can do this
Step 2: only for people with separate boot partitions. I would know if I had one... right? so I don't do that... right?
Step 3: "If you have any other *system* partitions such as "*/usr*" these should also be mounted in a similar manner." Um... is the next set of code (that I have listed under part 4)? because I don't know if I have done this correctly or not.
Step 4: "Mount devices:      Code: sudo mount --bind /dev/ /mnt/dev " 
-this is where things fall apart, so I'm assuming that I'm not mounting the /usr part correctly?
Step 5:Chroot into your normal system device:      Code:
     sudo chroot /mnt 
this doesn't work. on a side note, what the heck is "/mnt"
Step6:Reinstall GRUB 2:      Code:
     sudo grub-install /dev/sdX 
*sigh* nope

---

### Post by pearldrums on 2009-11-17
Thanks, got grub re-installed. life is good. I can now do my homework....

---

### Post by Sealbhach on 2009-11-17
> **pearldrums said:**
> 
Step6:Reinstall GRUB 2:      Code:
     sudo grub-install /dev/sdX 
*sigh* nope

Cool, I guess you figured out that the X in sdX should be a.

.

---

