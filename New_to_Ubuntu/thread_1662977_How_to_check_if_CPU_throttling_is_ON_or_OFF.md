---
title: "How to check if CPU throttling is ON or OFF"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by gaurish108 on 2011-01-09
I am trying to install the ATLAS BLAS library which recommends that I turn if CPU throttling to do the install. 

How do I check if my CPU throttling is ON or OFF? 

I tried the suggestion of   ```
./cpufreq-selector -g performance
``` in the /usr/bin directory as suggested elsewhere in the forum but there was no output and the control returned back to the user. 

I have searched everywhere but there does not seem to be a way to determine the status of the CPU throttling

Thank you

---

### Post by 3rdalbum on 2011-01-09
> **gaurish108 said:**
> I am trying to install the ATLAS BLAS library which recommends that I turn if CPU throttling to do the install. 

How do I check if my CPU throttling is ON or OFF? 

I tried the suggestion of   ```
./cpufreq-selector -g performance
``` in the /usr/bin directory as suggested elsewhere in the forum but there was no output and the control returned back to the user. 

I have searched everywhere but there does not seem to be a way to determine the status of the CPU throttling

Thank you

Throttling occurs when the CPU governor is set to Ondemand or Conservative. Set it to Performance or Powersave within Linux to disable throttling. Or disable Speed Step in your computer's BIOS to run at full speed the whole time.

---

### Post by NickJones on 2011-01-09
Right click on a blank area of the top panel, click CPU Frequency Scaling Monitor, then you can easily turn it off & on.

---

### Post by Kasami on 2011-01-09
> **NickJones said:**
> Right click on a blank area of the top panel, click CPU Frequency Scaling Monitor, then you can easily turn it off & on.

Right Click on blank area, then click add to panel then click CPU Frequency Scaling Monitor.

---

### Post by ShakeyJake on 2011-01-09
There are numerous ways to display the speed the currently at. I use conky, but there is also the applet mentioned above. Once you can see what speed the cores are at, type
```
yes > /dev/null
```
into a terminal and see if it ups to the highest speed it should. In my case each core is currently at 800MHz, sending one of the cores into an infinite series of 'yes' it jumps to the full 3.2GHz.

---

### Post by abc14jon on 2012-12-10
The most recent ubuntus have a utility called indicator-cpufreq. It can be installed with sudo apt-get install indicator-cpufreq. After logging in and out again it started automatically and shows an icon near the top-right screen corner, and one can both see all the cpu-frequencies and change the policy. Kristjan Jonasson.

---

### Post by nothingspecial on 2012-12-10
Thanks for the information but this thread is nearly 2 years old.

Closed.

---

### Post by coffeecat on 2012-12-10
Old thread closed.

---

