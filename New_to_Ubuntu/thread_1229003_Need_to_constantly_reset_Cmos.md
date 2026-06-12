---
title: "Need to constantly reset Cmos"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by julian.irwin on 2009-08-01
Sometimes when I turn on my computer there is no video output and neither the bios or grub load. Is my processor overheating? I just built this comp and I'm wondering if I applied th thermal paste incorrectly. I fix the problem by restarting a fee times abd if that doesn't work I have to press the hard reset CMOS button. Can I fix this?

---

### Post by LookTJ on 2009-08-01
Sounds like a dying CMOS battery, though I hope someone else can confirm this.

---

### Post by LowSky on 2009-08-01
could be a short on the motherboard, sometimes we get lemons

---

### Post by julian.irwin on 2009-08-01
This is a brand new motherboard. Once I get it to load the BIOS it works fine. Could the problem have been caused by any bad moves by me when I was installing the parts?

---

### Post by LookTJ on 2009-08-01
> **julian.irwin said:**
> This is a brand new motherboard. Once I get it to load the BIOS it works fine. Could the problem have been caused by any bad moves by me when I was installing the parts?
Sometimes new motherboards go bad, and we have to ask for replacement motherboard ;). Also known as RMA

---

### Post by julian.irwin on 2009-08-01
Will I damage anything by reseting so often? Unless the problem gets worse this is just a minor inconvenience. Is it better to get it fixed or can I let it be?

---

### Post by LookTJ on 2009-08-01
do you have an older motherboard?  You could take the CMOS battery of that mobo and put it in the new mobo. Then see if the problem persists.

---

### Post by SuperSonic4 on 2009-08-01
It's likely to be one of three things:

[list=A]
[*]Poor CMOS battery - may be a new motherboard for *you* but how long has it been sitting in a warehouse?
[*]Old BIOS - Particularly on older models when there is an error fixed in a later patch
[*]Dodgy motherboard
[/list]

Solutions include [list=A]
[*]Replace the CMOS battery with another one of the same type
[*]Flashing the BIOS (but be careful with this...very careful). Ensure your problem would be fixed with a flashing
[*]RMA it
[/list]

---

### Post by aesis05401 on 2009-08-01
I will add that most common electrical problem I see on Mobos is from flexing the board when seating components.  When building always be aware of how much pressure you are using and how suddenly you apply.  Apply slowly even if you must build pressure pretty high and make sure mobo is supported properly when you press on it.

That being said, I think that general mobo reject rate is around 3%, but I don't have a ref link for that num.  That means over time three of every hundred customers will need to return their product as defective.  

With this in mind, you should remain open to returning the product instead of living with a compromise.  It is very possible that you are dealing with manufacturing defect.

**Edit: ** If thermal goop is applied incorrectly the machine will usually start hard locking because modern CPUs have thermal protection on board.  You should be able to go into your bios and view last time thermal protection was tripped.  The way the field is worded varies a bit, but this information should be present somewhere in there.

---

### Post by LewRockwell on 2009-08-01
> **julian.irwin said:**
> Sometimes when I turn on my computer there is no video output and neither the bios or grub load.

to troubleshoot for a bad switch you should take the cover off and observe whether the power supply and fans power up

your statement isn't clear and precise enough for a specific determination

> **julian.irwin said:**
> Is my processor overheating?

from your statement above you are having a problem getting the machine to start up...if it has been off then it is doubtful that it is overheated when you first try to switch it on

> **julian.irwin said:**
> I just built this comp and I'm wondering if I applied th thermal paste incorrectly.

thermal compound is pretty straightforward(sometimes when it's mis-applied or over-applied the excess finds it's way to shorting out the processor or other board level component-I use plastic-safe electronics contact cleaner and/or alcohol to clean them up)

> **julian.irwin said:**
> I fix the problem by restarting a few times and if that doesn't work I have to press the hard reset CMOS button. Can I fix this?

I'm not sure what you are referring to regarding a "CMOS button"

motherboards usually just have a jumper that resets the CMOS

keep us posted on what you find out

.

---

### Post by Trebaruna on 2009-08-01
It may not be the most obvious bit that's the problem. Have you double-checked that you wired everything up properly and that all your components are properly seated (sometimes this takes some gentle but stern force)?
Do you know your power supply is good? Bad PSUs can cause a range of vague symptoms that could be anything.

Did you stress the parts at all? Run memtest for a bunch of hours (overnight, perhaps), get a video benchmarking tool and stress the GPU; likewise for the CPU.
I know this is a hassle, and perhaps a bit of overkill, but it is a good way to spot problems very early on.

---

