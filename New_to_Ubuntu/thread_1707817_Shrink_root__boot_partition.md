---
title: "Shrink root / boot partition?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by purebuilt on 2011-03-15
Hello,

I an new to Linux and when I set up my disk I gave root 54 GB and Home 100 GB and Swap 6GB. Who knew the OS didn't need that much space? :)  Can I shrink the 54GB to 15GB and give 14GB to the Home partition without losing any data?

Thanks. I am using Ubuntu 10.04 LTS.

DB

---

### Post by crispy_420 on 2011-03-15
Maybe, just maybe this could work but keep in mind this is just a guess. Boot into a LiveCD designed for editing partitions like Parted Magic or GParted. They both have the ability to resize partitions. Then shrink /root and grow the other to fill that gap. I have not tried this with a Linux system just windows.

---

### Post by Paqman on 2011-03-15
Yep, it'll work fine. Just do what crispy_420 said, boot up into a LiveCD. You need to do this because you can't change any partition while it's mounted, so you need to be running off a CD or USB. Once you've got Gparted open right click on your swap partition and "swapoff", that'll allow you to make any changes you want.

Back up your data before you make any changes, just in case.

---

### Post by purebuilt on 2011-03-17
Thanks. Looks like it is working and gparted was on the liveCD. Took me a while to figure out I had to extend the logical partition into the new space and *then *extend the partitions within it, but I got it.

Thanks!

:)

---

### Post by Dutch70 on 2011-03-17
> **purebuilt said:**
> Hello,

I an new to Linux and when I set up my disk I gave root 54 GB and Home 100 GB and Swap 6GB. Who knew the OS didn't need that much space? :)  Can I shrink the 54GB to 15GB and give 14GB to the Home partition without losing any data?

Thanks. I am using Ubuntu 10.04 LTS.

DB

Just curious what you're going to do with the other 29GB? 

 Also, It looks like you may be wasting Gigs with your swap space too, Unless you  have 6GB of RAM. Swap only needs to be equal to your pysical RAM & then that's only if you want to hibernate. I know disk space is cheap these days, still 1-2 GB's is a substantial amount of **storage**. No sense in totally wasting it.

---

### Post by crispy_420 on 2011-03-17
I was under the impression that swap space should be bare minimum equal to the size of physical RAM but ideally should be more if the option is available, so maybe 150% the size of RAM. But a lot depends on tasks being done of course. But everyone has their own opinion and there is no standard answer.

[https://help.ubuntu.com/community/SwapFaq#How](https://help.ubuntu.com/community/SwapFaq#How) much swap do I need?

---

### Post by Dutch70 on 2011-03-18
> **crispy_420 said:**
> I was under the impression that swap space should be bare minimum equal to the size of physical RAM but ideally should be more if the option is available, so maybe 150% the size of RAM. But a lot depends on tasks being done of course. But everyone has their own opinion and there is no standard answer.

[https://help.ubuntu.com/community/SwapFaq#How](https://help.ubuntu.com/community/SwapFaq#How) much swap do I need?

crispy_420, You need to visit KY sometime. :popcorn:

Anyway, that's the same link I give people that have a lot of questions about Swap. I agree with the swap being equal to RAM plus a little extra for good measure, but I've never actually heard of anyone having problems hibernating because of the size of their swap partition, if it was equal to the size of their RAM. That's how mine is set up & i've never had a problem either. Imho 110% would be plenty extra.

---

### Post by deconstrained on 2011-03-18
Depends on what filesystem you have set up on the root partition. As long as it's not JFS or some freaky-deaky filesystem that isn't very well supported you should have no trouble resizing it.

---

### Post by crispy_420 on 2011-03-18
> **Dutch70 said:**
> crispy_420, You need to visit KY sometime. :popcorn:

Strangely I probably have been through Corbin, KY.

---

### Post by Dutch70 on 2011-03-18
> **crispy_420 said:**
> Strangely I probably have been through Corbin, KY.

If you've been through KY on I-75, then you probably have.

---

### Post by purebuilt on 2011-03-19
I added the 29GB to /Home where I have some Windows VMs that are rather large. I needed the room to defrag them. As for the SWAP the recommendation was 2x the RAM. This system has 4GB. 

Thanks.

DB

---

### Post by Dutch70 on 2011-03-20
> **purebuilt said:**
> I added the 29GB to /Home where I have some Windows VMs that are rather large. I needed the room to defrag them. As for the SWAP the recommendation was 2x the RAM. This system has 4GB. 

Thanks.
DB

The recommendation of 2x RAM is incorrect, it was intended for people with very low RAM(256-512MB). Although it doesn't hurt anything to have extra. Swap only needs to be equal to the physical RAM.
[[COLOR="Blue"]SwapFAQ's[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

Anyway, did you get everything else worked out?

---

