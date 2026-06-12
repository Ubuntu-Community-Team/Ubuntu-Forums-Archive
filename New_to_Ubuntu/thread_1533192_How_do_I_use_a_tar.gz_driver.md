---
title: "How do I use a tar.gz driver?"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by blairm on 2010-07-17
Hi,

Bought my first laptop yesterday and have been having an uphill battle getting wireless to work.
It's a realtek 8192se chipset, and I've located a linux driver on the realtek site... but it's tar.gz and I'm not sure how to proceed from here.
Have been using Ubuntu about five years but until now I've found debs available for everything I need.

Any advice would be greatly appreciated,

Blair

---

### Post by limestone on 2010-07-17
Did ubuntu not support your card from the hardware drivers?? Anyway, you'll have to unpack the .tar.gz and usally you open a terminal and do: 
./configure
make
sudo make install

But sometimes there are other commands, in the .tar.gz you'll find a howto or install/readme file. check that.

---

### Post by blairm on 2010-07-17
Unfortunately there doesn't appear to be suuport; the laptop recognises the local network and establishes a connection but I can't use the internet,

 It could be I'm overlooking something very simple - have zero exerience with wireless on Ubuntu.

Blair

---

### Post by blairm on 2010-07-17
OK, something's odd here; just worked for the time and I haven't changed anything! Never look a gift horse in the mouth, I guess...

Just hope it's working for good

Thanks,

Blair

---

