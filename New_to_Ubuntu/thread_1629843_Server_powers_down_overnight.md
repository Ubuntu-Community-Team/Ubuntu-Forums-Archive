---
title: "Server powers down overnight"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by soonerken on 2010-11-24
Morning afternoon and Evening. I need help. I'm pretty much a beginner so pretty simple jargon would be great. I have built my first server(purely media storage) Overnight it shuts itself off. After sifting through the message logs the common error I receive is a "Resume from disk fails". Failed to write the number down and as I'm at work, for the moment, will be a bit before I can get to it, to give specifics. But a place to start would be great. 1st post of many I have a feeling. :) thank you all.

---

### Post by papibe on 2010-11-24
Could you give us more details?

Is it a well known brand computer? which model? If you build it up from scratch, which parts did you use (processor and motherboard are very important)? 

It looks like a power saving issue, which is pretty common default setting on a laptop, and not so much on a desktop. Nevertheless, with more info, we may come up with better ideas.

Regards.

---

### Post by soonerken on 2010-11-24
I will get that info in a few hours when I get to the server. I believe it is an intel board, just an old clunker that I added a PCI Raid card to and various other things.

1 thing of note is that this thing has worked flawlessly for over 8 months. I had a ram issue over the weekend I removed the stick of ram in the first dimm and the error there went away. So I assume it was a bad stick of ram. Of course that was confirmed through the bios not through the server itself. Also I didn't add the same amount of ram back in should I have?

---

### Post by papibe on 2010-11-24
> **soonerken said:**
> ... just an old clunker ...I had a ram issue over the weekend I removed the stick of ram in the first dimm and the error there went away...
I see. That opens other possibilities. Have you run the RAM test? I think it would be a good idea to test the remaining RAM stick. You can do that by hitting ESC while booting to get to grub. Select memtest86. The longer you run the test the better. I'd suggest s couple of hours.

> **soonerken said:**
> ... Also I didn't add the same amount of ram back in should I have?
Not necessarily, but you should have at least the minimum RAM recommended to run Ubuntu. Check that [here]("https://help.ubuntu.com/community/Installation/SystemRequirements"). 

Regards.

---

### Post by pricetech on 2010-11-24
Just a thought, based upon experience.  Does the room where the server is located change temperature at night ??

Had an old board with what turned out to be either a crack or a cold solder joint that would fault every night when it got cold in the shop.

Just a thought.

---

### Post by soonerken on 2010-11-24
Good on minimum amounts of ram. Out of curiosity is there a way to run a test through an SSH client? I don't wanna have to drag the blasted thing out of the closet and hook to a monitor(I can mind ya but just curious for alternative). Again pretty much a newbie when it comes to commands and capabilities from command line.

---

### Post by soonerken on 2010-11-24
Good on minimum amounts of ram. Out of curiosity is there a way to run a test through an SSH client? I don't wanna have to drag the blasted thing out of the closet and hook to a monitor(I can mind ya but just curious for alternative). Again pretty much a newbie when it comes to commands and capabilities from command line.

---

### Post by soonerken on 2010-11-24
> **pricetech said:**
> Just a thought, based upon experience.  Does the room where the server is located change temperature at night ??

Had an old board with what turned out to be either a crack or a cold solder joint that would fault every night when it got cold in the shop.

Just a thought.

That is possible. I hope that isn't the case. The temps here have been rather mild of late but lots of humidity.

---

### Post by soonerken on 2010-11-26
This issue is resolved turned out it was a bad PSU ugh :( thanks for your time folks.

---

