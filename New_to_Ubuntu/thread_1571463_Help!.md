---
title: "Help!"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by realhope on 2010-09-09
I have a hp dv7-3165dx. it has 4 partioins already i need one how can i back up my recovery hdd on another is this even possable .please help and thanks if you do.

---

### Post by Immolatus on 2010-09-09
assuming you are running win7, you have the option to make recovery media from within windows. It requires three dvdr disks. I think everyone should do this anyhow because if the hdd ever went you could still reinstall from the recovery media.

Doing this will allow you to do away with all the spare partitions and dual boot if you like. I just did this on a new thinkpad.

---

### Post by realhope on 2010-09-09
thanks, my problem is im outta a discs right now i have a spare hdd is there way to put it on one?

---

### Post by Immolatus on 2010-09-09
I suppose, but only if the laptop bios supports booting from usb. I also wouldn't have anything else bootable on that external. I have read of some people doing this with a usb flash drive although it must be prepared to be bootable. The only way to know it was done right is to use dvdrs. First disk is the boot medium, second is app data and the third is drivers. what this does is return the machine to the factory state.

Personally I would wait and scrounge up three dvdrs.

One more note: If you try this and put it on a non-bootable medium and don't know it doesn't work you're stuck. win7 will only let you do this once. However if recovery partition is still intact you can reinstall from that and burn again because it thinks you never did it.

---

### Post by realhope on 2010-09-09
WOW! ok thanks ummmmm now i dont even know if i wanna do it (install UB 10.04) thses are my partioins ,hp tools, recovery, system, and win 7 is recovery the best candidate if i were to?

---

### Post by Immolatus on 2010-09-09
I personally would reinstall from the recovery media using "advanced" partition editing. Delete the recovery partition and HP tool as they are probably useless anyhow. Install win7 to take up about half of the drive and install Ubuntu on the remaining space.

Have you ever done a dual boot install??

---

### Post by realhope on 2010-09-09
Yes i have done it before i have two notoriously impossible dell 1525, that have the dual boot installed on )(everything works). 

Can you tell me how to do a partition edit or a link to one , i did it before and it was only one disc, and seeing how the recovery is 17gb i assumed that it was wrong.lol.

side note im hesitant to delete the hp tool , on the count of i deleted a mere 2.5 gb partition an my dell.........had to reinstall quite literally everything.

---

### Post by Immolatus on 2010-09-09
the aforementioned "everything" is all of the app data and drivers that will be located on dvds two and three. the only thing the recovery media will not reinstall is the recovery partition.

---

### Post by sxmaxchine on 2010-09-09
i have a dv-6 and i had to remove a partition before installing ubuntu. Dont remembe what i removed but [here is a screenshot of what i have at the moment.]("http://sxmaxchine.deviantart.com/art/my-partitions-178675790")

i removed the hp tools partition 9after i backed it up)

---

### Post by realhope on 2010-09-09
well thats great seeing how the hp didn't come with any drivers!
what will the first disc be?





SX how ever did you achieves such perfection!?!?!?!?

---

### Post by sxmaxchine on 2010-09-09
> **realhope said:**
> well thats great seeing how the hp didn't come with any drivers!
what will the first disc be?





SX how ever did you achieves such perfection!?!?!?!?

hahah thanks

here is how i did the partitioning.

1. start windows and make your windows recovery disks (just in case something goes wrong)
2. backup HP tools partition then delete the partition.
3. resize the windows partion to desired amount.
4. open the ubuntu installer. from there im pretty sure you can tell it to install using the available space if not then let me know and i will have to click advanced and create 2 partitions one is an ext4 partition and add a / as themount point and create a swap partition. If you need more help with this then feel free to ask and i will try and explain this better.

---

