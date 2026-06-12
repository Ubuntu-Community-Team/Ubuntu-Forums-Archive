---
title: "Need help with GParted"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by darshan123 on 2010-10-23
Hi,

I am trying to expand a partition using gparted. Please check the attached image (want to move sda7 to left to use sda5). So I guess, I need to first copy sda7 onto sda5 and then format sda7 and then expand sda5 to the right (am I right?).

But, the option, 'copy' is not getting highlighted for sda7 (when i right-click on it). Does the 'lock' icon mean that I can't copy ?
Is it because my current OS is running on sda7?

Now, how should I go about it?

Thanks,
Darshan

---

### Post by sikander3786 on 2010-10-23
You need to unmount the drive before making any changes.

It would be better to run gparted from a Live CD. I guess you are trying from inside your Ubuntu install?

Backup all the important data on those partitions (if any).

---

### Post by jgeralnik on 2010-10-23
Since it seems like you don't care about sda5, why don't you just delete sda5 and then you should be able to expand sda7 without a problem?

---

### Post by Rubi1200 on 2010-10-23
+1 to everything said by sikander3786.

---

### Post by coffeecat on 2010-10-23
> **darshan123 said:**
> I am trying to expand a partition using gparted. Please check the attached image (want to move sda7 to left to use sda5). So I guess, I need to first copy sda7 onto sda5 and then format sda7 and then expand sda5 to the right (am I right?).

sda7 is your root partition. You cannot work on it from the system it is on. As sikander3786 said, you need to use the live CD.

Also, be careful with UUIDs. They are needed for your /etc/fstab and grub to work properly and you may end up with a non-booting system if your root partition UUID changes. You don't say how you intend to copy sda7 to sda5, but much safer as far as UUIDs are concerned would be to delete sda5 and simply enlarge sda7 'backwards' into the freed space.

---

### Post by darshan123 on 2010-10-23
@sikander:
i had tried that. It says some error.
[COLOR=Blue]"Unmount Error
Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually"[/COLOR]
Yes. I am trying from inside ubuntu. 
What option I have if i dont have a liveCD right now?

@jgeralnik:
yes. I have already formatted in ext4 and there's nothing in there. But i guess i just can't expand sda7.

---

### Post by sikander3786 on 2010-10-23
No other options except Live CD or a Live USB or a Live Gparted CD.

sda7 is your root partition so it cannot be unmounted obviously.

---

### Post by darshan123 on 2010-10-23
but even if i delete sda5 and then try to resize/move sda7, it is not considering/showing the deleted space at the left.

---

### Post by jgeralnik on 2010-10-23
As stated above, there is really no option other than downloading and burning a live cd. sda7 is where your root partition is and so as long as you are running ubuntu from it you will not be able to change it. If you happen to have an ubuntu live cd lying around that would work too; just install gparted and from there you should be able to resize the partition with no problem.

---

### Post by bumanie on 2010-10-23
The gparted help manual should explain everything you need to do and how to do it. Go [here]("http://gparted.sourceforge.net/documentation.php").

---

### Post by darshan123 on 2010-10-23
Ok. Will try with a LiveUSB.
Thanks for all the quick replies.

Darshan

---

