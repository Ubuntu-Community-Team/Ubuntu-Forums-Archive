---
title: "Temperature Monitor is incorrect"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Just-trevor on 2009-06-23
I'm OC-ing my i7 2.67GHz at 3.1GHz so it seems necessary to have a temperature monitor on my desktop somewhere...

I followed the HOWTO somewhere to install a monitor on a panel, but I'm pretty sure the temperature it is showing is wrong. It normally shows 50 C but when I check it on BIOS it says its 65 C to 85 C. Also it says that the HDD temp and CPU temp are the same which is not likely. The temperature is the same when I run acpi -t.

Others with the same processor comment on newegg that the stock fan is a piece of $H1T, so yeah...

Any guesses as to why the temperature is wrong?

---

### Post by wpshooter on 2009-06-23
Hmmmmmmmm, 65 C to 85 C in the BIOS !!!

I would hope that the temperature being given by Ubuntu are the correct ones.

How old is the motherboard ?  See if there is a BIOS update for your M/B.

---

### Post by LewRockwell on 2009-06-23
what temperature does it run at when you're not OC'ing it

---

### Post by LowSky on 2009-06-23
even 50C is high... and overclocking  with stock cooler is dangerous, its not meant for such things, and maybe your motherboard doesn't support hard drive temp monitoring, so it reporting the only monitor it has.

Run the chip at stock and see the temps then... check your thermal greese is applied properly, buy a real cooler  if you need to over clock... because to me Ocing on OEM parts is like running NO2 on stock Honda Civic

---

### Post by jimv on 2009-06-23
It's spot on.  You need another CPU fan, like something by Artic Cooling or Zalman.

---

### Post by Just-trevor on 2009-06-23
I don't think it was 85 C in bios, rather 65 C and it got messed up in my memory. 72 C was highest

I'm running it at 1.6 GHz though, there is a applet thing for the cpu speed that I have on a panel.

The mobo is less than a month new so I don't think there's a bios update yet...

Using the CPU usage app thing I changed from 1.60 GHz to 2.79 GHz and the temperature went down... that's why I think it's wrong

The thermal compound is on plentifully

I think I'll just get another fan.

---

### Post by LowSky on 2009-06-23
> **Just-trevor said:**
> I don't think it was 85 C in bios, rather 65 C and it got messed up in my memory. 72 C was highest....I'm running it at 1.6 GHz though, there is a applet thing for the cpu speed that I have on a panel....The thermal compound is on plentifully

  

1)65C is hot for processor, 40C or Below is what you should be aiming for. No more than 50C under a full load.

2)Speed stepping as your CPU is doing is common practice for newer chips, its save energy, therefor heat too.

3)Too much thermal grease is a big NO NO! You should have a thin, barely covering layer on the processor, no so much that it pours out the sides when the heatsink is installed. Also a small amount should be worked into the heasink, and by small I mean just enought to fill the unseeable grooves of the heatsink. Basically rub it in until its barely there.

I'm not a fan of pre applied thermal grease/pads that many OEMS and heat sink companies use, your better off cleaning it off and applying it yourself. Doing this can drop temps considerably.

---

### Post by Just-trevor on 2009-06-23
Argh there isn't THAT much on it and I'm too lazy to take my computer apart again to rub a little bit off.
I have some thermal compound left so I'll just get a new fan and save the rest for when the new fan arrives

This wasn't really a thread about colling your CPU though - it was about why the temps were different on the BIOS and panel thing. But whatever

It's not like it's going to implode if it gets over 60 degrees or anything, and if it did that would be awesome

---

### Post by Paqman on 2009-06-23
> **Just-trevor said:**
> 
The mobo is less than a month new so I don't think there's a bios update yet...


Check anyway. It might have been sitting on a shelf in a warehouse for a while. I've had mobos arrive with outdated BIOS on them before.

Obviously, flash your BIOS at your own risk.

---

### Post by Just-trevor on 2009-06-23
There's no BIOS update.

---

### Post by Mark Phelps on 2009-06-24
I didn't catch how you're monitoring your CPU temps in Ubuntu, but the general approach is to install lm-sensors, run sensors-setup, and then run sensors.

When I do that, I get readings from two different chips.  The first chip is always wrong and several degrees to low.  The second chip produces LOTS of temps, and is generally correct.

Also, if you're using conky to display the temps, you may be using the wrong temps for reporting the CPU(s).

---

### Post by Just-trevor on 2009-06-24
Yah that's what I did. Both the chips say the same temp. They might be right, but when I restart and go to BIOS the temperature is significantly different.

If it gets too hot somehow it will just shut down anyway

Another reason I think the gnome panel applet is wrong is because when I run a game, the temperature jumps from 45 C to 71 C in a couple seconds. Not likely - right? If it is right, I'm thinking that's a bit of a problem... a 26 degree temperature increase from running one single game is pretty ludicrous.

---

