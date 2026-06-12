---
title: "Controling CPU fan speed?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-08
How can i speed up or dumb down my CPU fan using Ubuntu?? i am using an NC10 Samsung netbook.

---

### Post by cywhale on 2009-12-19
There's no possibility of changing the fan speed with Linux for the NC10.

Somwhere I read that "silent mode" in XP somehow changes the fan-on/off trip points from ~45° to ~50°, combined with staying at 800Mhz cpu speed this results in longer "silent" time. So it *should* be possible but seemingly nobody was able to find out how... :(

---

### Post by wojox on 2009-12-19
[http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)

---

### Post by joes7 on 2009-12-19
Use Fan Speed Monitor.
[http://www.almico.com/speedfan.php](http://www.almico.com/speedfan.php)

---

### Post by 3rdalbum on 2009-12-19
> **JamesParnell said:**
> How can i speed up or dumb down my CPU fan using Ubuntu?? i am using an NC10 Samsung netbook.

Your computer's BIOS gets fed thermal sensor data every second. While your computer is on and booted, this is all the BIOS does. It's much better than you at controlling fan speeds. It's much better than any human at controlling fan speeds.

Let it do its job, and you won't end off with an extra-crispy CPU.

---

### Post by joes7 on 2009-12-19
> **3rdalbum said:**
> Your computer's BIOS gets fed thermal sensor data every second. While your computer is on and booted, this is all the BIOS does. It's much better than you at controlling fan speeds. It's much better than any human at controlling fan speeds.

Let it do its job, and you won't end off with an extra-crispy CPU.
Do as he says, it is the safest way.

---

### Post by 73ckn797 on 2009-12-19
The fan speed on my desktop (see signature) does speed up and down as system load requires.

I have another desktop computer with 9.10 and the fan stays constantly at full speed. The bios has a fan speed test and it shows a minimum and maximum speed detected. There was a different heat sink and fan that stayed on max speed and the bios test failed for fan speeds. I swapped that one out. I have another fan that I am going to connect to see what happens.

I cannot figure out why one system cycles the fan through speed based on load while the other one does not. Any suggestions?

---

### Post by JamesParnell on 2009-12-22
I tried the way listed here, but nothing much happened...and according to the CPU scaling app, it can only get up to 799mhz....is there a way to break that (effectively OC'ing the CPU)

---

### Post by 3rdalbum on 2009-12-22
> **73ckn797 said:**
> The fan speed on my desktop (see signature) does speed up and down as system load requires.

I have another desktop computer with 9.10 and the fan stays constantly at full speed. The bios has a fan speed test and it shows a minimum and maximum speed detected. There was a different heat sink and fan that stayed on max speed and the bios test failed for fan speeds. I swapped that one out. I have another fan that I am going to connect to see what happens.

I cannot figure out why one system cycles the fan through speed based on load while the other one does not. Any suggestions?

Asus motherboards call it "Q-Fan". When I first built this computer, I didn't know what Q-Fan meant, so I had it switched off.

Have a look at your motherboard manual and see if it's called some weird name in your BIOS.

---

### Post by 73ckn797 on 2009-12-23
> **3rdalbum said:**
> Asus motherboards call it "Q-Fan". When I first built this computer, I didn't know what Q-Fan meant, so I had it switched off.

Have a look at your motherboard manual and see if it's called some weird name in your BIOS.

The computer I speak of with the high fan speed is a Biostar with Phoenix BIOS (both computers have the Phoenix BIOS). They have the "Smart Fan" control. I did install a different CPU fan and it does respond to the BIOS test and only speeds up as system load requires. I tried 3 fans and figure the others were not sending a temp signal. The temp sensors appear OK at the fans.

---

### Post by spud1 on 2010-01-07
I have a problem in 9.04 my computer was doing great but I installed 9.10 now my cpu gets too hot and shuts off....Can someone fixes it for me


Laptop toshiba satellite L505d-s5965: AMD 64b X2  2.1 gig
3gig ram 250HD

Ubuntu 64bit 9.10

---

### Post by 73ckn797 on 2010-01-07
> **spud1 said:**
> I have a problem in 9.04 my computer was doing great but I installed 9.10 now my cpu gets too hot and shuts off....Can someone fixes it for me


Laptop toshiba satellite L505d-s5965: AMD 64b X2  2.1 gig
3gig ram 250HD

Ubuntu 64bit 9.10


If you go to [http://www.uboontu.com](http://www.uboontu.com) you will have a better search tool to look for other solutions given to fix your computer fan operation. It is a better search tool than the forum search feature.

---

