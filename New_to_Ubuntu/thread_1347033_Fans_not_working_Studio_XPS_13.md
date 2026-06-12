---
title: "Fans not working Studio XPS 13"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by bdjohnso on 2009-12-05
I installed 9.10 on a friend's Studio XPS 13 (aka XPS 1340), but I can't get the fans to come on. As such, the laptop overheats and shuts itself down. I've done the standard i8k and gkrellm install, and I think I know what the problem is:

It seems that there is some miscommunication between the laptop sensors and i8k. The CPU temp is being reported as -22 C, and the fan speeds are reported at -22 RPM as well. This values are constant for the entire time the computer is on, so clearly something is wrong. 

I'm still relatively green with Linux, but I can usually solve my problems with the assistance of the Google oracle. Maybe I'm not searching correctly, but I can't find a fix for this problem.

Thoughts?

---

### Post by Temposs on 2009-12-05
I don't know what the problem would be, but if I were in your position, I would try to install another version of Ubuntu on this computer.

---

### Post by The_Pirate_King on 2009-12-05
I have a problem on 9.1 where the fan runs constantly, but your problem sounds much more serious.  However, there are known problems with fan management in 9.1: [http://ubuntuforums.org/archive/index.php/t-330917.html](http://ubuntuforums.org/archive/index.php/t-330917.html)

You could try some of the fixes in there, they might apply to either situation.  I might recommend running Ubuntu in recovery terminal mode while you do that, since it would use less CPU.  ACPI is a great terminal-based program for monitoring your processor temperature. 

I think the best thing to do in this situation, however, might be a clean install, since overheating your computer can cause some serious damage to the hardware.

---

