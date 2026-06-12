---
title: "Is swap nescessary?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by mamamia88 on 2010-01-13
I have a netbook.  I had 2gb i was going to dedicate to swap but for some reason it says unusable.  does anyone know if it will have a performance hit to go without swap?

---

### Post by SuperSonic4 on 2010-01-13
It will have a performance hit if you use heavy duty apps

---

### Post by mamamia88 on 2010-01-13
so if i just use rhytmbox and firefox i should be alright?  also is it possible to add swap post install?

---

### Post by tom.swartz07 on 2010-01-13
> **mamamia88 said:**
> I have a netbook.  I had 2gb i was going to dedicate to swap but for some reason it says unusable.  does anyone know if it will have a performance hit to go without swap?

yeah, you will get a bit of a loss if you dont have it, and you will lose your ability to suspend/hibernate.

Just out of curiosity, what were you going to use for swap? the way you have it worded, it makes me wonder if you were going to put it on a flash drive or something.

You only need as much swap as you have ram (some say 1.5X ram, still more say 2x) but generally its just used as a 'safe spot' for files you have open but arent using, a place to write your current status if you want to hibernate, and a dedicated 'overflow' for your ram.

---

### Post by A_M_S on 2010-01-13
The swap file is also used when you hibernate your computer.

---

### Post by cherva on 2010-01-13
The SWAP partition is used as if it was RAM ... if you open a lot of things and you need more ram that you have, ubuntu will start writing in the SWAP partition. But the most important thing about SWAP on laptops/netbooks is that if you don't have swap or it is not two times your RAM or bigger you won't be able to SUSPEND the laptop/netbook. In SUSPEND mode your laptop does not require any power because everything from your RAM is written to the hard drives SWAP partition and when you power up the computer everything will return to the state when you SUSPENDED your computer.

P.S 
...... 4 comments for the time I wrote this :) NICE

---

### Post by mamamia88 on 2010-01-13
gparted won't let me create any more partitions so how can i add swap?

---

### Post by SuperSonic4 on 2010-01-13
You can remove an existing partition and create a logical partition on which you can add more than one.

---

### Post by mamamia88 on 2010-01-13
there isn't a partition i can delelte.  right now i have a 100mb system partition for windows, a 80gb partition for the rest of windows, a root partition of 15gb for ubuntu, and a 50gb home partition for ubuntu.  why won't it let me use my dedicated swap space?

---

### Post by HarrisonFan on 2010-01-13
Although I have never tried it, I believe there is a way to create a swap file post install as well.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/")

BTW, I have installed 9.04 on two Aspire One Netbooks both without swap.  I disabled the Hibernate options since this does not work well (or at all) without swap.  Those with the Netbooks haven't had any memory related issues at all.

---

### Post by mamamia88 on 2010-01-13
i opened all my favorite programs at once and the most ram it used was about a quarter of my total ram which is 1gb do you think it's worth bothering installing a swap partition?

---

### Post by JoelbX on 2010-01-13
> **mamamia88 said:**
> there isn't a partition i can delelte.  right  now i have a 100mb system partition for windows, a 80gb partition for  the rest of windows, a root partition of 15gb for ubuntu, and a 50gb  home partition for ubuntu.  why won't it let me use my dedicated swap  space?

Sounds to me like those are all primary partitions. There is a limit of 4  primary partitions, this is probably why you can't add anymore  partitions.
 You could create an extended partition, which doesn't have any  partition limits, but it counts as 1 primary partition. So that would  mean reinstalling either win7 or Ubuntu, since you would have to take a  partition out to make a extended one.

---

### Post by mamamia88 on 2010-01-13
so i can make an extended partition into 2 partitions?  think i am going to do that thanks.  reinstalling ubuntu will take at most half hour think i will go for it

---

### Post by Cheesemill on 2010-01-13
> **cherva said:**
> The SWAP partition is used as if it was RAM ... if you open a lot of things and you need more ram that you have, ubuntu will start writing in the SWAP partition. But the most important thing about SWAP on laptops/netbooks is that if you don't have swap or it is not two times your RAM or bigger you won't be able to SUSPEND the laptop/netbook. In SUSPEND mode your laptop does not require any power because everything from your RAM is written to the hard drives SWAP partition and when you power up the computer everything will return to the state when you SUSPENDED your computer.

That's hibernating your talking about, not suspending.

Also you don't need swap to be twice as big as your RAM to hibernate, you can actually get away with less than your RAM because the working memory gets compressed whilst being written to the swap partition.

---

### Post by JoelbX on 2010-01-13
> **mamamia88 said:**
> so i can make an extended partition into 2 partitions?  think i am going to do that thanks.  reinstalling ubuntu will take at most half hour think i will go for it

You can make logical partitions inside a extended partition, the amount of logical partitions you can have inside the extended partition is unlimited.

Make sure you have backed up any important documents before reinstalling...

---

### Post by LinuxDeal on 2010-01-13
I do not use a swap partition. I have 2GB RAM and have never run into problems.  I can suspend but not hibernate.

I might even argue that the system runs faster without swap because anything swapped will take 100x longer to load.

---

### Post by 2blue on 2010-01-13
I have swap and lots of RAM and still go slow at time. I have had Ubuntu on minimal comptuers, and there was no difference between recommended swap and now swap. I had put in lots of RAM though, in comparison to the processor capacity. The only ting was as mentioned by others here, computer could not hibernate.

---

