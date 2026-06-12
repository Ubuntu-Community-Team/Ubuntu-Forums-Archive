---
title: "Ubuntu Crashes"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by bhappyharsha on 2010-06-24
Hi,

I've installed Ubuntu 10.04 as a dual boot with Windows XP SP3. After i installed it, randomly, ubuntu crashes to a wierd screen with part of the screen filled with some colors appearing randomnly.

I am not a programmer and do not know what to do about this. It does not happen after a particular pattern.. i just login and browse internet. Thats it. The browser window suddenly disappears and shows up this flickering screen. 

The only way is to restart my computer. I've not done any troubleshooting.. 

please help.....

---

### Post by VH-BIL on 2010-06-24
Sounds like a driver issue or a hardware problem.

---

### Post by bhappyharsha on 2010-06-28
> **VH-BIL said:**
> Sounds like a driver issue or a hardware problem.
 
Thanks for the reply. Quite possible. My computer is about 7 years old. I have an Intel 845GVAD chipset with Pentium IV (2.4 GHz) processor and 1.5 GB RAM. I also have an ethernet card and a 4.1 channel creative sound card. I have 2 USB ports and one of them has a USB cable connected it. 
 
Is there any way to find out which hardware/driver is causing an issue? 
 
Regards,
Sri Harsha Kiran.P
 
:guitar:

---

### Post by DrMelon on 2010-06-28
The usual lifetime of a computer is about 6 years (at least in my experience) so I'm not very surprised it's starting to become unstable.

---

### Post by nothingspecial on 2010-06-28
You could do with checking your logs

Next time ubuntu crashes, press ctrl alt F1 to see if you can run it from the console

Type ```
cd /var/log
```

Then type ```
ls
``` to view all the logs. You can view individual files with the less command. For example

```
 less Xorg.0.log
```

Hunt around for any errors.

---

