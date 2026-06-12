---
title: "External HDD 2.5&quot; vs 3.5&quot;"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-28
Hi, I'm looking to buy about a dozen external HDDs to install Ubuntu on them and distributing fully ready systems to people in college. Do you guys recommend 2.5" or 3.5" ones?

1.)In my college dorm room experience, people seem to have a lot more failures with the 3.5" drives than they do with 2.5" ones (all drives from name barands like seagate, WD etc). Is this actually true or just down to chance or the fact that the direct power connection of the 3.5" leaves a lot to go wrong when power is interrupted?

2.)The 3.5" tend to produce more heat. But is this even an issue? I remember reading this google study for their massive data centers that sort of concluded that high temperatures showed no direct correlation with risk of failure.

3)The 2.5" ones are more portable without needing an extra power adaptor and wires. So like......why do the (cost? coz they're cheaper?)

4)Could you throw some light on 1.8" ones

Thank you very much

---

### Post by Boondoklife on 2009-05-28
I can't say that there is any advantage other than cost and speed to using any of the three. With a larger drive you tend to get more space and a faster speed than the smaller ones.

With this in mind, unless you are pressed for space I would use the 3.5s but that is just my 2cents.

---

### Post by Andy06 on 2009-05-28
But if a 2.5" is rated at 5400 RPM and so is a 3.5", will it still make that much of a difference? I know the actual I/O and read/write speeds can be a bit different but would it be noticeable.

I just realised that 3.5" enclosures tend to have esata, firewire and nextbigthing interfaces as well whereas 2.5" usually have slow USB ones. Now that WOULD make a difference. However how will this change with USB3.O coming up. Does that catch up with firewire and esata?

---

### Post by Andy06 on 2009-05-28
Oh and does heat make a difference? We all try to keep our HDD temps down but I would imagine Google has many more HDDs running than perhaps everyone on this forum combined. So maybe they are onto something?

---

### Post by TheLions on 2009-05-28
> **Andy06 said:**
> Hi, I'm looking to buy about a dozen external HDDs to install Ubuntu on them and distributing fully ready systems to people in college. Do you guys recommend 2.5" or 3.5" ones?

1.)In my college dorm room experience, people seem to have a lot more failures with the 3.5" drives than they do with 2.5" ones (all drives from name barands like seagate, WD etc). Is this actually true or just down to chance or the fact that the direct power connection of the 3.5" leaves a lot to go wrong when power is interrupted?

2.)The 3.5" tend to produce more heat. But is this even an issue? I remember reading this google study for their massive data centers that sort of concluded that high temperatures showed no direct correlation with risk of failure.

3)The 2.5" ones are more portable without needing an extra power adaptor and wires. So like......why do the (cost? coz they're cheaper?)

4)Could you throw some light on 1.8" ones

Thank you very much

I would say:
2.5: 
lower speed (5400 rpm)
more resistant to movement shocks (like vibration)
less power consumption
smaller
shorten lifetime

3.5
faster (7200rpm)
non resistant to shock and vibration
lifetime ~7 years

> **Andy06 said:**
> Oh and does heat make a difference? We all try to keep our HDD temps down but I would imagine Google has many more HDDs running than perhaps everyone on this forum combined. So maybe they are onto something?

Google have airconditioning, why do you think what comsumes 1,800,000 kW/h (~ 7000 households)?

And about HDD temp, all above 60° is hazardous

---

### Post by Boondoklife on 2009-05-28
I would not go by the RPM to define data xfer, you need to look into the actual transfer rates.

---

### Post by Paqman on 2009-05-28
> **Andy06 said:**
> Hi, I'm looking to buy about a dozen external HDDs to install Ubuntu on them and distributing fully ready systems to people in college. 

What about 8GB or 16GB memory sticks with it preinstalled?

What's the target audience for this? You trying to run it as a business?

---

### Post by networkproblems on 2009-05-28
I've owned two 3.5" Western Digital usb drives for nearly four years, and they haven't gone bad on me.

The heat on the 3.5" ones shouldn't matter unless it just bothers you or you are constantly reading/writing to it. My 250 GB MyBook and most other newer ones turn off the disk after about 15 minutes of inactivity, so heat is not a big issue.

Speed is not an issue since both read and write faster than USB can transfer.

2.5 inchers are more portable since most don't need to be plugged into an outlet and just run off of USB.

The only real issue is price; 2.5's are much more expensive than 3.5's.

---

### Post by LowSky on 2009-05-28
2.5 drives can run on USB power. 3.5 requires a outlet.

2.5 drives are made for laptops and usually have better g-force tolerance

3.5 drive are built for desktops and servers they will have higher capacities but they cant take as many hits/drops.

2.5 drives are availible at 7200RPM

3.5 drive can be purchased with 10,000RPM (see WD Rapter)

Also the smaller the device the more expensive... that is how technology works.

---

### Post by callan79 on 2009-05-28
> **Andy06 said:**
> Hi, I'm looking to buy about a dozen external HDDs to install Ubuntu on them and distributing fully ready systems to people in college. Do you guys recommend 2.5" or 3.5" ones?


Hi Andy06,

Have you considered providing the system software on a USB stick instead - which makes it perhaps cheaper, and more portable?

Then if you/they want additional storage, they could just get their own external USB hard drive, or a network hard drive, or a USB stick ....

I've tried running Ubuntu off a USB stick and provided you're using USB 2.0, it's quite fast!

Also then you won't have any heat or vibration issues to worry about.

Cheers
Callan

---

### Post by Andy06 on 2009-05-29
Thanks all for the great help, all questions comprehensively answered.

Some follow ups:

@TheLions:

> I would say:
2.5:
lower speed (5400 rpm)
more resistant to movement shocks (like vibration)
less power consumption
smaller
shorten lifetime

3.5
faster (7200rpm)
non resistant to shock and vibration
lifetime ~7 years

Thanks for that. We always noticed 3.5" being more fragile and crashing faster, now I know it's because of careless student-like handling.

> And about HDD temp, all above 60° is hazardous 

:eek: What about in and around 60 (how do you make a degree sign??). My personal laptop is a HP dv6000 series and the HDD is always around high 50s.

> What about 8GB or 16GB memory sticks with it preinstalled?

What's the target audience for this? You trying to run it as a business? 

We initially gave out 2 GB memory sticks with customised live systems installed (Wallpaper changed, theme/icons/pointer changed, apps and codecs loaded, complete out of box functionality).

Unfortunately, doing a FULL install on memory sticks doesn't give enough useful life, we burn through them very fast, especially if the swap file is on the memory stick itself.

Not a business, wouldn't wanna make money of linux:D
Uni society, goal is to start propagating linux in college dorms.

> Speed is not an issue since both read and write faster than USB can transfer. 

What happens when USB3.0 becomes available? What about esata and firewire. Is the interface always the bottleneck.

> Have you considered providing the system software on a USB stick instead - which makes it perhaps cheaper, and more portable?

Yep. That's the preferred solution to get the feet wet. But unfortunately its not a good long term solution since full blown installs drastically shorten the lives of the USB sticks.
They can only take about 10K-100K read/write cycles and with a swap file on them and apps writing and reading from cache and tmp files, it dies pretty quickly.

Thank you all once again

---

### Post by TheLions on 2009-05-29
> **Andy06 said:**
> 
@TheLions:
:eek: What about in and around 60 (how do you make a degree sign??). My personal laptop is a HP dv6000 series and the HDD is always around high 50s.


degree sign '°' is AltGr+5 (on my Croatian keyboard)

and about your hdd check your product manual there should be exact operating temperature which is safe. if temp is above that limit you should give a call to HP support/service.

(you can findot which hdd you have by installing this program: [apt:sysinfo]("apt:sysinfo"))

---

### Post by binbash on 2009-05-29
3.5 is louder, needs external power, it is heavy and so on.

---

### Post by freeman2000 on 2009-05-31
If you're in the USA, Costco has the Western Digital Passport Elite 500gb (2.5") portable on sale for $100.   It comes with a carrying case, USB cable, and software (Mac & Windows), and runs on USB 2.0 which means it has a transfer rate of 480 mb/s.  Sleek, quiet & fast.  It has a 5yr warranty.  I'm real happy with mine - no problems using it in Ubuntu.  Good luck.

---

### Post by Andy06 on 2009-05-31
When is USB3.0 coming out anyway? Will it come out for desktops first and will there be a lag before we see it on notebooks and other devices and peripherals (like there was for Core i7)?

Should I just wait for USB3.0 before I make any purchases of big drives for myself?

---

### Post by TheLions on 2009-05-31
> **freeman2000 said:**
> If you're in the USA, Costco has the Western Digital Passport Elite 500gb (2.5") portable on sale for $100.   It comes with a carrying case, USB cable, and software (Mac & Windows), and runs on USB 2.0 which means it has a transfer rate of 480 mb/s.  Sleek, quiet & fast.  It has a 5yr warranty.  I'm real happy with mine - no problems using it in Ubuntu.  Good luck.


USB 2.0 has theoretical transfer rate of 480 mb/s (60MB/s) and e-sata has 3Gb/s (375MB/s) but still my 1TB drive has same transfer rate (~50MB/s) on both buses.

@Andy06

don't wait for USB 3.0, rather wait for bigger and cheaper SSD HDDs.

---

