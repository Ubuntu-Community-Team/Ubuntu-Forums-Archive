---
title: "swap area"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by bobin on 2009-06-05
why should i allocate so much space for the swap area ? i have never seen my lap EVER using even 10 mb of it? (RAM = 2gb . hence swap area = 2*2.5=5gb)

---

### Post by steeleyuk on 2009-06-05
Its also used if you hibernate your machine. Thats why you should leave at least the same amount of Swap as you have RAM, though its recommended you leave double.

---

### Post by ganesathandavam on 2009-06-05
i want to know is there any way to control the swap space dynamically

like for instance in windows xp we can set the virtual memory size..

but still it requires a reboot for the change to take effect 

(i feel i can understand the logic behind requiring a reboot ...)

but is there any work around ....

how about changing the swap space dynamically

is it possible at all

we need not worry about the time it takes to do this ...

is it possible ???

---

### Post by shaoxiao on 2009-06-05
If you use software like virtual box, the swap usually be used.

---

### Post by Sir Jasper on 2009-06-05
Hi,

I have a desktop. I never hibernate. I never use more than 10 MB of RAM.

On booting  I usually use the command "sudo swapoff /dev/sdb5".

If you do likewise, substituting "sdb5" with your swap partition then if all goes well for say, a week you could use Gparted to reduce the size of your Swap Partition and increase the size of another partition.

Alternatively, you could use Gparted to make your Swap partition inactive for a trial period.

It is, I think, possible to make a Swap file (rather than a Swap partition) but I don't know if that might be of any possible advantage to you.

My regards

---

