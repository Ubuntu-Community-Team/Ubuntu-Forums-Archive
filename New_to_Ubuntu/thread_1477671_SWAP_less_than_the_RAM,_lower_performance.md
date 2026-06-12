---
title: "SWAP less than the RAM, lower performance?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by rajnikhil on 2010-05-09
Hi,

I recently did a clean install of Ubuntu 10.04. I have a 1Gb DDR2 RAM and allocated 1.5Gb for SWAP. I now want to add an additional 2Gb of RAM so that I will be able to run windows 7 in virtual box smoothly.

My doubt is whether having 3Gb of RAM and only 1.5Gb of SWAP restrict me from using the full potential of the 3Gb RAM or will I get the better performance of having larger RAM even though the SWAP is smaller in size than RAM.

Thanks.

---

### Post by Speed_arg on 2010-05-09
You won't be able to suspend.

And perfonmance won't be worse. SWAP is only used when you are out of RAM :D That shouldn't occur unless you are using a VEEEEEEEEERY heavy app (or many heavy apps). SWAP is slow. I don't even have a sawp partition (since I don't care about suspend, and I have 4gb)

---

### Post by 3rdalbum on 2010-05-09
You can suspend, but you can't hibernate. And of course you can't hybridnate either.

With 3 GiB of RAM you'll probably never touch the swap anyway. Back when this computer had 2 GiB of RAM it actually never had any swap, and never needed any.

---

### Post by rajnikhil on 2010-05-09
Thank you Speed_arg and 3rdalbum for the quick and easy reply. Thanks a lot.

---

