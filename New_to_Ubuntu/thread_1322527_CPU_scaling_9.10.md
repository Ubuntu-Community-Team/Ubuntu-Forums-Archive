---
title: "CPU scaling 9.10"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by M@rio on 2009-11-11
Hi 
I have some problems with CPU scaling in KK. 
I can't change the governor from performance to ondemand.  
laptop_mode = true
p4_clockmod added to /etc/modules
```

cat /proc/cpuinfo | grep name
model name    : Genuine Intel(R) CPU           T1600  @ 1.66GHz
model name    : Genuine Intel(R) CPU           T1600  @ 1.66GHz

```

```

cpufreq-info
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
  cpufreq stats: 208 MHz:0,00%, 417 MHz:0,00%, 625 MHz:0,00%, 833 MHz:0,00%, 1.04 GHz:0,00%, 1.25 GHz:0,00%, 1.46 GHz:0,00%, 1.67 GHz:0,00%
analyzing CPU 1:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
  cpufreq stats: 208 MHz:0,00%, 417 MHz:0,00%, 625 MHz:0,00%, 833 MHz:0,00%, 1.04 GHz:0,00%, 1.25 GHz:0,00%, 1.46 GHz:0,00%, 1.67 GHz:0,00%

```

---

### Post by jbrown96 on 2009-11-11
I've seen this before, but my cpu still did scale. Install powertop ```
sudo apt-get install powertop
``` and run it with ```
sudo powertop
``` You can see if it is actually scaling. It's under "P-states (frequencies)"

---

### Post by M@rio on 2009-11-11
```

Cn                Avg residency       P-states (frequencies)
C0 (CPU aktywny)        ( 3,2%)         1,67 GHz   100,0%
polling           0,0ms ( 0,0%)          833 MHz     0,0%
C1 mwait          0,1ms ( 0,0%)          625 MHz     0,0%
C3 mwait          2,6ms (96,8%)          417 MHz     0,0%
                                         208 MHz     0,0%


```

---

### Post by M@rio on 2009-11-12
I really need this scaling. My laptop mostly works on battery. On 9.04 it works with out any problems after upgrade to 9.10 it stops. I did a fresh install and still no go :(

---

### Post by diekstra on 2009-11-12
M@rio, I totally agree with you, it should work... But it does seem to be rocket science...

A few days ago I upgraded from 8.04 x86 to 9.10 x64 and cpu scaling doesn't seem to do the right thing... Sometimes it detects the powerstate and adjusts the scaling settings, but mostly it is "ondemand" if the laptop is on AC and it's on "performance" if it's on Battery :icon_frown:

I was deepdiving some scripts and settings to manually adjust the settings and discovered a thread where some developers talked about the removal of the ac.d & battery.d directories, replacing them with some new utils for powerstate change detection... 

I created a script that I run when settings are wrong... It's not very polished but it does the job...

```
#! /bin/sh
# Custom CPU Scaling setting
if on_ac_power; then
	echo "We're on AC power"
	echo "performance" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	echo "performance" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
   else
	echo "Can't say we're on AC power"
	echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	echo "ondemand" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
   fi

```

---

### Post by M@rio on 2009-11-12
My laptop is on performance wherever it on AC or battery. I try those commands but my system just ignore them and still going on performance.

Those little things are really makes me nervous.

---

### Post by diekstra on 2009-11-12
Weird...
But like I said... It seems to be rocket science... :P

---

### Post by philinux on 2009-11-12
> **M@rio said:**
> I really need this scaling. My laptop mostly works on battery. On 9.04 it works with out any problems after upgrade to 9.10 it stops. I did a fresh install and still no go :(

Right click to panel. Add "CPU Frequency Scaling Monitor".

Left click to change govenor.

---

### Post by M@rio on 2009-11-12
> **philinux said:**
> Right click to panel. Add "CPU Frequency Scaling Monitor".

Left click to change govenor.

I try this, I try to change governor using terminal, no go. Nothing change still performance.

---

### Post by philinux on 2009-11-12
> **M@rio said:**
> I try this, I try to change governor using terminal, no go. Nothing change still performance.

When you left click do you get the options? It should by default ask for your password to change the governor.

Also whats in here.

```
cat /etc/init.d/ondemand
```

---

### Post by M@rio on 2009-11-12
Ok. He asked me for a password and I get all the governors and MHz. When I select one nothing change. 
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
    ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```Only powersave works but only for CPU1 for CPU0 nothing change.

---

### Post by philinux on 2009-11-12
As you can see it's already set to ondemand.

---

### Post by philinux on 2009-11-12
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
```

---

### Post by M@rio on 2009-11-12
```
mariusz@mariusz-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance 
mariusz@mariusz-laptop:~$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance 
```

Yes, but why on gnome applets  its performance, and CPU is still on max MHz ?

---

### Post by philinux on 2009-11-12
Try just running on battery.

---

### Post by M@rio on 2009-11-12
On battery - still performance, when I change to ondemand it switch back to performance and CPU is still on  1,67 GHz

---

### Post by philinux on 2009-11-12
Have you tinkered with some other settings for this?

I can suggest this resource though.
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

---

### Post by M@rio on 2009-11-12
ok. all the modules are loaded.
But when I try to change the governor i get this 
```

sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```

I try the gnome applet and still can't change the governor.

---

### Post by philinux on 2009-11-12
> **M@rio said:**
> ok. all the modules are loaded.
But when I try to change the governor i get this 
```

sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```

I try the gnome applet and still can't change the governor.

```
sudo -s

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

---

### Post by M@rio on 2009-11-12
```

root@mariusz-laptop:~# echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
root@mariusz-laptop:~# echo "ondemand" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

root@mariusz-laptop:~# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor 
performance

```
but

```

root@mariusz-laptop:~# echo "powersave" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
root@mariusz-laptop:~# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor 
powersave

```

---

### Post by philinux on 2009-11-12
> **M@rio said:**
> ```

root@mariusz-laptop:~# echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
root@mariusz-laptop:~# echo "ondemand" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

root@mariusz-laptop:~# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor 
performance

```
but

```

root@mariusz-laptop:~# echo "powersave" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
root@mariusz-laptop:~# cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor 
powersave

```

Looks like the computer says "no" :lolflag:

For now. It's my computer and I'll do it my way...eventually.

Habe you got powernowd installed as my cpu is amd but I havent got this installed and scaling works fine.

Do a search in synaptic with cpu freq. I got nothing installed like powernowd and cpufreqd.

---

### Post by M@rio on 2009-11-12
> **philinux said:**
> Looks like the computer says "no" :lolflag:
For now. It's my computer and I'll do it my way...eventually.
Habe you got powernowd installed as my cpu is amd but I havent got this installed and scaling works fine.
he he something like this. You now on 9.04 every thing was working super. Now I manage to solved all the problems only this little left.

---

### Post by M@rio on 2009-11-13
So any more ideas ? I really need this to work.

---

### Post by diekstra on 2009-11-13
I still have some troubles with the automatic scaling, when I boot the laptop it's setting is "ondemand" when I set the governor to "performance" with the CPU Scaling Applet (because it's on AC) the setting is changed.
When I disconnect the AC adapter it goes to "ondemand" and when I reconnect the adapter it goes back to "performance"

The only problem seems to be the detection during boottime...

---

### Post by M@rio on 2009-11-14
Why get this message 
FATAL: Module acpi_cpufreq not found.
When I try to modprobe this module ??

HELP !!

---

### Post by M@rio on 2009-11-15
OK. Problem solved. Just install powernowd. The scaling works like a charm.

It works but still I wont this ACPI to cover scaling on my CPU. 

**Any idea why I can't load acpi_cpufreq ?? **

Common gays it is not a rocket sciences ;)

---

### Post by spacemonkey211 on 2009-12-05
Saw in another forum that the devs decided to deliberately locked out p4-clockmod from using ondemand governor.  They compiled the kernel module with a delay that is one above the max allowed so it wont work.

---

