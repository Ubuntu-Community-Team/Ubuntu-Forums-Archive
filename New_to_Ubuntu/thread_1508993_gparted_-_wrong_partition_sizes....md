---
title: "gparted - wrong partition sizes..."
date: 2010-06-13
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-13
Just installed 10.04 and created several partitions. When I view the partition sizes using gparted, they're ALL off, and some quite a bit off. For example, I created a partition size of 120GB for photos, but gparted only shows 112 gig. All partitions are several gig off from what I specified during install. Any idea why it's not showing the sizes I specified?

Thanks,

Andy

---

### Post by Locke_99GS on 2010-06-13
Formatting the partition consumes space.

---

### Post by wilee-nilee on 2010-06-13
> **akelsall said:**
> Just installed 10.04 and created several partitions. When I view the partition sizes using gparted, they're ALL off, and some quite a bit off. For example, I created a partition size of 120GB for photos, but gparted only shows 112 gig. All partitions are several gig off from what I specified during install. Any idea why it's not showing the sizes I specified?

Thanks,

Andy

Give us a screen shot of gparted.

---

### Post by dearingj on 2010-06-13
> **akelsall said:**
> Just installed 10.04 and created several partitions. When I view the partition sizes using gparted, they're ALL off, and some quite a bit off. For example, I created a partition size of 120GB for photos, but gparted only shows 112 gig. All partitions are several gig off from what I specified during install. Any idea why it's not showing the sizes I specified?

Sounds to me like gparted is actually showing your partition sizes in [gibibytes]("http://en.wikipedia.org/wiki/Gibibyte"), and whatever you used to create the partitions used [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte"). 120 gigabytes equals approximately 112 gibibytes according to the unit converter I found [here]("http://wintelguy.com/gb2gib.html").

---

### Post by akelsall on 2010-06-14
dearingj I believe you are spot-on. Why the heck would the developers of gparted not stick with Gigabytes? That's what 98% of the population knows and goes by. 

I never even heard of a gibibyte until you responded. Wow! 120 gibibytes does equal roughly 111 gigabytes. Wish I had known that before hand, as I just moved all my data over to my newly formatted harddrive yesterday ](*,)](*,)

Thanks so much for educating me!!

Andy

---

### Post by srs5694 on 2010-06-14
Actually, the difference between gigabytes and gibibytes is not well-understood by most people. For historical reasons, the term "gigabyte" (and related terms, such as "kilobyte", "megabyte", etc.) started out meaning what is technically today known as "gibibyte:" namely, 2^30 bytes. This is what most utilities mean when they refer to units in "gigabytes" or "GB." Unfortunately, this usage violates the usual [International System of Units (SI) prefixes,](http://physics.nist.gov/cuu/Units/prefixes.html) in which the prefix "giga" is reserved for a multiple of 10^9 of the base. For instance, a gigawatt is 10^9 watts. For the "kilo" prefix, the difference was small (1000 vs. 1024), but it grows with higher prefixes; for "mega," it's 1,000,000 vs. 1,048,576, for "giga," it's 1,000,000,000 vs. 1,073,741,824, and so on.

One notable holdout on the initial misuse of SI prefixes in computing was the hard disk industry, which stuck to using megabytes (MB) to refer to 10^6 bytes, gigabytes to refer to 10^9 bytes, and so on. Most disk utilities used the power-of-2 units (MB = 2^20 bytes, GB = 2^30 bytes, etc.), which led to a lot of confusion, and continues to do so.

In many computing realms, power-of-2 units still make a lot of sense. Your computer's memory, for instance, is probably installed in some power-of-2 multiple of bytes, rather than a power-of-10 multiple. In disk storage, the sector size is 512 bytes -- a power-of-2 value that can't be expressed as an integral power of 10. Thus, the exact size of partitions and disks is expressible as integral power-of-2 units, but seldom as integral power-of-10 units. A few years ago, standards organizations came up with new units (mebibytes, MiB; gibibytes, GiB, etc.) to express the power-of-2 units that are still useful to the point of necessity for such purposes.

The trouble we now face is one of fixing all these old references to "MB" as meaning 2^20 bytes, "GB" as meaning 2^30 bytes, and so on. Software that wants to conform to standards rather than perpetuate old sloppiness has two options: Convert the values it reports into power-of-10 values or convert the labels it uses for its power-of-2 values. Sometimes one or the other makes better sense. Other times the choice is arbitrary or a matter of personal preference. Many GNU text-mode tools now seem to offer both options via command-line switches. As this transitional period is underway, there will necessarily be confusion on the part of users who are unfamiliar with the new terms, or even who are unfamiliar with the old (and non-compliant with the SI) uses. The alternative is even greater long-term confusion as sloppy naming continues, and the difference grows greater. (Note that for each new prefix, the difference between true SI values and the not-quite-SI binary equivalent increases -- it's 2.4% for kilo, 4.9% for mega, 7.3% for giga, 10.0% for tera, and so on.)

So I'm sorry to say, you'll just have to get used to it.

---

### Post by akelsall on 2010-06-15
So srs5694, if I understand you correctly, you're saying the the developers of gparted are correct in using GiB to express the partition size? If so, you are correct, it will take some time to "re-school" the general population.

Thanks,

Andy

---

### Post by -kg- on 2010-06-15
> **akelsall said:**
> So srs5694, if I understand you correctly, you're saying the the developers of gparted are correct in using GiB to express the partition size? If so, you are correct, it will take some time to "re-school" the general population.

Thanks,

Andy

It's been an ongoing issue (and debate) for ages now.  Hard drive manufacturers ***love*** to use GB...it makes their hard drives seem larger than GiB would.

:lolflag:

---

### Post by akelsall on 2010-06-15
So, KG, I guess that begs the question "What is the TRUE size of a harddrive? Is it the size expressed in GiB, or GB?

Thanks,

Andy

---

### Post by -kg- on 2010-06-16
> **akelsall said:**
> So, KG, I guess that begs the question "What is the TRUE size of a harddrive? Is it the size expressed in GiB, or GB?

Thanks,

Andy

All I can give you is my opinion.  Since hard drives are accessed by a computer, which is based on binary code, I would say that GiB would be correct, being the measurement is in base 2, and more easily converted to octal and hexadecimal.  Disk locations are expressed as a hexadecimal address.

One thing is certain, though (again, IMHO)...a standard should be accepted and used universally.  It can get confusing trying to figure out which figure is being used and whether you need to convert it to the other for other uses.

---

### Post by srs5694 on 2010-06-16
> **akelsall said:**
> So, KG, I guess that begs the question "What is the TRUE size of a harddrive? Is it the size expressed in GiB, or GB?

This is like asking "what is the TRUE speed of a car? Is it the speed expressed in mph, or km/h?" The answer is that both values are (or at least can be) correct. In the case of a car's speed, which you prefer depends on whether you're more comfortable with English measures (now used mainly just in the USA) or metric (used everywhere else). In the case of computer units such as disk space, it's more of a judgment call because the difference is numerically smaller and most people have only rather imprecise notions about what these units are, much less the differences between GB and GiB. A value in either unit is likely to be rounded slightly (213.7GB rather than 213.723918GB, or whatever), so neither is really more precise, at least not in terms of disk space in use. (GiB does offer advantages when real precision is important, such as when laying out disk partitions, since the basic units for partition placement are in power-of-2 multiples.)

IMHO, at this point the most important thing for program authors to do is to use the correct label -- that is, to use "GB" or "gigabytes" for power-of-10 units and "GiB" or "gibibytes" for power-of-2 units. Users will just have to learn both. In the long run, this is better than perpetuating incorrect use of SI labels for power-of-2 units, which is ambiguous and confusing in other ways.

---

