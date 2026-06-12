---
title: "palimpsest disk utility tells me I have many bad sectors"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by joshuapbell on 2010-01-26
on my windows xp partition, is that a bad sign? how do i go about fixing it?

---

### Post by lotharmat on 2010-01-26
How many bad sectors exactly?

If it is a ludicrous number then you can pretty much assume that palimpsest is mis-reporting

If it is a sensible number; keep an eye on it. If it starts rising; it could be an early indication of HDD failure.

I RMA'd a Samsung drive when this number went from 89 to 108 in one day - No questions asked!

---

### Post by joshuapbell on 2010-01-26
> **lotharmat said:**
> How many bad sectors exactly?

If it is a ludicrous number then you can pretty much assume that palimpsest is mis-reporting

If it is a sensible number; keep an eye on it. If it starts rising; it could be an early indication of HDD failure.

I RMA'd a Samsung drive when this number went from 89 to 108 in one day - No questions asked!

here is a screenshot maybe it will make more sense to you then me, but i think it is telling that there is only one sector that is bad??

---

### Post by lotharmat on 2010-01-26
What does the re-allocated sector count say?

To be honest '-1' bad sectors sounds as if the utility is mis-reading the SMART data.

There are other utilities that can read this SMART data - Although I cannot remember the names at the moment:

Windows has got one called 'Crystal Disk Info' - Get it from Snapfiles.com

Best of luck.

---

### Post by joshuapbell on 2010-01-26
> **lotharmat said:**
> What does the re-allocated sector count say?

To be honest '-1' bad sectors sounds as if the utility is mis-reading the SMART data.

There are other utilities that can read this SMART data - Although I cannot remember the names at the moment:

Windows has got one called 'Crystal Disk Info' - Get it from Snapfiles.com

Best of luck.

re-allocated sector count in new screenshot

---

### Post by warfacegod on 2010-01-26
gsmartcontrol is much less prone to false positives. Using it and Palimpset is wise. It's like going to the Doctor, if one tells you, "You have six months to live." go get a second opinion. Or, if a Doctor says, "Your fit as an ox." when your exsanguinating from your femoral artery because a Great White Shark decided to use your thigh as an mid-morning snack, go get a second opinion.

---

### Post by Paqman on 2010-01-26
Can you scroll through those SMART attributes and find which one has something other than "Good" under the assesment column, then let us know what it says?

---

### Post by joshuapbell on 2010-01-26
gsmartcontrol reports one bad sector, so i guess Palimpset is correct, so how do i go about fixing this?

> **warfacegod said:**
> gsmartcontrol is much less prone to false positives. Using it and Palimpset is wise. It's like going to the Doctor, if one tells you, "You have six months to live." go get a second opinion. Or, if a Doctor says, "Your fit as an ox." when your exsanguinating from your femoral artery because a Great White Shark decided to use your thigh as an mid-morning snack, go get a second opinion.

---

### Post by Paqman on 2010-01-26
One bad sector is no problem at all, as long as the drive has remapped it correctly. If it's in the "reallocated sector" count then you don't need to do anything, the drive has dealt with it.

---

### Post by warfacegod on 2010-01-26
> **joshuapbell said:**
> gsmartcontrol reports one bad sector, so i guess Palimpset is correct, so how do i go about fixing this?

Frankly, I wouldn't worry about it. If they both said around 50 or more, then I'd look into fixing it.

In essence there are two kinds of bad sectors. Software and hardware. Software sectors can be repaired probably most easily by removing everything from the drive and reformatting it. If it's hardware, you're SOL because that means there is actual physical damage to your HDD plater. Replacing is the only solution.

Again though, you only have one so don't worry about it. Just test it every day or so and if, in a week or two, the number is rising, that's when it's time to replace or repair. Making a backup won't go amiss though, just in case.

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by joshuapbell on 2010-01-26
Thanks for the information, i have been getting the warning for a while, just now finding the time to ask about it, so i am guessing that it is not getting any worse. 

> **warfacegod said:**
> Frankly, I wouldn't worry about it. If they both said around 50 or more, then I'd look into fixing it.

In essence there are two kinds of bad sectors. Software and hardware. Software sectors can be repaired probably most easily by removing everything from the drive and reformatting it. If it's hardware, you're SOL because that means there is actual physical damage to your HDD plater. Replacing is the only solution.

Again though, you only have one so don't worry about it. Just test it every day or so and if, in a week or two, the number is rising, that's when it's time to replace or repair. Making a backup won't go amiss though, just in case.

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by warfacegod on 2010-01-26
Glad to help. To be on the safe side, read the thread I posted, it's about making backups. I use it regularly. If you feel that your issue has been resolved to our satisfaction then please mark as solved under thread tools.

---

### Post by joshuapbell on 2010-01-26
Backups are not an issue already have a plan in place. Thanks for the suggestion though

> **warfacegod said:**
> Glad to help. To be on the safe side, read the thread I posted, it's about making backups. I use it regularly. If you feel that your issue has been resolved to our satisfaction then please mark as solved under thread tools.

---

