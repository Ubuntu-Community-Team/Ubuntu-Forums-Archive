---
title: "linuxdcpp out of control?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Syndacate on 2009-01-30
Hey,

I've been having issues with linux DC++ (linuxdcpp).

It seems to be going renegade and consuming all of my CPU resources - this did NOT happen before, just started today.

Whenever I open it, ksysguard claims DC++ is using 18-30% of my CPU, and top claims DC++ is using 30-40% of my CPU, and regardless of how I look at it, my computer is bogged down to hell, to the point where I can barely do anything.  So I look at the CPU use (total) and ksysguard is reporting 60-90% of my CPU being used (which is what I'd expect from the computer being bogged down this much).  Though when I sort by CPU useage, the only thing that's using memory is ksysguard (like 5% and DC++ (like 18-30%)) - as soon as I kill DC++, it retracts the 18-30% and my CPU drops from 60-90% used, to its typical 5% use.

Top reports 5-10% regardless (which is what it usually is), but top claims that DC++ is using 40%.

Numbers might be thrown due to my CPU being hyperthreaded, but other than that, stats:

8.10 Xubuntu with the QT toolkit and some KDE apps.
1GB DDR RAM
Abit IC7-G mobo
3.0Ghz P4 w/ hyperthreading

Anybody have any input?

USUALLY:
I don't usually check ksysguard or top, but DC++ makes a barely noticeable difference on my computer and CPU useage tends to be around 5-10%.

---

### Post by soxs on 2009-01-30
I am using it almost daily, and it doesn't use more than 10% (Phenom X4 9500). Though it locks up quite often, but whern it runs, it keeps running. Ubuntu 8.10 x86_64

---

### Post by Syndacate on 2009-01-31
> **soxs said:**
> I am using it almost daily, and it doesn't use more than 10% (Phenom X4 9500). Though it locks up quite often, but whern it runs, it keeps running. Ubuntu 8.10 x86_64

I know, I was using it almost daily too until this started happening.

The Phenom is a newer processor though, my P4 3.0 is like 5yrs old, so there's a big difference, apples to oranges in my opinion.  Though yeah, mine usually wouldn't use more than 10% while it was running, and now it's chewing the processor a new ***.  I can't figure it out.

I'm using 32 bit, obviously, as the P4 isn't 64x.

EDIT:
PS:
I'm using 8.10 x64 on my macbook pro and absolutely love it - gets the same (maybe a bit less) battery life (3.5 hours) as OS X on full brightness with the NIC running.  Though my desktop, as you can see, is rather old :(.

I need to buy a new one, but I've been procrastinating - don't want to spend money  :(.

---

