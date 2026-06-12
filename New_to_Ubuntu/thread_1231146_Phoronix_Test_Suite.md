---
title: "Phoronix Test Suite"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by swong on 2009-08-04
The Phoronix Test Suite has so many built-in tests, just wondering if there is a single test or a small number of tests I can use to test the stability of the cpu when overclocking.

---

### Post by wizard10000 on 2009-08-04
> **swong said:**
> The Phoronix Test Suite has so many built-in tests, just wondering if there is a single test or a small number of tests I can use to test the stability of the cpu when overclocking.

Tellya what I use.

Got a Core i7 920 overclocked to 3.5GHz on air using stock voltage and a big Zalman 9900 heatsink and fan.  I use the SMP version of folding@home to stress test a machine - linkage here:

[http://folding.stanford.edu/English/LinSMPGuide](http://folding.stanford.edu/English/LinSMPGuide)

I had to install the latest lm-sensors from source but once I got all the thermal indicators running and started folding@home I had eight threads kicking the crap out of this processor.  Even at the stock 2.66GHz with a stock heatsink and fan the i7 started throttling back once the temperature reached 80 degrees (yeah, that's hot).  With the Zalman fan installed, the machine overclocked to 3.5GHz and eight threads of folding@home running highest temp I ever saw was 75 degrees and the machine idles at 45 give or take.

Hope this helps -

---

### Post by swong on 2009-08-04
Thanks, I will check it out.

---

### Post by swong on 2009-08-05
I did some experimenting in PTS, there is a test called "StressCPU2", it can load all cores at 100% for up to 12 hrs.

---

