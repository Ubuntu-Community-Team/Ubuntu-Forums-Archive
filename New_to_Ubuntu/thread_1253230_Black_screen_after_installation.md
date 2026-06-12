---
title: "Black screen after installation"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by jltrain on 2009-08-29
I installed Ubuntu on an old computer that was running Windows 2000. This computer is a 
Gateway 450mhz 3842MB of ram. It would not install from the Live CD. I downloaded it to that computer and installed it. The machine turns on but there is nothing on the monitor. The keyboard lights come on briefly. I have tried making a boot disc. Are there any suggestions on what may be the problem and if it worth fixing. Prior to the Ubuntu installation the machine ran fine. Any assistance would be appreciated. Thanks

---

### Post by sandyd on 2009-08-29
a black screen makes me suspect a video problem.

while the black screen is there, can you press ctrl-alt-f1 and see if anything comes up?

---

### Post by jltrain on 2009-08-31
I tried ctrl-alt-F1 and got zip. Would pulling out the video card and reseating be of any use??

---

### Post by halitech on 2009-08-31
does it show the POST info when it first starts? If not, then yes, try reseating the card. If it does and you lose the screen after Ubuntu starts, its a driver issue.

---

### Post by jltrain on 2009-09-01
I tried re-seating the video card. nothing. Nothing comes up on the screen at all. The monitor light stays yellow. Is there simple way to startover. I was actually just trying to salvage an old computer.

---

### Post by QIII on 2009-09-01
Are you sure you have that much RAM, or was it a typo?

How fast did you burn the CD?  A slower speed will yield a better result.

Did you do an md5sum and check the CD's integrity?

It might be worth creating another CD and checking to make sure it is a good image.

Then, a new attempt to install may be in order.

---

### Post by halitech on 2009-09-01
> **jltrain said:**
> I tried re-seating the video card. nothing. Nothing comes up on the screen at all. The monitor light stays yellow. Is there simple way to startover. I was actually just trying to salvage an old computer.

if you don't even see the POST when you turn the computer on, either the card is no good, the motherboard is shot (do you hear any beeps?) the monitor is no good or unplugged. Burning a new cd is pointless at this point as it seems more a hardware problem.

---

### Post by QIII on 2009-09-01
It could be entirely coincidental, but the OP did say the machine worked fine until the install.

I hadn't caught the part about the light staying yellow when the POST should have been occurring.  The BIOS should light the screen.

True enough.

---

### Post by halitech on 2009-09-01
it's also an old machine so I think it's more coincidence that something died when the install finished then anything else.

---

### Post by LewRockwell on 2009-09-01
> **jltrain said:**
> I installed Ubuntu on an old computer that was running Windows 2000. This computer is a 
Gateway 450mhz 3842MB of ram. It would not install from the Live CD. I downloaded it to that computer and installed it. The machine turns on but there is nothing on the monitor. The keyboard lights come on briefly. I have tried making a boot disc. Are there any suggestions on what may be the problem and if it worth fixing. Prior to the Ubuntu installation the machine ran fine. Any assistance would be appreciated. Thanks

just for kicks you might try to run that machine with Damn Small Linux or Puppy Linux

otherwise, just know that we're shredding those daily around here

(we won't even pick them up anymore, folks must use their gas and time to get them here)

still, it is fun to play around with them before smashing them

.

---

### Post by zkriesse on 2009-09-01
Definitely sounds like a driver problem. The BIOS should light up the screen even if it decided to shut off afterwards.

---

### Post by jltrain on 2009-09-02
I tried Puppy linux. Which worked fine when tested on my other PC, but I got zilch with the old Gateway. I would like to thank everyone for there suggestions. At this point I'm taking it too Goodwill along with an "old" printer,scanner. Thanks

---

