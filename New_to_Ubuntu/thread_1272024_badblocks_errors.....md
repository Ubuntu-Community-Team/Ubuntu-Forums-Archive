---
title: "badblocks errors...."
date: 2009-09-21
forum: New to Ubuntu
---

### Post by earthpigg on 2009-09-21
my brother dropped his laptop. which was turned on and had the hard drive spun up.

windows is experiencing boot errors. not a problem, windows can be replaced :D

i took the hd out and am running badblocks on it now using my desktop.

underlined the thousand and million place to make it easier to read...

```
[chris: ~]$ man badblocks
[chris: ~]$ sudo badblocks -nv /dev/sdd
Checking for bad blocks in non-destructive read-write mode
From block 0 to 24_4_19_8_583
Testing with random pattern: rawrjimmy
4638976
4638977
4638978
4638979
[snip -> continued]
4653623
4655252
4655253
4655254
4655255
4656008
4656009
4656010
4656011
4656764
4656765
4656766
4656767
4657520
4657521
4657522
4657523
4658276
4658277
4658278
4663685
4663686
4663687
4664440
4664441
4664442
4664443
4665196
4665197
4665198
4665199
4665952
[continued -> you get the idea...]
4676015
4676768
4676769
4676770
4676771
4677524
4677525
4677526
4677527
_4_67_9_036
```

ive never used badblocks and actually found errors.

are all those numbers being spit back at me blocks that are now bad?

since we are at about 4 million out of 240 million, is it worth even continuing this test?

is the hard drive a brick, or can the badblocks be marked as such and not used when an operating system is reinstalled? since my brother is cheap, will probably not be willing to purchase windows, and since i will not help him pirate it, there is a good chance that will leave Linux as the primary contender.

what would the process be of formatting the hard drive with ext3/4 and marking blocks as bad so subsequent operating systems installed will know not to store data there?

i understand that the hard drive, and laptop in general, can not be expected to operate as reliably as it did before being dropped... but can any reliability be gained at this point? even if badblocks + mark blocks as bad + reinstall needs to be done once a month?

alternative solution is to grab a thumb drive, install onto that, and use the laptop's internal as quasi-reliable storage.

---

### Post by bodhi.zazen on 2009-09-21
In general, yes, bad blocks are a sign of wear and tear on the hard drive. Depending on the age of the HD not all of them may have been caused from a single drop/incident.

In general bad blocks accumulate over time and once you get enough the HD will fail.

With the number you are seeing, I would at a minimum back up your data (off the hard drive).

Personally I like smartmontools:

[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

Good luck ;)

---

