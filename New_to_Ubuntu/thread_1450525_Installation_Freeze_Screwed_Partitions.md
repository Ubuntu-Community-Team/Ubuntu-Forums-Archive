---
title: "Installation Freeze/ Screwed Partitions"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Pragueinspring on 2010-04-09
I am very new to Linux and spent the last 17 hours trying to figure out which OS I would go with. After a few weeks of actually reading about what Linux was all about, of course. I went with Ubuntu.

First, I ran the Live CD which worked fine multiple times before trying to install it without problem. The installation, which I had intended on sharing a partition with Windows 7, stopped at 15% completion. I hard restarted because I knew of no other way to escape this frozen screen- ESC didn't work nor any of the Function keys and the CD had ceased to be read. I though it was odd that the partition scan didn't recognize that there was another OS installed. I selected and then deselected the "boot (something)" which was one of the three buttons in the bottom right corner. Of my 160GB HD, 89.2 would go to Ubuntu.

I restarted to Windows 7 and checked to see if there was an extra data written to the hard drive and there seemed not to be so I popped the Live CD in and started again. When it got to the partition screen I noticed something very wrong; Not only did it read Windows 7 (199MB), it said I had Windows Vista, an unknown installation (The unfinished installation?), and that with the new Ubuntu installation would leave only 1.5MB left of free space should I continue. That was wrong!

Cancelled the installation, restored the Windows 7 system to an earlier time and restarted to come to a black screen. Twice. Third time I got to safe mode with networking and then I came here. What the heck should I do to remedy this matter?

In the olden days on Windows shipping with CD's I'd simply reinstall Windows clean- that, in these modern times- seems not to be an option.

Here is my computer: [http://www.bestbuy.com/site/Compaq+-+Presario+Laptop+with+Intel%26%23174%3B+Celeron%26%23174%3B+Processor+-+Black/9755437.p?id=1218167800811&skuId=9755437](http://www.bestbuy.com/site/Compaq+-+Presario+Laptop+with+Intel%26%23174%3B+Celeron%26%23174%3B+Processor+-+Black/9755437.p?id=1218167800811&skuId=9755437)

---

### Post by slooow on 2010-04-09
It was a long time ago that I installed a dual-boot with windows. So my advice can only be very sketchy.
First of all you should burn one or several installation DVDs or CDs from the windows system. (Then you are on the safe side, if anything goes wrong.)
Then a CD with parted helps you with to reducing the windows partition to make space for the ubuntu installation. gparted.sourceforge.net
Google for dual-boot linux on windows system. You need some file called boot.ini on the windows system for it to allow it to boot into linux.
And then you can put in the ubuntu live cd.

---

### Post by -humanaut- on 2010-04-09
Did you delete the "compaq restore" feature on it?

---

