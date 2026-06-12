---
title: "under/over clocking and under volting"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by dan0804smith on 2011-07-26
can anyone point me in the direction of a place when i can leanr to under and over clock my dell mini 10v.  i would also like to learnhow to undervolt my computer so that the battery last longer.  anybody no any good guides?

OS: ubuntu 8.04?

---

### Post by Matt__ on 2011-07-26
guide to undervolting here; [https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)

[overclock intel gfx]("http://www.gmabooster.com/home.htm") 

you can probably clock the cpu using the fsb setting in bios (not on my mini at the moment so I dont know what bios settings there are)

on the down side, _you will fry your netbook pretty damn quick_..as the 10v has NO FANS

10.04/10.10 work really well on the 10v too by the way.

---

### Post by Brushstroke on 2011-07-26
Never, ever attempt to overclock a laptop/netbook. Period.

That is all.

---

### Post by pommie on 2011-07-26
> **Brushstroke said:**
> Never, ever attempt to overclock a laptop/netbook. Period.

That is all.
Pretty strong statement there, if they want to take the risk and over-clock what give you the right to say they can't.

That said I would be very wary of over-clocking a laptop, but if you want to take the risk, have fun :P

If you under-clock it reducing the voltage wont gain much, if any, battery life as the cpu consumes a certain wattage, so when under-clocked it will use less amps, reduce the volts and the amps will increase to get the same watts.

Cheers David ... who has over-clocked every computer he's had since, and including, his Amiga, but no laptops.

---

### Post by 3rdalbum on 2011-07-26
To change the clock speed, you need to turn off CPU speed scaling. Underclocking will cause the CPU to run at your nominated speed and not go into a sleep state; you'll probably find that with underclocking alone your battery will last a shorter amount of time.

You could try undervolting as well, which reduces the amount of electricity that goes to the CPU, but honestly these CPUs today are already designed to eke out as much performance with as little power as possible. If you underclock and undervolt the CPU it won't be able to be in sleep state for as long, because it will be working for longer (because it's less powerful).

In short: Play with it if you want, but be careful, there might not be any safety features to get back to the factory settings if you undervolt too far. And don't expect to get any noticeable extra battery life. You might, but it's not too likely.

---

