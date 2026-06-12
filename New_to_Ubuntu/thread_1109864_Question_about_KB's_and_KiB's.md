---
title: "Question about KB's and KiB's"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by 311005901 on 2009-03-29
I know one is 1024 units and the other is 1000 units and the "i" is added to get rid of the confusion,

But I'm confused. Which one's which?
[IMG]http://img155.imageshack.us/img155/4895/32710870.jpg[/IMG]

PS: Please don't flame me... :sad:

---

### Post by jakupl on 2009-03-29
This has an upper case K, so I would think that this is
one kibibit 1 Kibit = 2^10 bit = 1.024 bit
as opposed to:
one kilobit 1 kbit = 10^3 bit = 1.000 bit
However, I am not sure

---

### Post by Lawand on 2009-03-29
1 KiB = 1 kibibyte = 1,024 bytes
1 KB = 1 Kilobyte which is equal to either 1,024 bytes or 1,000 bytes, depending on context.

Source: Wikipedia

For more info, read this article: [When is a kilobyte a kibibyte? And an MB an MiB?]("http://www.iec.ch/zone/si/si_bytes.htm").

---

### Post by aikiwolfie on 2009-03-29
[Wikipedia actually explains this quite well.]("http://en.wikipedia.org/wiki/KiB")

To try and keep it simple. 1024 = memory in your PC, the size of a file for example. 1000 is network or hard disk transfer speeds.

What the prefixes mean is contextual. Lower case is normally bits. Uppercase is normally bytes. The definition of a kilobit or kilobyte, 1024 or 1000, depends on the context of the measurement.

1KiB = 1 KiloByte and is 1024 bytes. This is used to distinguish measurments bound by powers of 2, like the memory in a PC, from measurements not bound by powers of 2, like network transfer speeds.

---

### Post by sgosnell on 2009-03-29
But in actual use, all these distinctions get very blurry.  Manufacturers report memory, HDD size, and pretty much everything else in multiples of 1000, not 1024, to make the numbers seem bigger.  You 1GB memory stick doesn't actually have a gigabyte of memory, most likely, but 1,000,000,000 bytes, or just over 976MB.  The abbreviations mean whatever the user wants them to mean in real life, regardless of the formal definitions.

---

### Post by sdennie on 2009-03-29
I think this is probably the definitive source on this question: [http://xkcd.com/394/](http://xkcd.com/394/)

---

### Post by Lawand on 2009-03-30
funny :)

---

### Post by scorp123 on 2009-03-30
> **311005901 said:**
> I know one is 1024 units and the other is 1000 units and the "i" is added to get rid of the confusion Nope. It was added to create the confusion ;)

In the good old days (back in the 1980's) when only the toughest men and women dared to work with computers (e.g. because they were such loud and unfriendly big iron monsters back then ...) everything was clear:

1 MegaByte = 1024 KiloBytes = 1024 * 1024 Bytes = 1048576 Bytes

But then along came some sales guys who found out that by falsely advertising their products they could make more money by cheating people. So they started this BS and they e.g. started selling bigger and better harddisks .... **"brand new! 500 MB disks!!"**

And only when you looked at the small print you could see that you were cheated, for there was a sticker which explained their deeply flawed math: **"500 MB = 500'000'000 Bytes"**

They still do this, up to this day. Only that the harddisks got even bigger and that there are more zeros involved, and that people therefore get cheated even more. Don't believe me?

When you buy a "500 GB" disk these days then this size was calculated by the sales department, so their deeply flawed and unfair math applies here: "500 GB = 500'000 MB = 500'000'000 KB = 500'000'000'000 Bytes".

So you didn't buy a "500 GB" disk. What you bought is a "500'000'000'000 Bytes" disk. **Nope, the two are not the same!!**

Let's do the real math - and divide that number by steps of 1024:

500'000'000'000 Bytes = 488'281'250 KB = 476'837 MB **_= 465 GB_**

And whoooosh! A whopping 35 GB disappear from your "500 GB" disk when you do the math right. So when you buy a "500 GB" harddisk ... you in fact bought a 465 GiB harddisk. Not exactly the same!

So, can you sue them? No. Unfortunately not. By international standards the abbreviations such as "kilo" mean "steps of 1000". And "mega" means "steps of one million". e.g. 1 kg = 1 kilogram = 1000 grams. 1 Megaton = 1 million tons, and so forth. 

So the sales guys who came up with this way of cheating can get away with it because their way of calculating disk sizes etc. is perfectly legal and within international standards. Unfortunately.

So that's why (IT- ?) people came up with these new-fashioned units "KiB", "MiB", and "GiB" to denote the "steps of 1024" again. It seems some people felt that this was necessary because the old-style ways of calculating "1 KB = 1024 Bytes" had dropped out of use, everybody was now referring to 1 KB as being "1000 Bytes" ....

Hence the difference.

I personally say: scr*** that. I refuse to use those new-style units. "kibibytes" ... Riiiight.

1 KB = 1024 Bytes. And basta.

BTW, they are cheating with DVD's too, you know? You don't really believe that an empty DVD can _really_ hold 4.7 GB of data? :D  Or that a double-layer DVD can _really_ hold 8.5 GB of data? Nope. Do the math. And you will see that DVD's are quite a bit smaller than what they advertise ;)

---

### Post by sdennie on 2009-03-30
I think my link more accurately describes what scorp123 said.

---

### Post by LowSky on 2009-03-30
KB= 1024
KiB=1000

both can be use interchangably, as most manufacurers us the 1000 number to mess with people when buying hard drives and the like.

So when you buy a 80 GB hard drive you are really getting a 71Gb hard drive, the issue arises from manufacturers using the 1000 scale (which is wrong) and the operating system using the 1024 (which is correct)

Manufacturers are comming under more and more fire as drives and data transmission speeds get larger and larger. For instance a 10 GB drive may have 9.4GB usuable in an OS, while 750GB will only get about 680GB. The loss is very confusing and annoying to people unaware of this marketing gimmick.

---

### Post by FraggedLocust on 2009-03-30
Won't the "interchangeable" numbers start to show real discrepancy when we get up into high terabytes of usage? I suppose everything will keep scaling as it usually does and it won't matter in the end.

---

### Post by sgosnell on 2009-03-30
Get screwed often enough and you get used to it, and eventually don't even notice it.  Marketing always wins, and soon only old dinosaurs like us will even remember that a kilobyte was ever 1024 bytes.  I'm old enough to remember that when I was in college, the university had a computer.  One.  It had its own **building**.  Heaven help you if you dropped your foot-high stack of punch cards and got them out of order.  Your program was fried until you could get tham back in the correct order.

---

### Post by Yashiro on 2009-03-30
Gnome uses **KB** to represent **1024 bytes**.
Nautilus should consider switching to KiB.

k  = 1000
Ki = 1024
B  = byte
b  = bit

---

### Post by aikiwolfie on 2009-04-02
At the end of the day when we now have 2 terra-byte hard drives and 8 giga-bytes of RAM is becoming common place with 1 giga-byte of video RAM it really doesn't matter.

---

### Post by Flimm on 2009-04-02
I can't believe how many people got it wrong.
1KiB = 1024
It was supposed to eliminate the confusion of KB or kB, which look too similar to the kilo 1000 of the metric system.

---

### Post by Penguin Guy on 2009-04-02
This might sound like a stupid question; but why not just have, say, 10bits to a byte?

---

### Post by jakupl on 2009-04-02
> **Penguin Guy said:**
> This might sound like a stupid question; but why not just have, say, 10bits to a byte?

[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

---

### Post by aikiwolfie on 2009-04-03
> **Penguin Guy said:**
> This might sound like a stupid question; but why not just have, say, 10bits to a byte?It all comes down to how computers count in binary.

---

### Post by jakupl on 2009-04-06
> **aikiwolfie said:**
> At the end of the day when we now have 2 terra-byte hard drives and 8 giga-bytes of RAM is becoming common place with 1 giga-byte of video RAM it really doesn't matter.

No it still matters. The difference is always the same, percentage wise.
For instance, I have a 1TB external hard drive... If it were one real terabite, it would be,

8796093022208  Bits (b)
1099511627776  Bytes (B)
1073741824 Kilobytes (kB)
1048576 Megabytes (MB)
1024 Gigabytes (GB)
1  Terabytes (TB)

But what I actually have is,

8000000000000 Bits (b)
1000000000000 Bytes (B)
976562500 Kilobytes (kB)
953674.31640625 Megabytes (MB)
931.3225746154785 Gigabytes (GB)
0.9094947017729282 Terabytes (TB)

So as you see, when it comes to one terabyte, the difference is 92.6774253845215 GB... That is huge.

---

### Post by 311005901 on 2009-04-07
> **Lawand said:**
> 1 KiB = 1 kibibyte = 1,024 bytes 1 KB = 1 Kilobyte which is equal to either 1,024 bytes or 1,000 bytes, depending on context...
Hmm... Ok. I understand.
> **LowSky said:**
> KB= 1024 KiB=1000 both can be use interchangably, as most manufacurers us the 1000 number to mess with people when buying hard drives and the like.
So when you buy a 80 GB hard drive you are really getting a 71Gb hard drive, the issue arises from manufacturers using the 1000 scale (which is wrong) and the operating system using the 1024 (which is correct)
Manufacturers are comming under more and more fire as drives and data transmission speeds get larger and larger. For instance a 10 GB drive may have 9.4GB usuable in an OS, while 750GB will only get about 680GB. The loss is very confusing and annoying to people unaware of this marketing gimmick.
What the? Isn't this opposite of what Lawand said?

> **scorp123 said:**
> ...It was added to create the confusion ;)
In the good old days (back in the 1980's) when only the toughest men and women dared to work with computers (e.g. because they were such loud and unfriendly big iron monsters back then ...) everything was clear:

1 MegaByte = 1024 KiloBytes = 1024 * 1024 Bytes = 1048576 Bytes
But then along came some sales guys who found out that by falsely advertising their products they could make more money by cheating people. So they started this BS and they e.g. started selling bigger and better harddisks ...
...So the sales guys who came up with this way of cheating ...
BTW, they are cheating with DVD's too, you know? You don't really believe that an empty DVD can _really_ hold 4.7 GB of data? :D  Or that a double-layer DVD can _really_ hold 8.5 GB of data? Nope. Do the math. And you will see that DVD's are quite a bit smaller than what they advertise...
What's this I hearrr!? A conspiracy of computer product advertising!? _**Ubuntu is involved in this conspiracy people!_** Call the press! :roll:


I think I understand the separation now, but Ubuntu (and/or GNOME) currently uses both and it can be confusing.
Somebody grab a developer and a pen and include this in HIG. Please.

Pics related.
Both are of my USB flash drive, one screenie in Nautilus (using GB) and the other in gParted (using GiB).

---

