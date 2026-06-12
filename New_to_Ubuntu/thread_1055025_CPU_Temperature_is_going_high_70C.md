---
title: "CPU Temperature is going high 70C"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Black_agent on 2009-01-30
I used XP but decided to work with Ubuntu and after that I installed ubuntu...

But then my CPU temperature is going high something like 70 degrees.And I think it's not good so I changed motherboard and CPU fan.But I still get 70 degrees.

I really need help with that.I am very sad about this because I have lots of works to do...but have no way to do in this way....:(:(:(:(

Please help me....

Thanks! 

PS-My casing is now opened...So there is no way to increase system temperature.Is there a way to increase fan speed in ubuntu?:)

---

### Post by Paqman on 2009-01-30
How are you monitoring the CPU temp? In the BIOS or in Ubuntu (lm-sensors?)

70deg C is very hot if it's correct. With the side of the case off you should be able to see if your fan(s) are running correctly. The BIOS should also give your their RPMs to make sure they're running at a good speed.

---

### Post by buffy^ on 2009-01-30
It could be just conincidence that the CPU is now overheating. I had a problem with my CPU over heating when I had the heat sink on the wrong way round (it has a shaped contact area). Also purchasing a new cooler can be inexpensive and easy to fit and a big bounus on performance if your CPU has been underclocking to preveing heat problems in windows.

---

### Post by Black_agent on 2009-01-30
> **Paqman said:**
> How are you monitoring the CPU temp? In the BIOS or in Ubuntu (lm-sensors?)

70deg C is very hot if it's correct. With the side of the case off you should be able to see if your fan(s) are running correctly. The BIOS should also give your their RPMs to make sure they're running at a good speed.


I monitored by BIOS and it says my fan is 2250RPMS and I think it is enough.And fans are running correctly.:(:(:(:(

---

### Post by Black_agent on 2009-01-30
> **buffy^ said:**
> It could be just conincidence that the CPU is now overheating. I had a problem with my CPU over heating when I had the heat sink on the wrong way round (it has a shaped contact area). Also purchasing a new cooler can be inexpensive and easy to fit and a big bounus on performance if your CPU has been underclocking to preveing heat problems in windows.

Yeah I purchased new cooler system but problem is not have end.

---

### Post by buffy^ on 2009-01-30
That is most odd.

When you put your had in the case can you feel the heat, it could be your mobo is not correctly reporting the temp. Also when you installed the new heat sink what thermal grease did you use if any?
could I ask what cooling soloution you bought?

---

### Post by Black_agent on 2009-01-30
> **buffy^ said:**
> That is most odd.

When you put your had in the case can you feel the heat, it could be your mobo is not correctly reporting the temp. Also when you installed the new heat sink what thermal grease did you use if any?
could I ask what cooling soloution you bought?

Yeah..I used thermal grease and my cooling solution is  CPU Heat Sink Cooling system(Not water cooling system)

And I think maybe it will work well if I reinstall cooling fan system....But what are other suggestions...

Do my CPU overlocking?

---

### Post by buffy^ on 2009-01-30
Do you know which model you have for example I have a 
[http://www.zalman.co.kr/ENG/product/Product_Read.asp?idx=277](http://www.zalman.co.kr/ENG/product/Product_Read.asp?idx=277)

Which is designed to work with my AMD 9850 CPU

I just want to make sure you have the right setup. Sorry if these questions are not helping, I am just trying to understand what we are working with.

Thanks

---

### Post by Paqman on 2009-01-30
> **Black_agent said:**
> ....But what are other suggestions...



You could try updating your BIOS. If could be either not controlling the fans properly or not reporting the temp correctly.

> Do my CPU overlocking?

Sorry, I don't quite understand what you mean. But if you have overclocked the CPU, reset it to normal now.

Rest assured, if you're getting these readings from the BIOS, it's nothing to do with Linux. Your problem is either BIOS or hardware.

---

### Post by Malta paul on 2009-01-30
For info. my CPU fan runs at 2766 rpm maximum speed.
Have you tried carrying out a 'memory Check' at boot up? I have over- clocked my system and I had to reduce some voltages in my BIOS when the 'mem chk failed! This has reduced my CPU temperature and it now checks out OK. My system now runs fine :D

---

### Post by LowSky on 2009-01-30
70'C should invoke the BIOS to shutdown the PC, as that is way too hot to be running. Linux in general should not casue such things to happen 

2250RPMS isn't that fast, my 120mm fans run at that speed and its rather slow, 80mm fans should be closer to 3000rpm

Also overclocking the voltage or the processor in general too high can lead to high temperatures. Some chips handle temperatures rather well and some are horrible (like the old Intel P4s were known for high temps)

---

### Post by skuntbehavior on 2009-01-30
Check the basics first. 

- fan on heatsink spinning? how is that fan powered? by the motherboard power header or via 4 pin molex directly to the power supply?

I have installed dozens of heatsink / fan combinations in my time, you should ALWAYS power your fan directly connected to your power supply.

- in my opinion, bios information (as it relates to fan speed and temps) can be off. download a free utility like Sisoft Sandra or something along those lines to check and monitor idle / ambient air temps in your case. 

- can you include a pic somehow of the case make and model?
- how many fans do you currently have installed.

---

### Post by Paqman on 2009-01-30
> **skuntbehavior said:**
> 
I have installed dozens of heatsink / fan combinations in my time, you should ALWAYS power your fan directly connected to your power supply.


Er, if you do that, you won't get any PWM of the fan, surely?

Regarding fan speed, I have a similar Zalman CPU fan and it runs around 1500RPM, so 2000+ seems consistent with very high CPU temp.

---

