---
title: "Help with CPU scaling."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Marbash on 2008-12-07
I've just installed emifreq and cpufreqd to try to scale down the performance of my CPU, but none of them will let me downgrade the frequency. :S

Does anyone know what I can do?

---

### Post by bobnutfield on 2008-12-07
CPU frequency scaling is usually enabled by default in Ubuntu, and it definitely is in 8.10.  To be sure, go to System>Administration>Services and be sure CPU frequency management is checked.  You can also add an applet for in you panel.  Just add the applet and select "On Demand" to use only the CPU speed you need for whatever you are doing.

---

### Post by Marbash on 2008-12-07
> **bobnutfield said:**
> CPU frequency scaling is usually enabled by default in Ubuntu, and it definitely is in 8.10.  To be sure, go to System>Administration>Services and be sure CPU frequency management is checked.  You can also add an applet for in you panel.  Just add the applet and select "On Demand" to use only the CPU speed you need for whatever you are doing.

I've added the applet to my panel, but I still won't let me change the freq. There's no error msg. or anything, it just goes back to the same as it was before. :S

---

### Post by mk1w86 on 2008-12-07
To make sure the kernel module for frequency scaling is loaded run:

```
sudo modprobe p4_clockmod
```


To load it at boot add 

p4_clockmod

to 

/etc/modules

---

### Post by mk1w86 on 2008-12-07
There is also a guide here about setting up frequency scaling.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

It shows how you can change the CPU frequency without needing to use sudo. :D

---

### Post by Marbash on 2008-12-07
> **mk1w86 said:**
> There is also a guide here about setting up frequency scaling.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

It shows how you can change the CPU frequency without needing to use sudo. :D

I checked the blog. but my terminal says that I only got one "governor" available, and that's "Performance". :S

My terminal:
raymond@laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance 
raymond@laptop:~$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance 
raymond@laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
125000 250000 375000 500001 625001 750001 875001 1000002 
raymond@laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance 
raymond@laptop:~$ $ cpufreq-selector -f 1300000
bash: $: command not found
raymond@laptop:~$ cpufreq-selector -f 125000
Invalid governor 'userspace'

---

### Post by mk1w86 on 2008-12-07
If you are not using powernowd to change the frequency then remove it and install cpufrequtils.

```
sudo apt-get remove powernowd
```

```
sudo apt-get install cpufrequtils sysfsutils
```

---

### Post by Marbash on 2008-12-07
> **mk1w86 said:**
> If you are not using powernowd to change the frequency then remove it and install cpufrequtils.

```
sudo apt-get remove powernowd
```

```
sudo apt-get install cpufrequtils sysfsutils
```

powernowd was not installed, but I installed cpufrequtils anyway, and then I got this msg in my terminal:

 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                       * disabled, governor not available...                                   [ OK ] 

Setter opp sysfsutils (2.1.0-4) ...
 * Setting sysfs variables...                                            [ OK ] 

raymond@laptop:~$ cpufreq-selector -f125000
Missing argument for -f
raymond@laptop:~$ cpufreq-selector -f 125000
Invalid governor 'userspace'

---

### Post by Marbash on 2008-12-08
I've seen some articles on the internet where my CPU type has been scaled down to 1000mHZ, but I can't even get it down from 1,67. ..and if someone says that it's not supported, why can I then scale it down in xp? :p

---

### Post by 3rdalbum on 2008-12-08
What CPU do you have? Scaling for some CPUs might not be supported out-of-the-box on Ubuntu. If we know what CPU you have, then we might be able to point you towards a kernel module that enables scaling for you.

---

### Post by Marbash on 2008-12-08
> **3rdalbum said:**
> What CPU do you have? Scaling for some CPUs might not be supported out-of-the-box on Ubuntu. If we know what CPU you have, then we might be able to point you towards a kernel module that enables scaling for you.

Intel T2300

[http://ubuntuforums.org/showthread.php?t=403841]("http://ubuntuforums.org/showthread.php?t=403841")

---

### Post by Marbash on 2008-12-09
Noone with an idea? :(

---

