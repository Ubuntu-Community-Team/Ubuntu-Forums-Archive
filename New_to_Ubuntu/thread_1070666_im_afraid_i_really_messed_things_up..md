---
title: "im afraid i really messed things up."
date: 2009-02-15
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-02-15
ok so i was testing a boot cd in my windows partition just to see if it would read since i was having issues with the disc. 
suddenly my sceen went blank. i restarted the compter and now my bios will not start up. all i get is a blank screen and it continualy restarts to no avail.

i connected my external hard drive to see if it would boot off of that in case my harddrive was bad.
nothing

next i removed the cmos battery and left it out for about 5 minutes
no resolution

im really worried something is bad. anyone able to help me?

---

### Post by KuroYoma on 2009-02-15
What version of ubuntu were you using.  Tell me what you can remember about you computer(specs).  Have you tried anything else?  Open the side panel and unhook your cd-rom and your internel HD.  Then reboot and see if it stays black.  If it does.  Take the cmos battery out again and leave it out longer even try to boot without the cmos battery inserted.  If no availe then leave the cmos battery out over night.

---

### Post by PatrickMoore on 2009-02-15
> **KuroYoma said:**
> What version of ubuntu were you using.  Tell me what you can remember about you computer(specs).  Have you tried anything else?  Open the side panel and unhook your cd-rom and your internel HD.  Then reboot and see if it stays black.  If it does.  Take the cmos battery out again and leave it out longer even try to boot without the cmos battery inserted.  If no availe then leave the cmos battery out over night.

intrepid. my specs include
hp pavillion dv6109om
amd 64 processor @2. ghz
broadcom chipset
nvidia graphics
2.0 gigs of ram

---

### Post by PatrickMoore on 2009-02-15
> **PatrickMoore said:**
> intrepid. my specs include
hp pavillion dv6109om
amd 64 processor @2. ghz
broadcom chipset
nvidia graphics
2.0 gigs of ram

i have a notebook pc so im unsure on how to unhook dvdrom

---

### Post by KuroYoma on 2009-02-15
Ok.  Remove battery and hd.  Then boot up and see what happens.  If nothing and it is still the same reboot once more and then leave off till tomarrow with cmos and hd removed.  Also remove Ubuntu CD if it is still inserted before you try to boot up again.  If you can't get it to open there should be a needle sized hole on the side of the dvd rom.  use a pin to push in and open dvd rom.  after trying these please post back to let me know whats going on.  I have a hp pavilion at my shop.  I will see if I can duplicate this.

---

### Post by Qjet on 2009-02-15
A pavillion? Have a look on the underside of that bad boy next to the DVD case. I know mine came with an alternate for swaping out the burner with a plastic place holder. I haven't needed to swap it out but i think there is a rather large ... i guess you would call it a latch... it only gives you like half a centimeter of give? That's the release latch you use once you have the screws out in the drive to remove it from the laptop

Though i'm quiet curious as to why you would need to remove it. Could a bios fail simply because of the existence of a drive? Actually this all kinda smacks of hardware failure.

that's only a guess though.

---

### Post by PatrickMoore on 2009-02-15
> **KuroYoma said:**
> Ok.  Remove battery and hd.  Then boot up and see what happens.  If nothing and it is still the same reboot once more and then leave off till tomarrow with cmos and hd removed.  Also remove Ubuntu CD if it is still inserted before you try to boot up again.  If you can't get it to open there should be a needle sized hole on the side of the dvd rom.  use a pin to push in and open dvd rom.  after trying these please post back to let me know whats going on.  I have a hp pavilion at my shop.  I will see if I can duplicate this.

nothing happened same nonsense. i have the hdd removed and the batteries both the power supply and the and just have it sitting. i think it may be my bios. this happened before and i let it sit for about 15 minutes and it worked but i did not remove the battery i just reseated the hdd

---

### Post by KuroYoma on 2009-02-15
Correct that why I am trying to get as much hardware removed so we can pinpoint the problem wheather it be worse case and the motherboard is shot or it could be something smaller.  Like the dvd rom is not loading past the POST step of boot up so the laptop would not load the bios because the happens after POST.  Same if its the HD.

PatrickMoore: Ok.  If you have prior knowledge then definetly try that.  What ever is best.  If it is just the bios then we need the ROM to take over and load the original bios. If it is a hardware conflict that is stopping POST then we need to find out what piece of hardware is causing it.

---

### Post by PatrickMoore on 2009-02-15
> **KuroYoma said:**
> Correct that why I am trying to get as much hardware removed so we can pinpoint the problem wheather it be worse case and the motherboard is shot or it could be something smaller.  Like the dvd rom is not loading past the POST step of boot up so the laptop would not load the bios because the happens after POST.  Same if its the HD.

PatrickMoore: Ok.  If you have prior knowledge then definetly try that.  What ever is best.  If it is just the bios then we need the ROM to take over and load the original bios. If it is a hardware conflict that is stopping POST then we need to find out what piece of hardware is causing it.

ok. let me try to unhook my dvdrom im going to look it up.
to be honest a dvd rom replacement is alot more economical than replacing an entire computer

---

### Post by PatrickMoore on 2009-02-15
ok so at this point my dvd rom is removed and i started with nothing connected. nothing happened. reconneced my cmod and hdd nothing.

---

### Post by Victormd on 2009-02-15
Trying to follow the post and from what I understood, the BIOS screen doesn't even show up? Is that right? If that's the case, you might be looking into something a little bigger than your DVD and HD drives. Normally, there is a jumper to reset the BIOS instead of (or along with) removing the battery. I'm not sure how that works with the laptop but you might want to check that as well.
Do you get any beeps/light flashing or anything when you turn it on?

---

### Post by PatrickMoore on 2009-02-15
> **Victormd said:**
> Trying to follow the post and from what I understood, the BIOS screen doesn't even show up? Is that right? If that's the case, you might be looking into something a little bigger than your DVD and HD drives. Normally, there is a jumper to reset the BIOS instead of (or along with) removing the battery. I'm not sure how that works with the laptop but you might want to check that as well.
Do you get any beeps/light flashing or anything when you turn it on?

no beeps. my dvd rom is running i can hear tha. but there is no dvd in it any more. my hdd light flashes momentarily.i didnt see a jumper. and based of the repair info i found there was just the option to remove the battery

---

### Post by PatrickMoore on 2009-02-15
> **PatrickMoore said:**
> no beeps. my dvd rom is running i can hear tha. but there is no dvd in it any more. my hdd light flashes momentarily.i didnt see a jumper. and based of the repair info i found there was just the option to remove the battery

and my external hd will run but of course turns off when my computer restarts automatically and kicks right back on

---

### Post by Victormd on 2009-02-15
and do you get anything on the screen (as far as BIOS info goes)? Does it detect the HD/DVD, memory count, things like that?

---

### Post by PatrickMoore on 2009-02-15
> **Victormd said:**
> and do you get anything on the screen (as far as BIOS info goes)? Does it detect the HD/DVD, memory count, things like that?

nothing, just completely blank

---

### Post by Victormd on 2009-02-15
I think this might be a bigger issue than just DVD/HD because you're not getting any informative beeps during boot. Normally you'll get a series of beeps that indicate what the problem might be... you may want to start striping your laptop down, i.e., remove memory and boot to see if it notices you have no memory, remove graphics card, and things like that. If you still don't get any beeps, then it most likely will be your motherboard...

---

### Post by PatrickMoore on 2009-02-15
> **Victormd said:**
> I think this might be a bigger issue than just DVD/HD because you're not getting any informative beeps during boot. Normally you'll get a series of beeps that indicate what the problem might be... you may want to start striping your laptop down, i.e., remove memory and boot to see if it notices you have no memory, remove graphics card, and things like that. If you still don't get any beeps, then it most likely will be your motherboard...


but this happened before + last time i played with it and managed to fix it. so im hoping this is temporary. other than that im trying to figure if it is more reasonable to replace the motherboard or just by a new laptop

---

### Post by Victormd on 2009-02-15
> **PatrickMoore said:**
> but this happened before + last time i played with it and managed to fix it. so im hoping this is temporary. other than that im trying to figure if it is more reasonable to replace the motherboard or just by a new laptop

I would say contact HP support and see what they have to say about it. It might be something very simple, or not + they can fill you in on the replacement costs...
sorry I couldn't be more help...

---

### Post by PatrickMoore on 2009-02-21
> **Victormd said:**
> I would say contact HP support and see what they have to say about it. It might be something very simple, or not + they can fill you in on the replacement costs...
sorry I couldn't be more help...

is ok thank you amyways. i concluded that the motherboard is junk. but hey at least im not struggling to get a new computer. perfect timing i'd say

---

### Post by stalkingwolf on 2009-02-21
given the lack of beeps and other indicators I think I would try
plugging in an external display.  You might just get lucky and it be the display that has quit.

---

