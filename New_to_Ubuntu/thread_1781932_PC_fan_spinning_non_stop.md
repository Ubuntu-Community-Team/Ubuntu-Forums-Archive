---
title: "PC fan spinning non stop"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Amagaeru on 2011-06-14
I have a Packard Bell EasyNote F0336-095.
When I am using this machine in WindowsXP, however, fans works normally.

I'd appreciate it if you could give me a hand.:'(

*Sorry,My English skills are sucks.

---

### Post by grahammechanical on 2011-06-14
Hi, Welcome to the forum. You say:

> My English skills are sucks.You are right. It is better to say "My English skills suck." The verb is "suck." You do not need "are." I hope that you do not mind me saying this.

I have a good ability at reading English but I cannot find anywhere in that sysinfo.txt document that mentions the fan speed. I see this:

> GenuineIntel, Intel(R) Celeron(R) M CPU        520  @ 1.60GHzand this:

> CPU clock currently at 1599.807 MHz with 1024 KB cacheThis is the internal speed or clock speed of the CPU. It is my guess that 1599.807 Mhz (mega hertz or cycles per second) is a speed a little less than 1.66Ghz (giga hertz or cycles per second). It tells you how fast the CPU is able to process instructions.

I have installed a utility called xsensors. It tells me my CPU temperature and my motherboard temperature and also the chassis (case) fan speed for the two case fans. It also tells me the CPU fan speed which is 948 RPM (revolutions per minute}. This speed will increase as the CPU does more work and as the temperature of the case rises.

All my fans are spinning non-stop. This is correct. If any of these fans stopped working then the computer would overheat and some components would be damaged.

May I suggest that you install the xsensors utility. It is in the Ubuntu Software Centre. Search for xsensors and the software will centre will install it for you. Do you have a utility in Windows to tell you the speed of the fans. If so you can compare the results and this will tell you if the machine is working hotter in Ubuntu than in Windows.

It is good to be able to speak any language in the correct way. It is better to be able to communicate with people who speak different languages. It does not matter if we speak another person's language incorrectly. Can we understand each other? Do we respect each other? Can we laugh together? These is the important matters.

Regards.

---

### Post by 3rdalbum on 2011-06-14
There are two things to check:

1. Something might be using up all the CPU capacity on Ubuntu, which normally shouldn't happen, but would cause the fans to spin at high speed constantly. Look in the System Monitor to see if any programs are using nearly 100% CPU.

2. Your BIOS should be able to control the speed of your fans, but some computer manufacturers turn off the BIOS' fan speed control and instead install software on Windows to control the fans. Try looking in your BIOS setup and see if fan speed control is enabled.

---

### Post by collisionystm on 2011-06-14
Install HTOP and run it in terminal. You can watch your CPU's and see if they  are maxxing out causing the fan to run.

```
sudo apt-get install htop
```

open terminal

```
htop
```

---

### Post by Amagaeru on 2011-06-14
Thank you for your advice. Well,I see. I study English more and more and more harder.(I've been studying English for 4 months.It begins to study English in the first grade of junior high-school in Japan. Studying English is really hard for we the Japanese)


It's return for the main topic.

I installed xsensors and command from terminal;
xsensors

xsensor says
tab:coretemp Temperatures
Core0:24.0 &#8451;/ *degrees

Only this,,,

---

### Post by Amagaeru on 2011-06-14
> **3rdalbum said:**
> There are two things to check:

1. Something might be using up all the CPU capacity on Ubuntu, which normally shouldn't happen, but would cause the fans to spin at high speed constantly. Look in the System Monitor to see if any programs are using nearly 100% CPU.

2. Your BIOS should be able to control the speed of your fans, but some computer manufacturers turn off the BIOS' fan speed control and instead install software on Windows to control the fans. Try looking in your BIOS setup and see if fan speed control is enabled.

1 is no.
2 is maybe YES. Fan control is unenable.I can't look this in BIOS.

Really thanks.

---

### Post by Amagaeru on 2011-06-14
> **collisionystm said:**
> Install HTOP and run it in terminal. You can watch your CPU's and see if they  are maxxing out causing the fan to run.

```
sudo apt-get install htop
```

open terminal

```
htop
```


I have done it.
Sorry, but Where is items about fan? 

Thank you.

---

### Post by collisionystm on 2011-06-14
Your fans are probably cranking to cool the CPU. So when you run HTOP was is your CPU usage at?

---

### Post by Amagaeru on 2011-06-14
> **collisionystm said:**
> Your fans are probably cranking to cool the CPU. So when you run HTOP was is your CPU usage at?


CPU using is 2.6 to 9.3.

---

