---
title: "does linux use less power?"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by comp3820 on 2010-03-24
My sister has a Dell Inspiron 1100 that has overheating issues. It seems to be a common problem for that laptop. 
Currently she's using books to keep the laptop elevated so there is more airflow. I've checked the thermal paste and cleaned the fans, but the problem is still there.

I was just wondering if, in general, linux uses less power (=less heat) than Windows XP Home.

---

### Post by crlang13 on 2010-03-24
I've heard varied things depending on the make and model of the computer.  I get better battery life on my MSI netbook through Ubuntu than Windows, but it really depends.

If you are having trouble with overheating, I think there is a tutorial thread somewhere on this forum on getting your ubuntu machine to undervolt.  That may help.

---

### Post by ubudog on 2010-03-24
It depends.  If you are running a program that takes up a lot of energy, then you will have bad battery life.

---

### Post by Marlonsm on 2010-03-24
The Windows that comes pre-installed already have some optimizations for that hardware, so it's likely to be easier on power than an out-of-the-box Ubuntu.
But if you fine-tune Ubuntu, you can get to to use very little power.

Also, maybe there is something else causing the overheat, have you tried speeding up the fas to see what happens, I know it's not an ideal solution, tho, mine gets very noisy the few times it needs to speed up the fans.

---

### Post by admiralspark on 2010-03-24
I have a single 2.0GHz core laptop that originally came with Windows XP Home.
With Windows, it would overheat if you played ANY game (or did anything requiring it to run at the full 2.0).
With Ubuntu, I can adjust the clock speed with a click and a few keystrokes, I have better battery usage management and have cooler core temps. Most Linux applications (along with the OS itself) are lighter weight than the Microsoft-related products they replaced. My battery life has increased nearly twofold (with some slick powersaving modes) and core heat never goes above 70 Celsius at full use (running game/internet/email client/IMer).

---

### Post by ubudog on 2010-03-24
> **admiralspark said:**
> I have a single 2.0GHz core laptop that originally came with Windows XP Home.
With Windows, it would overheat if you played ANY game (or did anything requiring it to run at the full 2.0).
With Ubuntu, I can adjust the clock speed with a click and a few keystrokes, I have better battery usage management and have cooler core temps. Most Linux applications (along with the OS itself) are lighter weight than the Microsoft-related products they replaced. My battery life has increased nearly twofold (with some slick powersaving modes) and core heat never goes above 70 Celsius at full use (running game/internet/email client/IMer).

Me too.  In Windows, whenever I ran a graphic intense game, it would overheat and the laptop would suddenly shut off.  That never happens now.

---

### Post by NightwishFan on 2010-03-24
I think power management is supposed to get a big overhaul by 10.10.

---

### Post by daveritah on 2010-03-24
I have a Dell 1501 running with AMD 64 processor. I had overheat problems and my mouse would go crazy and start doing strange things. My solution cost me about $30.00. I bought one of those cooling pads that ties into an unused usb port. Here in TN (U.S.A.), I picked mine up at a Walmart. Problem solved and no more over-heat issues.

---

### Post by _h_ on 2010-03-24
My battery which only has a 40% total capacity from when I first got it with my laptop, only got around 35 minutes running under Windows 7 with power saver settings and max dimmed lighting and LED lights turned off.

On Lucid now, I am getting about an hour and 20-30 minutes from my battery.

---

### Post by Mark Phelps on 2010-03-25
While I would agree, from personal experience, that Linux apps tend to demand less resources than MS apps, and consequently, using less CPU allows it to run cooler, I would not go so far as to say that installing any Linux distro will solve your overheating problem.

In fact, given the number of posts we've seen from folks complaining that their machines have STARTED to overheat only since installing 9.10, it could actually make your situation worse.

Unfortunately, while a LiveCD will allow you to test drive Ubuntu, since you're constantly waiting on CD activities, you won't get a real feel for CPU usage.  The only way to do this would be to do an actual install.

Also, Dells have a nasty habit of coming preconfigured with 4 primary partitions on the drive, making it then very difficult to repartition the drive for a traditional dual-boot install.

To try out Ubuntu, while I normally avoid Wubi installs, this might be you best bet just to see if it works and helps with the overheating problem.

---

### Post by 3rdalbum on 2010-03-25
Some posters have said that they get more battery life. I get less life with Ubuntu than I did with Linpus Lite, and I think my Ubuntu battery life was on a par with Windows XP.

Ubuntu 10.10 does seem to be a little more power efficient than earlier versions, so my best advice is to try it.

---

### Post by Drenriza on 2010-03-25
Why dont you under-clock your system to avoid heat issues?

---

### Post by Roger Allott on 2010-03-25
> **NightwishFan said:**
> I think power management is supposed to get a big overhaul by 10.10.

So it's a thousand years overdue???

---

### Post by sylaryn on 2010-03-25
I have a Thinkpad that was running Vista on it and, like others, whenever I played a game it would overheat and shut off... the solution for me was to use the power management to configure the CPU (using SpeedStep) to only use 50% of the CPU during gaming.

The Thinkpad came with a power management utility that allowed that level of configuration. I don't know if other laptops have such utils. There are 3rd-party programs (some freeware) that you can find to control fan speed and CPU usage.

The problem with under-clocking is that you can't switch to full CPU on the fly whenever you want. On my Thinkpad I had a "Gaming" power management profile created which I would switch to when needed, and then switch back to "Maximum Performance" when done.

Good luck with your issue.

---

