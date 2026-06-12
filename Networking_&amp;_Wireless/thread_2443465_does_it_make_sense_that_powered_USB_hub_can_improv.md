---
title: "does it make sense that powered USB hub can improve internal wi-fi?"
date: 2020-05-15
forum: Networking &amp; Wireless
---

### Post by anotherChris on 2020-05-15
I put Lubuntu 20.04 on an Intel Compute Stick, which has a wi-fi connection and a bluetooth connection (I believe they are somehow on a shared internal component), and a single USB 2.0 port.  There is no battery in the Compute Stick, so it remains plugged in to an electrical socket constantly.

The bluetooth stays connected to a small bluetooth audio speaker.  

If I use the single USB port for a wireless keyboard/mouse USB dongle, the Internet wi-fi connection seems to be slow and goes in and out.  However, if I use the single USB port to connect a powered USB hub and then put the keyboard/mouse dongle in the USB hub, the Internet wi-fi connection seems to be fine.  Does that make any sense?

---

### Post by kurt18947 on 2020-05-16
I'm not an expert in such matters but yes, it may make sense. USB ports can supply limited power, 500 milliamps for USB2 comes to mind. USB3 can supply more power. Using a powered hub increases that 500 ma. I don't know if low power would make your wifi connection slow but it seems reasonable. Kind of like an incandescent light bulb on an overloaded circuit, it gets dim.

---

### Post by anotherChris on 2020-05-17
> **kurt18947 said:**
> I'm not an expert in such matters but yes, it may make sense. USB ports can supply limited power, 500 milliamps for USB2 comes to mind. USB3 can supply more power. Using a powered hub increases that 500 ma. I don't know if low power would make your wifi connection slow but it seems reasonable. Kind of like an incandescent light bulb on an overloaded circuit, it gets dim.

On a tiny device like a Compute Stick, could you run into a problem of providing too much power with a powered USB hub?  (I know nothing about electrical engineering.)

---

### Post by kurt18947 on 2020-05-17
I know nothing of electrical engineering either. I've never heard of supplying too many amps to a device causing a problem. The device should accept only what it needs unless there is a design or function failure. Supplying too few amps or volts to a device can cause a problem. This was talked about recently in a thread discussing backups. An experienced poster said a USB mechanical hard drive with external power input will read and write faster than one running off USB port power only.

---

### Post by DuckHook on 2020-05-17
At the risk of sounding like an idiot to a real electrical engineer, my understanding of electricity is that lots of amperage is not a problem, but voltage is. The analogy is to a pipe. Voltage is akin to water pressure. Even a small amount of water at high presure will burst a pipe. OTOH, a lake full of shallow water is safe because it can never achieve the pressure needed to burst the pipe.

Insufficient amperage is a different story. Going back to the water analogy, if a water wheel requires 20 litres of water per second, and all we supply it with is 10, the water wheel will not turn. If we oversupply it with a million litres of water, it will work quite nicely so long as we don't overpressurize the water such that it damages the mechanism.

A compute stick with an insufficient amperage supply will not work or may work suboptimally.

---

### Post by anotherChris on 2020-05-17
Thanks!

---

