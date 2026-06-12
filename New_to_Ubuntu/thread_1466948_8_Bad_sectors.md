---
title: "8 Bad sectors"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by UpSignal on 2010-04-30
Hi, today i checked my "disk utility" and it says i have 8 bad sectors. here is the screenshot

[IMG]http://i42.tinypic.com/2hhlv0y.png[/IMG]

How alarmed should i be? this laptop is about 2.5 years age. Never replaced any hardware. Should i expect a failure soon? also, is there a way to fix bad sectors?

---

### Post by Delever on 2010-04-30
No fix, do backups, save money for new hard drive...

---

### Post by UpSignal on 2010-04-30
hm. gonna check the prices. is there a way to clone my disk to the new one? don't want to install ubuntu again :s

---

### Post by psusi on 2010-04-30
> **UpSignal said:**
> hm. gonna check the prices. is there a way to clone my disk to the new one? don't want to install ubuntu again :s

Check out the parted magic cd.  It has a few cloning tools on it including ghost4linux.

I wouldn't go into a panic just yet.  Run the long smart test and see if it finds any more bad sectors.  Look at the pending relocation count too.  The 8 you are looking at have already been remapped to good locations.  Keep an eye on it and as long as you don't develop any more you're fine.  Run the long smart test again in a week or two to make sure no more have come up.

---

### Post by philinux on 2010-04-30
The self assessment says passed. No harm to keep regular backups though.

The smart disk system on your hard drive has already remapped the sectors. Also read error rate it says is good.

Time to worry is if read/write errors start to appear.

---

### Post by quadproc on 2010-04-30
> **UpSignal said:**
> Hi, today i checked my "disk utility" and it says i have 8 bad sectors. here is the screenshot
...
How alarmed should i be? this laptop is about 2.5 years age. Never replaced any hardware. Should i expect a failure soon? also, is there a way to fix bad sectors?
I would suspect that your drive is near its end-of-life.  Prudence dictates that you make preparations for copying your old disk to a new one.

quadproc

---

### Post by philinux on 2010-04-30
[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

---

### Post by UpSignal on 2010-04-30
Thanks for all the advices guys. going to keep a look on it
cheers

---

### Post by Delever on 2010-04-30
Well, no need to panic, especially if you don't keep very important stuff on it. However, if you do, you should not wait until you get damaged mp3 files, half-blanked images, missing files, funny file names and so on. If you do, there is still good chance to get what is left by pluging you hard drive to another computer (I am not sure about this process in case of laptops though).

External drive or flash stick might be a good idea. Usefull to for backing up stuff, and in case your drive keeps working, usefull anyway ;)

---

### Post by Rex Bouwense on 2010-04-30
No one can predict when a hard drive will fail or if it will fail.  However, backing up your data is always a good idea.  I too would keep an eye on it, not anticipation of failure but because it would be the prudent thing to do unless you can afford to lose the data.  Enjoy.

---

### Post by dmb on 2010-04-30
Run 'badblocks /dev/sda' in the terminal. That will test reading from every single sector, and if it can't, that means its bad. If you see more then 3 sector counts, I would replace the hard drive.

---

### Post by psusi on 2010-04-30
> **dmb said:**
> Run 'badblocks /dev/sda' in the terminal. That will test reading from every single sector, and if it can't, that means its bad. If you see more then 3 sector counts, I would replace the hard drive.

Badblocks is obsolete.  Use the SMART tools instead.

---

### Post by UpSignal on 2010-04-30
i'm doing an extensive scan now with smart

---

