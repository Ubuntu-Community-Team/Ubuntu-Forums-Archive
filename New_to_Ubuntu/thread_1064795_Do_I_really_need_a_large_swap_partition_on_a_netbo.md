---
title: "Do I really need a large swap partition on a netbook?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by cyclone5uk on 2009-02-09
I have 2gb of ram in my Asus EEE PC 901. I currently run a version of Hardy which includes a custom Kernel for the EEE PC.

The default install allocated me about 250mb of swap space. When I look on system monitor I rarely seem to use more than half of my RAM, and never more than 70% of my CPU. Of course on a netbook I'm not doing things like editing videos or graphics manipulation.

My swap usage (according to system monitor) is always at 0%. Obviously using a 4gb SSD for my operating system, I need every bit of space available – and the swap just seems like a waste of space.

I know I need a swap partition for a linux install, but can I allocate it a much smaller token amount of space (like 25mb or something)? Surely this wont have any detrimental affects on my usage?

---

### Post by tad1073 on 2009-02-09
I think the minimum swap space you can have is 8mb

---

### Post by ByteJuggler on 2009-02-09
IMHO, no you don't need much swap for the uses you put the machine to (and attested to by your own monitoring.) But to reclaim the space currently allocated is probably more hassle than it's worth.  (Aside, one can always add swap space in a file later even if you don't have a swap partition.)

---

### Post by ByteJuggler on 2009-02-09
> **tad1073 said:**
> I think the minimum swap space you can have is 8mb

Actually no, it's possible to run entirely without swap, if you have enough physical RAM, of course.  (Fairly easy on today's multi GB RAM machines.)

---

### Post by snowpine on 2009-02-09
You do not need a swap partition, and in fact if your eee has a SSD, many people recommend not using a swap partition to prolong the lifespan of the drive. The only reason to have a swap partition in my opinion is if you want the ability to hibernate, but if that is the case, your swap must be at least as large as your ram (250mb won't cut it).

---

### Post by cyclone5uk on 2009-02-09
Good point about the hibernate function - but luckily it's something I never use.

Eventually I plan to replace the 4gb SSD with a larger/faster SSD (Runcore make some good SSDs), so when I reinstall after that, I'll be sure to manually configure the swap size to something smaller than I have now.

---

### Post by billgoldberg on 2009-02-09
> **cyclone5uk said:**
> I have 2gb of ram in my Asus EEE PC 901. I currently run a version of Hardy which includes a custom Kernel for the EEE PC.

The default install allocated me about 250mb of swap space. When I look on system monitor I rarely seem to use more than half of my RAM, and never more than 70% of my CPU. Of course on a netbook I'm not doing things like editing videos or graphics manipulation.

My swap usage (according to system monitor) is always at 0%. Obviously using a 4gb SSD for my operating system, I need every bit of space available &#8211; and the swap just seems like a waste of space.

I know I need a swap partition for a linux install, but can I allocate it a much smaller token amount of space (like 25mb or something)? Surely this wont have any detrimental affects on my usage?

Ok.

You shouldn't be using any swap at all on SSD hard drives. It wears them out too fast.

Also you'll need to tweak your install to perform better with SSD drives:

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

Also if you can, use a non journaling file system (ext2) instead of ext3. Also better for the SSD lifespan.

--

I only have 1gb of ram on my Asus Eeepc 900 and I never even came close to filling it up.

---

### Post by mechanic on 2009-02-09
You can decline to set a swap partition during Ub. install, the system complains a bit but ignore the warnings. If you decide later you want to hibernate, you can set up a swap file instead.

---

### Post by ByteJuggler on 2009-02-09
> **mechanic said:**
> You can decline to set a swap partition during Ub. install, the system complains a bit but ignore the warnings. If you decide later you want to hibernate, you can set up a swap file instead.

No, you can't hibernate to a swapfile, it has to be a swap partition.  See [here]("https://help.ubuntu.com/community/SwapFaq"). 


>       
_Hibernation needs swap_

The hibernation feature (suspend-to-disk) writes out the contents of the memory to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system. 

Please people, try to be accurate when you answer.  Don't guess, or if you do, make sure you qualify your answer as a guess.

---

