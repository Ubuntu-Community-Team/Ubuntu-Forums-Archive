---
title: "How to change refresh rate in Ubuntu 10.04.1"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by ffjjkk on 2010-09-04
Hi everyone!
I am a newbie in Ubuntu.

I want to change refresh rate from 60Hz to 75Hz or 85Hz.
I have used Monitor Preferences (System -> Preferences -> Monitors)
but have only one refresh rate option for 1024x768 is 60Hz. 
I think that my monitor can display 1024x768 with 75Hz or 85Hz.
My monitor is Samsung 793DF (17inch CRT, in Monitor Prererences is Unknown monitor status) and VGA card is intel 915GV.

I found some tutorials to change refresh rate is editting Xorg. But in Ubuntu 10.04 it is impossible.

Thanks for reading!
I need your help!

Nice day!

---

### Post by sandyd on 2010-09-04
> **ffjjkk said:**
> Hi everyone!
I am a newbie in Ubuntu.

I want to change refresh rate from 60Hz to 75Hz or 85Hz.
I have used Monitor Preferences (System -> Preferences -> Monitors)
but have only one refresh rate option for 1024x768 is 60Hz. 
I think that my monitor can display 1024x768 with 75Hz or 85Hz.
My monitor is Samsung 793DF (17inch CRT, in Monitor Prererences is Unknown monitor status) and VGA card is intel 915GV.

I found some tutorials to change refresh rate is editting Xorg. But in Ubuntu 10.04 it is impossible.

Thanks for reading!
I need your help!

Nice day!
a) are you sure that your monitor works with a higher refresh rate? Because if it doesn't, your monitor shall explode when you put it to a higher refresh rate (just kidding, but in all seriousness, it will badly damage your monitor)

b) Since Jaunty (or was it karmic?) the xorg configuration has changed. It **should** automatically detect your resolution and refresh rate properly.

However, if your sure about a)...
Then try post #3 of [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1437980](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1437980)

---

### Post by ffjjkk on 2010-09-04
Thanks Carlee

I am sure that my monitor works with a higher refresh rate (in Windows, 85Hz is ok)

I have read the topic (which you sent) yesterday but it is not help me solve my problem.

Thanks!

---

### Post by sandyd on 2010-09-04
> **ffjjkk said:**
> Thanks Carlee

I am sure that my monitor works with a higher refresh rate (in Windows, 85Hz is ok)

I have read the topic (which you sent) yesterday but it is not help me solve my problem.

Thanks!
whats the output of
```

gtf 1024 768 75

```

---

### Post by ffjjkk on 2010-09-04
> # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

Thanks again!

---

### Post by sandyd on 2010-09-04
> **ffjjkk said:**
> Thanks again!
```
xrandr --newmode"1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
xrandr --addmode VGA-0 "1024x768_75.00"
xrandr --output VGA-0 "1024x768_75.00"
```

might have to add sudo in front of the commands

---

### Post by ffjjkk on 2010-09-04
Thanks alot!

My problem was solved. 

PS:
Your code like is not correct 100%.
My monitor (or somethig) is VGA1 not VGA-0
The correct last line is **xrandr --output VGA-0 --mode "1024x768_75.00"**

(i said that to help some one have same trouble with me)

Thanks again!

---

### Post by leilton on 2011-09-29
Sorry if this is wrong place to ask my question.

I have recently installed Ubuntu, (in place of open Suse), and think I will like it if only I can get the Screen Resolution fixed.   At present having to run in safe mode as Resolution is set at 800x600 (4.3) and I need 1024x768 (60).

Have, as far as possible, checked most answers.   By the way I am using a Amilo Pro 2030.


Saw the solution from sandyd, can I show my ignorance, and ask, if I use this formula, only change is my refresh rate is 60, not 75, and my chip is VGA 3, what if this does not work?

Do I get left with a screen that is a mass of coloured lines.?

---

