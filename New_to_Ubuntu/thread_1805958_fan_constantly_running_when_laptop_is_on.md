---
title: "fan constantly running when laptop is on"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by philosophking on 2011-07-16
Hi everyone,

I'm new to the forums here. I have a Sony Vaio VGN SR210J running Ubuntu 10.04 (LTS). Really enjoying the setup, customizability, and great software!!

The problem: my fan is running all the time when it's on -- even if it's idle (blank screensaver is on, or I'm not doing anything on the laptop). I realize that's not necessarily a problem, but it does seem abnormal (based on my previous experience running Windows on it). Searching around on the forums didn't give me any good ideas.

By the way, relatedly, I'd be interested in any programs you can suggest on monitoring computer temperatures.

I know how to get around using the terminal, so let me know if there's something you'd like me to post to give you a better idea of the problem.

And, thanks for any help you can offer!

---

### Post by thomas144 on 2011-07-16
Yes. I'm not sure how to fix your main problem, but to check the temperature of your pc, run:
```
sensors
```
If you live in the US or otherwise use Fahrenheit, use:
```
sensors -f
```
to convert the units if Celsius isn't to your liking. I hope this helps you investigate.

---

### Post by philosophking on 2011-07-16
thanks for that command line! it's saying 42C which i guess is fine. just wondering if there actually IS something wrong since the fan seems to be running more than it ever did using windows. 

then again, windows is inefficient for a lot of reasons so maybe this is not "abnormal" :)

finally, i've heard vaio pc's can have unusually loud fans, so that could be the issue too 

thanks... anymore advice?

---

### Post by wildmanne39 on 2011-07-17
> **philosophking said:**
> thanks for that command line! it's saying 42C which i guess is fine. just wondering if there actually IS something wrong since the fan seems to be running more than it ever did using windows. 

then again, windows is inefficient for a lot of reasons so maybe this is not "abnormal" :)

finally, i've heard vaio pc's can have unusually loud fans, so that could be the issue too 

thanks... anymore advice?Hi, here is a link on how to control fan speed.
[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu).

---

### Post by HermanAB on 2011-07-17
Howdy,

Laptops may have weird hardware and the fan control is a frequent problem, so don't be too surprised if you cannot find any functional way to control the fan speed.

When all else fails, solder a 200 ohm, 1/4 Watt resistor in series with the fan to reduce the noise.

---

### Post by amjjawad on 2011-07-17
> **philosophking said:**
> Hi everyone,

I'm new to the forums here. I have a Sony Vaio VGN SR210J running Ubuntu 10.04 (LTS). Really enjoying the setup, customizability, and great software!!

The problem: my fan is running all the time when it's on -- even if it's idle (blank screensaver is on, or I'm not doing anything on the laptop). I realize that's not necessarily a problem, but it does seem abnormal (based on my previous experience running Windows on it). Searching around on the forums didn't give me any good ideas.

By the way, relatedly, I'd be interested in any programs you can suggest on monitoring computer temperatures.

I know how to get around using the terminal, so let me know if there's something you'd like me to post to give you a better idea of the problem.

And, thanks for any help you can offer!


Hello and Welcome :)

Sometimes, there are some processes running in the background (which require high CPU usage) and sometimes there is nothing. I think it's normal and I think it could be abnormal if that will last for a long time. Linux is NOT Windows so better not to compare a lot ;)

Your HDD Temp is ok. I agree with Herman. I don't feel much comfortable when I'm using Laptops. Still prefer PCs.

Good luck :)

---

