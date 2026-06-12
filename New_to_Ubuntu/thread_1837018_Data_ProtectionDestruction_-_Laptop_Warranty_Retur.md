---
title: "Data Protection/Destruction - Laptop Warranty Return"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Chrissd on 2011-09-01
Hi all,

I've got a fault with my laptop, so it's being sent off to be repaired. Being of the paranoid nature, and with my email password saved, bank details saved, phone numbers, addresses etc (you get the idea), I thought it'd be a good idea to delete this information off my system.

Initially, I just booted from a live CD, used gparted to delete the partition table. Job done, I thought. A little light reading later, and it appears, no, job is not done at all.

I then ran ```
shred -vfz /dev/sda
``` I believe that will destroy any data left on the hard drive? Is that right? Would dd be a better tool for the job? I understand it's slower, so unsure if it's more thorough.

My home directory, where all the data was saved, was encrypted anyway, so did I really need to shred it as well? 

I'm getting confused between what's easily recoverable by your average Joe, or computer repair company in this case, and what "*the man*" can achieve by extreme professional means.

---

### Post by egalvan on 2011-09-01
dban, from dban.org will erase a drive thoroughly..
enough so that it can be used on government contracts.

---

### Post by 3rdalbum on 2011-09-01
> **Chrissd said:**
> 
My home directory, where all the data was saved, was encrypted anyway, so did I really need to shred it as well?

No; without your passphrase, nobody can decrypt your data. Not even Them. Shredding won't help by any appreciable amount, but it WILL take a lot of time.

If you're really paranoid and want to overwrite the encrypted data, just overwrite it with zeroes:

```
sudo dd if=/dev/zero of=/dev/hda
```

of course, substitute "/dev/hda" with the actual device file for the hard disk or partition.

Overwriting with zeros will be quicker than using 'shred'*, with pretty much the end result. Only the most determined of attackers will be able to even see that you used to have encrypted data on the disk. Of course, this still won't help them decrypt the data.

*Shred overwrites with random data, I believe. Generating random data is surprisingly intensive on your CPU, whereas just spitting out zeroes is not CPU-intensive at all. That's why overwriting with zeroes is quicker than overwriting with random data.

---

### Post by Chrissd on 2011-09-01
> **egalvan said:**
> dban, from dban.org will erase a drive thoroughly..
enough so that it can be used on government contracts.

Unfortunately I don't have a CD drive to run it. Also, useless little fact, whilst it's secure enough for some governments, the UK government contract I worked on, there was only one approved way for hard drive data to be erased and that was with physical destruction.

Also, 3rdalbum, thanks. I'll just go over it now with the zeros.

Thanks guys.

---

